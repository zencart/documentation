To build one of these files: 
- Run View Schema: https://www.thatsoftwareguy.com/zencart_view_schema.html

- In Chrome Inspect, find the pageWrapper block, and copy element. 
Paste this into the new schema file. 

For these items, just reference the prior version's schema file, 
and copy and paste, adjusting where necessary. 
- Add the Markdown Header at the top.  Include a description line:
  description: This is the database schema for Zen Cart version xxx. 
  Add the weight: 
  weight: -1 * version number (-156 for 1.5.6)
- Below that, add the CSS from the prior version.
- remove the starting and ending <div> tags
- remove the <h1> tag. 

