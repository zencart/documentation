# Introduction
A number of changes have been made in 1.5.5 and v2 to make interacting with the database simpler.

## Looping
Starting with v1.5.5 looping through database queries no longer requires the complex while loop, and can instead use a simple foreach iterator. This is more intuitive and more maintainable.

<pre>
while (!$result->EOF) { 
  // some action
  $result->MoveNext();
}
</pre>

becomes:

<pre>
foreach($result as $row) {
  // some action
}
</pre> 

## Returned Data References
The syntax of referring to data returned from a query is now shorter.

<pre>
  $result = $db->Execute(some query) 
  $data = $result->fields['filename'];
</pre>

becomes:

<pre>
  $result = $db->Execute(some query) 
  $data = $row['fieldname'];
</pre> 
