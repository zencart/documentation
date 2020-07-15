To build one of these files after a new release: 
- Run View Schema, which is downloadable from the Zen Cart Plugins Library at  

https://www.zen-cart.com/downloads.php?do=file&id=2270 

- In Chrome Inspect, find the pageWrapper block, and copy element. 
Paste this into the new schema file. 

For these items, just reference the prior version's schema file, 
and copy and paste, adjusting where necessary. 
- Add the Markdown Header at the top.  Include a description line:
  description: This is the database schema for Zen Cart version xxx. 
- Add the weight: line to fix the sort order 
  weight: -1 * version number (-156 for 1.5.6)
- Below that, add the CSS from the prior version.
- remove the starting and ending <div> tags
- remove the <h1> tag. 

