---
title: Address formats - what are they? 
description: How addresses are displayed in different countries 
category: localization
weight: 10
---
You may have noticed the address format value ranges between 1 and 20.
The UK is 6, USA is 7 and most other countries are 5. There is a [full list below.](#zen-cart-158) The Default format is 1 which is no longer used by any country.

What exactly is the 'format' ?

Address formats are based on international ISO standard formats.

In Zen Cart, formats are stored in the `address_format` table. 

This table is structured as follows: 

## Columns

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

### address_format

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
### address_summary

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

### Zen Cart 1.5.6

The entries are:

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
```
1 - Default, most countries except those below. 
2 - USA 
3 - Spain 
4 - Singapore 
5 - Germany 
6 - UK/GB 
7 - Australia
```
### Zen Cart 1.5.8

Additional address formats have been added to Zen Cart 1.5.8. If you upgrade from a previous version of Zen Cart then any address codes you have created will be moved outside of the new default range and all orders and country entries that used them will be adjusted.

Below is a table with the Format ID, Address formats, an example of the address and the countries to which they are applied.

| Format | Address Format| Example  &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;| Countries |
|--------|----------------------|---------------|------------|
|1|$firstname $lastname$cr$streets$cr$city, $postcode$cr$statecomma$country |firstname surname<br>street address<br>addressline2<br>city, postcode<br>state, country|  Default - Not Used|
|2|$firstname $lastname$cr$streets$cr$city, $state    $postcode$cr$country|firstname surname<br>street address<br>addressline2<br>city, state postcode<br>country|Latvia<br>Myanmar<br>Saint Kitts and Nevis<br>Somalia<br>Trinidad and Tobago|
|3|$firstname $lastname$cr$streets$cr$city$cr $postcode - $statecomma$country|firstname surname<br>street address<br>addressline2<br>city<br>postcode - state, country|Not Used|
|4|$firstname $lastname$cr$streets$cr$city ($postcode)$cr$country|firstname surname<br>street address<br>addressline2<br>city (postcode)<br>country|Not Used|
|5|$firstname $lastname$cr$streets$cr $postcode $city$cr$country|firstname surname<br>street address<br>addressline2<br>postcode city<br>country|Åland Islands<br>Albania<br>Algeria<br>Andorra<br>Argentina<br>Armenia<br>Austria<br>Azerbaijan<br>Belgium<br>Bosnia and Herzegowina<br>Bulgaria<br>Cape Verde<br>Chile<br>Croatia<br>Cyprus<br>Czech Republic<br>Denmark<br>Dominican Republic<br>Equatorial Guinea<br>Estonia<br>Ethiopia<br>Faroe Islands<br>Finland<br>France<br>French Guiana<br>French Polynesia<br>French Southern Territories<br>Gabon<br>Georgia<br>Germany<br>Greece<br>Greenland<br>Guadeloupe<br>Guinea<br>Guinea-bissau<br>Haiti<br>Iceland<br>Israel<br>Jamaica<br>Kuwait<br>Lao People's Democratic Republic<br>Liechtenstein<br>Lithuania<br>Luxembourg<br>Macedonia, The Former Yugoslav Republic of <br>Madagascar<br>Martinique<br>Mayotte<br>Moldova<br>Monaco<br>Morocco<br>Netherlands<br>New Caledonia<br>Niger<br>Norway<br>Paraguay<br>Poland<br>Portugal<br>Réunion<br>Romania<br>San Marino<br>Senegal<br>Slovakia (Slovak Republic)<br>Slovenia<br>St. Pierre and Miquelon<br>Svalbard and Jan Mayen Islands<br>Sweden<br>Switzerland<br>Syrian Arab Republic<br>Tajikistan<br>Turkmenistan<br>Uruguay<br>Wallis and Futuna Islands<br>Palestine,  State of <br>Montenegro<br>South Sudan|
|6|$firstname $lastname$cr$streets$cr $city$cr$state$cr$postcode$cr$country|firstname surname<br>street address<br>addressline2<br>city<br>state<br>postcode<br>country|Afghanistan<br>British Indian Ocean Territory<br>Egypt<br>Falkland Islands (Malvinas)<br>Gibraltar<br>India<br>Iran (Islamic Republic of)<br>Ireland<br>Kazakhstan<br>Kenya<br>Kiribati<br>Malta<br>Montserrat<br>Pitcairn<br>Russian Federation<br>Seychelles<br>Solomon Islands<br>South Africa<br>South Georgia and the South Sandwich Islands<br>Sri Lanka<br>St. Helena<br>Swaziland<br>Togo<br>Turks and Caicos Islands<br>Tuvalu<br>Ukraine<br>United Arab Emirates<br>United Kingdom<br>Uzbekistan<br>Serbia<br>Zimbabwe<br>Guernsey<br>Isle of Man<br>Jersey|
|7|$firstname $lastname$cr$streets$cr $city $state $postcode$cr$country|firstname surname<br>street address<br>addressline2<br>city state postcode<br>country|American Samoa<br>Australia<br>Cambodia<br>Canada<br>Cayman Islands<br>China<br>Christmas Island<br>Cocos (Keeling) Islands<br>Colombia<br>Guam<br>Guyana<br>Heard and Mc Donald Islands<br>Japan<br>Korea,  Republic of <br>Marshall Islands<br>Micronesia, Federated States of <br>Norfolk Island<br>Northern Mariana Islands<br>Pakistan<br>Palau<br>Puerto Rico<br>United States<br>United States Minor Outlying Islands<br>Virgin Islands (U.S.)<br>Curaçao<br>Sint Maarten (Dutch part)|
|8|$firstname $lastname$cr$streets $cr$city$cr$country|firstname surname<br>street address<br>addressline2<br>city<br>country|Angola<br>Antigua and Barbuda<br>Aruba<br>Barbados<br>Benin<br>Bolivia<br>Botswana<br>Bouvet Island<br>Burundi<br>Cameroon<br>Central African Republic<br>Chad<br>Comoros<br>Congo<br>Côte d'Ivoire<br>Djibouti<br>Dominica<br>Eritrea<br>Fiji<br>Gambia<br>Grenada<br>Hong Kong<br>Libya<br>Macao<br>Malawi<br>Mali<br>Mauritania<br>Mauritius<br>Namibia<br>Qatar<br>Rwanda<br>Saint Lucia<br>Samoa<br>Sao Tome and Principe<br>Sierra Leone<br>Suriname<br>Tonga<br>Uganda<br>Vanuatu<br>Western Sahara<br>Yemen|
|9|$firstname $lastname$cr$streets $cr$postcode $city $state$cr$country|firstname surname<br>street address<br>addressline2<br>postcode city state<br>country|Cuba<br>Honduras<br>Italy<br>Liberia<br>Mexico<br>Tunisia<br>Turkey<br>Vatican City State (Holy See)|
|10|$firstname $lastname$cr$streets$cr $city $postcode$cr$country|firstname surname<br>street address<br>addressline2<br>city postcode<br>country|Anguilla<br>Antarctica<br>Bahamas<br>Bahrain<br>Bangladesh<br>Belize<br>Bermuda<br>Bhutan<br>Burkina Faso<br>Cook Islands<br>Timor-Leste<br>Indonesia<br>Jordan<br>Korea, Democratic People's Republic of<br>Lebanon<br>Lesotho<br>Maldives<br>Mongolia<br>Nauru<br>Nepal<br>Bonaire, Sint Eustatius and Saba <br>New Zealand<br>Niue<br>Saint Vincent and the Grenadines<br>Saudi Arabia<br>Singapore<br>Taiwan<br>Tokelau<br>Virgin Islands (British)<br>Zambia|
|11|$firstname $lastname$cr$streets$cr $city $state$cr$postcode$cr$country|firstname surname<br>street address<br>addressline2<br>city state<br>postcode<br>country|Brazil<br>Costa Rica<br>Ghana<br>Iraq<br>Thailand|
|12|$firstname $lastname$cr$streets$cr $postcode$cr$city $state$cr$country|firstname surname<br>street address<br>addressline2<br>postcode<br>city state<br>country|Ecuador<br>Nicaragua<br>Peru<br>Sudan|
|13|$firstname $lastname$cr$streets$cr $city $postcode$cr$state$cr$country|firstname surname<br>street address<br>addressline2<br>city postcode<br>state<br>country|Nigeria|
|14|$firstname $lastname$cr$streets $cr$postcode $city$cr$state$cr$country|firstname surname<br>street address<br>addressline2<br>postcode city<br>state<br>country|Belarus<br>El Salvador<br>Guatemala<br>Kyrgyzstan<br>Malaysia<br>Mozambique<br>Panama<br>Tanzania, United Republic of |
|15|$firstname $lastname$cr$streets$cr $postcode$cr$city$cr$state$cr$country|firstname surname<br>street address<br>addressline2<br>postcode<br>city<br>state<br>country|Oman|
|16|$firstname $lastname$cr$streets$cr $city $postcode $state$cr$country|firstname surname<br>street address<br>addressline2<br>city postcode state<br>country|Papua New Guinea<br>Venezuela|
|17|$firstname $lastname$cr$streets$cr $city$cr$postcode $state$cr$country|firstname surname<br>street address<br>addressline2<br>city<br>postcode state<br>country|Philippines|
|18|$firstname $lastname$cr$streets$cr $city$cr$state $postcode$cr$country|firstname surname<br>street address<br>addressline2<br>city<br>state postcode<br>country|Brunei Darussalam<br>Viet Nam|
|19|$firstname $lastname$cr$city$cr$streets$cr $postcode$cr$country|firstname surname<br>city<br>street address<br>addressline2<br>postcode<br>country|Hungary|
|20|$firstname $lastname$cr$streets$cr $postcode $city ($state)$cr$country|firstname surname<br>street address<br>addressline2<br>postcode city (state)<br>country|Spain|

The sources used to determine the address formats where [informatica](https://www.informatica.com/products/data-quality/data-as-a-service/address-verification/address-formats.html) and [loqate](https://www.loqate.com/en-gb/address-verification/international-address-formats). Loqate appeared to be more recent and had more formats with postcodes.

