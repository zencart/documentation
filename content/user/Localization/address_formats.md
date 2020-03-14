---
title: Address formats - what are they? 
category: localization
weight: 1
---
You may have noticed the address format value ranges between 1 and 6.
The Uk is 6 and most other countries are 1. 
What exactly is the 'format' ?

Address formats are based on international ISO standard formats.

In Zen Cart, formats are stored in the `address_format` table. 

This table is structured as follows: 

## <span class="mw-headline" id="Columns">Columns</span>

### address_format_id 

<dl>

<dd>A unique, auto incremented value, to identify each address format record.</dd>

</dl>

> <table>
> 
> <tbody>
> 
> <tr>
> 
> <td>Type:</td>
> 
> <td>int(11)</td>
> 
> </tr>
> 
> <tr>
> 
> <td>Null:</td>
> 
> <td>No</td>
> 
> </tr>
> 
> <tr>
> 
> <td>Default:</td>
> 
> <td></td>
> 
> </tr>
> 
> <tr>
> 
> <td>Extra:</td>
> 
> <td>auto_increment</td>
> 
> </tr>
> 
> </tbody>
> 
> </table>

### <span class="mw-headline" id="address_format">address_format</span>

<dl>

<dd>The format used for displaying the shipping/billing address.</dd>

</dl>

> <table>
> 
> <tbody>
> 
> <tr>
> 
> <td>Type:</td>
> 
> <td>varchar(128)</td>
> 
> </tr>
> 
> <tr>
> 
> <td>Null:</td>
> 
> <td>No</td>
> 
> </tr>
> 
> <tr>
> 
> <td>Default:</td>
> 
> <td></td>
> 
> </tr>
> 
> </tbody>
> 
> </table>

> Possible variables are:
> 
> <dl>
> 
> <dd>
> 
> *   $firstname - first name
> *   $lastname - last name
> *   $cr - forces line break
> *   $streets - street address
> *   $city - city
> *   $state - state
> *   $statecomma - state followed by a comma and a space
> *   $postcode - postcode
> *   $country - country
> *   Punctuation, spaces and other characters can be added as well before or after the variables
> 
> </dd>
> 
> </dl>
> 
### <span class="mw-headline" id="address_summary">address_summary</span>

<dl>

<dd>Summary of the address format used for display purposes.</dd>

</dl>

> <table>
> 
> <tbody>
> 
> <tr>
> 
> <td>Type:</td>
> 
> <td>varchar(48)</td>
> 
> </tr>
> 
> <tr>
> 
> <td>Null:</td>
> 
> <td>No</td>
> 
> </tr>
> 
> <tr>
> 
> <td>Default:</td>
> 
> <td></td>
> 
> </tr>
> 
> </tbody>
> 
> </table>

## Default Entries

The default entries can be seen in the file `zc_install/sql/install/mysql_zencart.sql`.

As of Zen Cart 1.5.6, they are: 

<table>
<tr><td>ID</td><td>Value</td></tr>
<tr><td>1</td><td> $firstname $lastname<br>$streets<br>$city, $postcode<br>$statecomma$country,$city / $country</td></tr>
<tr><td>2</td><td> $firstname $lastname<br>$streets<br>$city, $state    $postcode<br>$country,$city, $state / $country</td></tr>
<tr><td>3</td><td> $firstname $lastname<br>$streets<br>$city<br>$postcode - $statecomma$country,$state / $country</td></tr>
<tr><td>4</td><td> $firstname $lastname<br>$streets<br>$city ($postcode)<br>$country, $postcode / $country</td></tr>
<tr><td>5</td><td> $firstname $lastname<br>$streets<br>$postcode $city<br>$country,$city / $country</td></tr>
<tr><td>6</td><td> $firstname $lastname<br>$streets<br>$city<br>$state<br>$postcode<br>$country,$postcode / $country</td></tr>
<tr><td>7</td><td> $firstname $lastname<br>$streets<br>$city $state $postcode<br>$country,$city $state / $country</td></tr>
</table>

The values are used as follows: 
<pre>
1 - Default, most countries except those below. 
2 - USA 
3 - Spain 
4 - Singapore 
5 - Germany 
6 - UK/GB 
7 - Australia
</pre>

