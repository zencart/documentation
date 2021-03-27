---
title: JavaScript Customization 
description: Adding or changing JavaScript 
category: template
weight: 10
type: codepage
---

### Site-Wide jscript's
<p><b>jscript*.js files -- to be "linked" by your site</b> 
</p><p>Any file in the <code>includes/templates/<b>{template_directory}</b>/jscript/</code> directory with the following filename format will be loaded globally on every page of your shop: 
</p>
<pre> jscript_{unique_name}.js
</pre>
<p>(where <b>{unique_name}</b> can be anything you want) 
</p><p>Effectively, the file will be loaded as if you had inserted the following into an HTML page:
</p>
<pre> &lt;script type="text/javascript" src="includes/templates/{template_directory}/jscript/jscript_{unique_name}.js"&gt;&lt;/script&gt;
</pre>
<p><br>
<b>jscript*.php files -- to be "included" in your HTML content sent to the browser, inline.</b>
</p><p>If you need to control the content of certain PHP variables inside jscript code on the page, OR if you need to include several <code>&lt;script&gt;...&lt;/script&gt;</code> tags, use a <b>jscript_*.php</b> file instead. 
However, <b>in this case, you DO need to include</b> the <code>&lt;script .... &gt;</code> and <code>&lt;/script&gt;</code> tags in the file. 
</p><p><br>
</p>

### Page-Specific jscript files 
<p>For page-specific operation, put the file under the <code>/includes/modules/pages/{pagename}/</code> folder. 
</p><p><b>jscript*.js files -- to be "linked" by your site</b> 
</p><p>Note: <b>jscript_*.js</b> files must not contain any <code>&lt;script...&gt; .... &lt;/script&gt;</code> tags. They should contain ONLY the contents that are to go "between" those tags. 
</p><p><br>
<b>jscript*.php files -- to be "included" in your HTML content sent to the browser, inline.</b>
</p><p>If you need to control the content of certain PHP variables inside jscript code on the page, use a <b>jscript_*.php</b> file.
However, in this case, you DO need to include the <code>&lt;script .... &gt;</code> and <code>&lt;/script&gt;</code> tags in the file.
</p><p><br>
</p>

### On_Load Override How-To
<p>This is a bit of another angle on the use of JavaScript in Zen Cart pages.
</p><p>Zen Cart's modular system can be used to insert &lt;body&gt; tag "onload" event handling on a site-wide or per-page basis very easily. Within your /includes/templates/YOURTEMPLATE/ folder, you can create a <code>/jscript/on_load/</code> folder for this purpose. 
</p><p>Any <b>on_load_*.js</b> file in this directory can be used to modify the body tag with a JavaScript <i>on_load()</i> function.
</p><p><br>
</p>

### Site-Wide Use
<p>For site-wide operation, just name the file on_load_.js (you need the trailing underscore; on_load.js does not work) and store it in the <code>/includes/templates/YOURTEMPLATE/jscript/on_load/</code> folder. Multiple files may be present, and can be added by adding an underscore and more letters to the filename. 
</p><p><br>
</p>

### Page-Specific Use
<p>For page-specific operation, put the file under the <code>/includes/modules/pages/{pagename}/</code> folder. 
</p><p><br>
</p>

### File Contents
<p>Note: <b>on_load_*.js</b> files must contain ONLY the raw code to be inserted in the &lt;body&gt; tag in the <code>on_load=""</code> attribute.
</p><p>The effect is like this:
</p>
<pre> &lt;body onload="WHATEVER_YOUR_FILE_CONTAINS_GOES_HERE"&gt;
</pre>
<p>Essentially, the contents of the file will be a function call to the DOM or to functions loaded in a jscript file. 
</p><p><br>
</p>

### OVERRIDE Operation:
<p>1. Checks the existence of "on_load" scripts for the <b>individual page</b> first. Looks in 
</p><p>"<code>/includes/modules/pages/{PAGENAME}/</code>" for files named "<b>on_load_*.js</b>"
</p><p>2. Then checks for site-wide overrides in 
</p><p>"<code>includes/templates/TEMPLATE/jscript/on_load/on_load_*.js</code>"
</p><p><br>
</p>

### EXAMPLES
#### EXAMPLE #1 (per-page on_load coding)
<p>Two live examples of this exist for the default "login" and "contact us" pages in Zen Cart®.
Let's look at the login page: 
</p><p>You'll see that in <code>/includes/modules/pages/login/on_load_main.js</code> the code that is inserted into the &lt;body&gt; tag for that page is this:
</p>
<pre>  document.getElementById('login-email-address').focus();
</pre>
<p>This is a DOM call to set focus on the "login-email-address" field on the page as the first spot where the cursor will be flashing when the page is opened.
</p><p>When the login page is loaded, the &lt;body&gt; tag will read like this:
</p>
<pre>  &lt;body id="login" onload="document.getElementById('login-email-address').focus();"&gt; 
</pre>
<p><br>
</p>

#### EXAMPLE #2 (on_load calls on all pages in your shop)
<p>Sometimes a designer wishes to preload rollover images on the page for menu purposes. In this case, the implementation is two-fold:
</p><p>1. Create a file with JavaScript function definitions for the preload activities, and place it in:
</p><p><code>includes/templates/{template_directory}/jscript/jscript_preloadimages.js</code>
</p><p>2. Create a file for the onload code as:
</p><p><code>includes/templates/{template_directory}/jscript/on_load/on_load_image_preload.js</code>
</p><p>and in the file put just one function call to match the preload function definition in your js file, such as:
</p>
<pre> preloadImages();
</pre>
<p>3. Of course, be sure to upload the real image files, etc to support the preload activities.
</p>
