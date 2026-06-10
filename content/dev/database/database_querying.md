---
title: Querying the Database
description: Using QueryFactory
aliases:
  - /dev/code/database_querying/
category: code
type: codepage
weight: 10
---

Making a database query involves preparing a SQL statement, sanitizing any parameters to be passed to it, and submitting it for a result.
The result can then be inspected for the kind of response received.

## Preparing a Query

A typical query is built like this:

```php
$sql = "SELECT p.products_id, p.products_model, pd.products_name
        FROM " . TABLE_PRODUCTS . " p
        LEFT JOIN " . TABLE_PRODUCTS_DESCRIPTION . " pd USING (products_id)
        WHERE pd.languages_id = :lang_id
        LIMIT 10";
```

Note the inline inclusion of the TABLE_PRODUCTS and TABLE_PRODUCTS_DESCRIPTION constants. These are used so that the appropriate DB_PREFIX is automatically included if set.

Also note the use of tablename aliases `p` and `pd`. These are placed after the tablename to avoid having to use the full tablename constants repeatedly every time a table needs to be mentioned.

The `:lang_id` placeholder is used for sanitization, as described next:

## Sanitizing Inputs

A query should never just blindly use any received data. It should always sanitize the input variable before using it in a query.

We use `bindVars` for this.

Following the code example above, the next line of code would be:

```php
global $db;
$sql = $db->bindVars($sql, ':lang_id', $_SESSION['languages_id'], 'integer');
```

Here, the `$sql` variable is reset to the parsed response of the bindVars call.

The first parameter is `$sql` which is the query from the code example above.

The second parameter is the placeholder. Notice the use of the `:` prefix. The string here must be unique and only appear in the query once, as `bindVars` does a search-and-replace (`str_replace`) on the query text.
In Zen Cart code you will see cases where the `:` is used both as a prefix only, or also added as a suffix; both forms are acceptable.

The third parameter is the value to be substituted in place of the second parameter.

The fourth parameter is the kind of sanitization rule to apply while substituting. 

Valid sanitization rules are:

rule | meaning
--- | ---
`integer` | casts to integer (ignores all fractions, and treats it as 0 if the value is not numeric)
`float`   | casts to a float, or an empty/zero/falsey value is cast to `0`
`string`  | returns a quote-wrapped string after sanitizing by MySQL's escaping rules (note: string `NULL` is treated as a literal `null` response).
`stringIgnoreNull` | quote-wrapped string which ignores if the string is `NULL`, sanitized using MySQL escaping rules
`noquotestring`    | no quote-wrapping version of `stringIgnoreNull`
`currency` | alias of `stringIgnoreNull`
`date`     | same as `string` but treats both upper-and-lowercase `NULL` and `null` as `null`
`passthru` | no treatment; this should be avoided; only suitable for data already sanitized by a different means


### Alternative to BindVars

For very simple queries where you want to handle the casting manually, or just treat the value as a string, you may use `zen_db_input()` or `$db->prepare_input()`:

```php
$sql = "SELECT p.products_id, p.products_model, pd.products_name
        FROM " . TABLE_PRODUCTS . " p
        LEFT JOIN " . TABLE_PRODUCTS_DESCRIPTION . " pd USING (products_id)
        WHERE pd.languages_id = " . (int)zen_db_input($_POST['user_language_id']) . "
        LIMIT 10";
```

**NOTE:** `zen_db_input()` is an alias for `$db->prepare_input()`, which runs `mysqli_real_escape_string()` on its argument.

## INSERT and UPDATE Queries

Data-changing queries follow the same safety rules: build the SQL carefully, sanitize all external values, then execute the query.

### INSERT Example Using `bindVars`

```php
$sql = "INSERT INTO " . TABLE_PRODUCTS_DESCRIPTION . "
          (products_id, language_id, products_name)
        VALUES
          (:products_id, :language_id, :products_name)";

$sql = $db->bindVars($sql, ':products_id', $products_id, 'integer');
$sql = $db->bindVars($sql, ':language_id', $_SESSION['languages_id'], 'integer');
$sql = $db->bindVars($sql, ':products_name', $products_name, 'string');

$db->Execute($sql);
$inserted_record_id = $db->insert_ID();
```

Use `insert_ID()` after an `INSERT` into a table with an auto-increment column when you need the new record's ID.

### UPDATE Example Using `bindVars`

```php
$sql = "UPDATE " . TABLE_CUSTOMERS . "
        SET customers_firstname = :firstname,
            customers_lastname = :lastname
        WHERE customers_id = :customers_id";

$sql = $db->bindVars($sql, ':firstname', $_POST['firstname'], 'string');
$sql = $db->bindVars($sql, ':lastname', $_POST['lastname'], 'string');
$sql = $db->bindVars($sql, ':customers_id', $_SESSION['customer_id'], 'integer');

$db->Execute($sql);
$affected_rows = $db->affectedRows();
```

Use `affectedRows()` after an `UPDATE`, `INSERT`, `REPLACE`, or `DELETE` when you need to know how many rows were changed.

### Using `zen_db_perform()`

For common `INSERT` and `UPDATE` operations, Zen Cart also provides `zen_db_perform()`, which can be simpler than manually building SQL.

You pass the table name, an associative array of column/value pairs, and optionally the action and `WHERE` clause.

#### INSERT with `zen_db_perform()`

```php
$sql_data_array = [
    'products_id' => (int)$products_id,
    'language_id' => (int)$_SESSION['languages_id'],
    'products_name' => zen_db_prepare_input($products_name),
];

zen_db_perform(TABLE_PRODUCTS_DESCRIPTION, $sql_data_array);
$inserted_record_id = $db->insert_ID();
```

#### UPDATE with `zen_db_perform()`

```php
$sql_data_array = [
    'customers_firstname' => zen_db_prepare_input($_POST['firstname']),
    'customers_lastname' => zen_db_prepare_input($_POST['lastname']),
];

zen_db_perform(
    TABLE_CUSTOMERS,
    $sql_data_array,
    'update',
    "customers_id = " . (int)$_SESSION['customer_id']
);

$affected_rows = $db->affectedRows();
```

When using `zen_db_perform()`:

- the array keys are column names
- the array values are the values to store
- for updates, the fourth parameter is the `WHERE` clause
- integer values should still be cast explicitly
- string values should still be prepared appropriately before being passed in

`zen_db_perform()` is particularly useful in admin pages, installers, and other code that maps form fields directly to table columns.

## Running the Query

The prepared query can now be executed using:

```php
$results = $db->Execute($sql);
```

## Parsing the Query Response

### Checking for Empty Result Set

If there are no results found, then `$results->EOF` will be `true`.

The RecordCount will also be `0`. See below.

### Checking for Number of Records Found

The number of records retrieved from a `SELECT` query can be determined with:

```php
$records = $results->RecordCount();
```

### Checking Number of Affected Rows

If the query was an `INSERT`, `UPDATE`, `REPLACE` or `DELETE` then the number of affected rows can be determined using:

```php
$affected_rows = $db->affectedRows();
```

### Reading the New Record ID

If the query was an `INSERT` statement on an `auto-incrementing` table, then the inserted record ID number can be determined using:

```php
$inserted_record_id = $db->insert_ID();
```

### Reading the Retrieved Records

If the query was a `SELECT` statement, then the results will be in an `Iterable` `queryFactoryResult` object. 

These results can be read in two ways:

#### Single Row Responses
If the result is a single record, simply read it from the `->fields['column_name']` array:

```php
$prod_name = $results->fields['products_name'];
```

#### Multiple Row Responses
If there are multiple rows returned, the most efficient way to iterate through the results is using a `foreach()` loop:

```php
foreach($results as $result) {
  echo 'Product ID: ' . $result['products_id'] . ': ' . $result['products_name'] . "<br>\n";
}
```
This has worked since Zen Cart 1.5.5. 

An older more verbose syntax exists in legacy code. The following accomplishes the same as the `foreach` above, but is not preferred:

```php
while (!$results->EOF) {
  echo 'Product ID: ' . $results->fields['products_id'] . ': ' . $results->fields['products_name'] . "<br>\n";
  $results->MoveNext();
}
```


# Advanced

## Randomized Query Responses

If you wish to have the query_factory pick a random record from the query result, two steps are required:

a) instead of `$db->Execute()`, call `$db->ExecuteRandomMulti()` when running the query

b) instead of `$db->MoveNext()`, call `$db->MoveNextRandom()` when iterating through the results

In core code this is typically done in sideboxes and centerboxes when showing things like Specials and Featured Products, so that the customer doesn't always see only the most recently edited items.

Also note that randomizing the data like this means the page cannot be cached, so if you're using external caching systems to index your page (like Cloudflare), you may not see the randomized results.

## SQL Injection Protection

Your best defense against potential SQL injection attacks is to sanitize inputs as noted above.  Simply using a POSTed variable in a query is not safe! 

```php
$query = $db->Execute("UPDATE " . TABLE_CUSTOMERS . " SET customers_firstname = '" . $_POST['name'] . "'");    // DO NOT DO THIS! 
```
Instead, use `bindVars` as described above. 

```php
$query = "UPDATE " . TABLE_CUSTOMERS . " SET customers_firstname = :name:";    // DO THIS INSTEAD! 
$query = $db->bindVars($query, ':name:', $_POST['name'], 'string');
$db->Execute($query);
```

# Sniffer Object 

The file `includes/classes/sniffer.php` defines the `sniffer` class.  
The purpose of this class is to allow you to deduce the presence (or absence) of various things in the database.  
Its methods are: 

- `field_exists` - is a particular column in a table? 
- `field_type` - what is the type of a particular column in table? 
- `rowExists` - does a row exist where the specified column has the specified value? 
- `rowExistsComposite` - does a row exist where the specified columns have the specified values? 

See [database change checks](/dev/plugins/tips/#database-change-checks) for an example of using the sniffer object. 
