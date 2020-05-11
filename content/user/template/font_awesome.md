---
title: Font Awesome 
description: Using Font Awesome from local and remotely.
category: template
weight: 10
type: codepage
---

Font Awesome vector icons and social logos for your website using one of the most popular icon sets and toolkits.

Installation by hosting Font Awesome yourself or by external CDN linking.  I prefer hosting it myself and linking externally.  This provides a method for me to work with Font Awesome locally while building and testing my site.  Once my site is live, it serves as a backup if contact to the CDN fails.  Using external CDN linking allows your font to stay up-to-date on versions without downloading new icon sets yourself.

Font Awesome is growing in design and possible uses.  Visit [Font Awesome ](https://fontawesome.com) site for more information and to stay up on new icons and social logos. 

I use Font Awesome in different places within my site, but I mainly use them within my CSS buttons. With HTML there are basically two types of buttons.  Buttons used for links and buttons used within form submits. 

 As this one for the Add to Cart.   `<i class="fas fa-cart-plus"></i> Add to Cart`   <img src="/images/Add-to-cart_button.png" alt="Zen Cart Version information" />
 
At one time Font Awesome was just one set of fonts making scripting buttons/links easy with only one file.  Keep in mind that we say FONT, but this is not the normal fonts in your desktop and with new vector icons added each day it had to grow.

**NOTE:** there are different icon sets to use!

| Style Availability      |Style Prefix    |            Example                  |
|-------------------------|----------------|-------------------------------------|
| Solid Free              |fas             |`<i class="fas fa-camera"></i>`      |
| Regular Pro Required    |far             |`<i class="far fa-camera"></i>`      |
| Light Pro Required      |fal             |`<i class="fal fa-camera"></i>`      |
| Duotone Pro Required    |fad             |`<i class="fad fa-camera"></i>`      |
| Brands Free             |fab             |`<i class="fab fa-font-awesome"></i>`|

----------------
Enough with the history of Font Awesome.  I would suggest going to there site to see all the new free icons you can use and even more if you buy a pro account.

## Some helpful instructions

I've played around with the different methods suggested in the Font Awesome document site and found what works for my site the best.  I'm sure there may be other ways of doing this, but this is what I fond. 
 
My site is based on;<br/>
 Zen Cart 1.5.6c<br/>
 PHP7.3.11<br/>
 Modified Responsive Sheffield Blue 1.1 Template

I have not tested this with lesser versions of Zen Cart, PHP or other templates!

I have been loading Font Awesome from a free account with them for some years now. With the kit you could modify to only load what you want and not the whole 7+k of icons. If you used Font Awesome version 4, there is some changes in the code you need to do.  In Font Awesome documents is a list of changes.  As a example <br/>version 4 was `<i class=”fa fa-arrow-circle-o-down”></i>`<br/>version 5 is `<i class=”far fa-arrow-alt-circle-down”></i>` 

In testing, using a sample html page following Font Awesome instructions for hosting the fonts worked. However, when trying the same instructions on my Zen Cart site they did not work for me. I'll cover what did work and hopefully save you some time.  

I started by removing Font Awesome 4 CSS and font folder.

```
    includes/templates/YOURTEMPLATE/css/font-awesome.css (version 4)
    includes/templates/YOURTEMPLATE/fonts (version 4 font)
```
Now Add Font Awesome 5 CSS and Folder
``` 
    includes/templates/YOURTEMPLATE/css/all.css (version 5)
    includes/templates/YOURTEMPLATE/webfonts (version 5 font)
```
Once you do this, all locations where you used Font Awesome 4 well turn into missing fonts &#xf062;.  This helps to find and edit your code.  I printed/downloaded the new font lists from [Font Awesome Cheatsheet ](https://fontawesome.com/cheatsheet) to aid in making the code changes.

I created a kit with Font Awesome. I then updated the follow just below the call to load jQuery `includes/templates/YOURTEMPLATE/common/html_header.php` If you not installed this before, then add it.  This calls to Font Awesome and loads the font icons.  The script then creates and tests for the font.  If the font is not been loaded remotely, then the script looks at your template CSS folder.

```html
    <script src="https://kit.fontawesome.com/YOUR_KIT_ID.js" crossorigin="anonymous"></script>
    <script type="text/javascript">
    (function($){
    var $span = $('<span class="fas" style="display:none"></span>').appendTo('body');
    if ($span.css('font-family') !== 'Font Awesome 5 Free' ) {
    // Fallback Link
    $('head').append(<?php echo '\'<link rel="stylesheet" type="text/css" href="' . $template->get_template_dir('.css',DIR_WS_TEMPLATE, $current_page_base,'css') . '/' . 'all.css' . '" />\''; ?>);
    }
    $span.remove();
    })(jQuery);
    </script>
```

### Coding Buttons

I'll give you a couple examples of creating buttons with form input submit fields.  Input buttons use the **value** field for the button wording.  You can not use HTML coding in the value field as this `<input type="submit" value="<i class="fas fa-cart-plus"></i> Add to Cart">` well not work! 



#### Example 1 
To get input fields to display font icons in a CSS button is to change the code in your template files with button tags like the following.

Lets do the `includes/templates/YOURTEMPLATE/templates/tpl_product_info_display.php` The Add to Cart button code looks like this `zen_image_submit(BUTTON_IMAGE_IN_CART, BUTTON_IN_CART_ALT);` To add a Font Awesome add to cart icon we can changed it to `'<button class="cssButton submit_button" type="submit"><i class="fas fa-cart-plus"></i> ' . BUTTON_IN_CART_ALT . ' </button>' ; `

In your `includes/templates/YOURTEMPLATE/css/stylesheet_css_buttons.css` copy and paste your input button css and change the input. to button.


```cs
button.submit_button {border:none !important;font-size: 1.2em;display: inline-block;margin:0;padding: 12px 30px 30px 30px;}
button.submit_button:hover {border:none !important;font-size: 1.2em;display: inline-block;margin:0;padding: 12px 30px 30px 30px !important;}
button.cssButtonHover {border:none;cursor: pointer;border:none;font-size: 1.2em;display: inline-block;margin:0;padding: 12px 30px 30px 30px !important;}
```


Of course your CSS and button may be different depending on your template styles. The button element needs the _type="submit"_ field for it to work as a form submit button. 

#### Example 2 
 In Example One, we hard coded the font icons in the button code. The problem with this is you can not use image buttons again without changing the code back plus you would have to edit each file if you wanted to change icons. 
 
In Example Two I’ll change the `includes/functions/html_output.php` file such that you can turn CSS buttons off and display the hard buttons if you wish to. Plus you can use different icons based on language.

**Files affected are:**
<br/>`includes/functions/html_output.php (Master file)`<br/>
`includes/languages/english/YOURTEMPLATE/button_names.php`<br/>
`includes/templates/YOURTEMPLATE/css/stylesheet_css_buttons.css`

Editing `html_output.php` Lines in Functions noted with **//modified for FA5**

```go 
      function zen_image_submit($image, $alt = '', $parameters = '', $sec_class = '') {
        global $template, $current_page_base, $zco_notifier;
        if (strtolower(IMAGE_USE_CSS_BUTTONS) == 'yes' return zenCssButton($image, $alt, 'submit', $sec_class, $parameters); //modified for FA5 && strlen($alt)<70) 
        $zco_notifier->notify('PAGE_OUTPUT_IMAGE_SUBMIT');
        $alt = trim(explode('</i>', $alt)[1]);  //modified for FA5
         $image_submit = '<input type="image" src="' .  zen_output_string($template->get_template_dir($image,  DIR_WS_TEMPLATE, $current_page_base, 'buttons/' . $_SESSION['language'] .  '/') . $image) . '" alt="' . zen_output_string($alt) . '"';

        if (zen_not_null($alt)) $image_submit .= ' title=" ' . zen_output_string($alt) . ' "';

        if (zen_not_null($parameters)) $image_submit .= ' ' . $parameters;

        $image_submit .= ' />';

        return $image_submit;
      }
```

and

```go
     function zenCssButton($image = '', $text, $type, $sec_class = '', $parameters = '') {
       global $css_button_text, $css_button_opts, $template, $current_page_base, $language;

       $button_name = basename($image, '.gif');

        // if no secondary class is set use the image name for the sec_class
        if (empty($sec_class)) $sec_class = $button_name;
        if(!empty($sec_class)) $sec_class = ' ' . $sec_class;
        if(!empty($parameters))$parameters = ' ' . $parameters;
        $mouse_out_class  = 'cssButton ' . (($type == 'submit') ? 'submit_button button ' : 'normal_button button ') . $sec_class;
         $mouse_over_class = 'cssButtonHover ' . (($type == 'button') ?  'normal_button button ' : '') . $sec_class . $sec_class . 'Hover';
        // javascript to set different classes on mouseover and mouseout: enables hover effect on the buttons
        // (pure css hovers on non link elements do work work in every browser)
         $css_button_js =  'onmouseover="this.className=\''. $mouse_over_class .  '\'" onmouseout="this.className=\'' . $mouse_out_class . '\'"';

        if (defined('CSS_BUTTON_POPUPS_IS_ARRAY') && CSS_BUTTON_POPUPS_IS_ARRAY == 'true') {
           $popuptext = (!empty($css_button_text[$button_name])) ?  $css_button_text[$button_name] : ($button_name .  CSSBUTTONS_CATALOG_POPUPS_SHOW_BUTTON_NAMES_TEXT);
          $tooltip = ' title="' . $popuptext . '"';
        } else {
          $tooltip = '';
        }
        $css_button = '';

        if ($type == 'submit'){
          // form input button
         if ($parameters != '') {
             // If the input parameters include a "name" attribute, need to emulate  an <input type="image" /> return value by adding a _x to the name  parameter (creds to paulm)
            if (preg_match('/name="([a-zA-Z0-9\-_]+)"/', $parameters, $matches)) {
              $parameters = str_replace('name="' . $matches[1], 'name="' . $matches[1] . '_x', $parameters);
            }
             // If the input parameters include a "value" attribute, remove it since  that attribute will be set to the input text string.
            if (preg_match('/(value="[a-zA-Z0=9\-_]+")/', $parameters, $matches)) {
              $parameters = str_replace($matches[1], '', $parameters);
            }
          }  /* */
          
          // -----
          // Give an observer the chance to provide alternate formatting for the button (it's set to an empty
          // string above).  If the value is still empty after the notification, create the standard-format
          // of the button.
          //
          $GLOBALS['zco_notifier']->notify(
                'NOTIFY_ZEN_CSS_BUTTON_SUBMIT', 
                array(
                    'button_name' => $button_name,
                    'text' => $text,
                    'sec_class' => $sec_class,
                    'parameters' => $parameters,
                ),
                $css_button
          );
          if ($css_button == '') {
           //  $css_button = '<input class="' . $mouse_out_class . '" ' .  $css_button_js . ' type="submit" value="' . $text . '"' . $tooltip .  $parameters . ' />';
            $css_button = '<button class="' . $mouse_out_class . '" ' .  $css_button_js . ' type="submit" ' . $parameters . ' >' . $text .  '</button>';  // modified for FA5
          }
        }

        if ($type=='button'){
          // link button
          // -----
          // Give an observer the chance to provide alternate formatting for the button (it's set to an empty string
          // above).  If the value is still empty after the notification, create the standard-format
          // of the button.
          //
          $GLOBALS['zco_notifier']->notify(
                'NOTIFY_ZEN_CSS_BUTTON_BUTTON', 
                array(
                    'button_name' => $button_name,
                    'text' => $text,
                    'sec_class' => $sec_class,
                    'parameters' => $parameters,
                ),
                $css_button
          );
          if ($css_button == '') {
             $css_button = '<span class="' . $mouse_out_class . '" ' .  $css_button_js . $tooltip . $parameters . '>&nbsp;' . $text .  '&nbsp;</span>';
          }
        } 
        return $css_button;
      }
```

The file `button_names.php` holds your buttons and alt defines.  If it’s not in your template folder, copy it there. This is where you can add the font icons to match your languages. Each language should have its own button name file. Be sure to use the right style, they are fas, far, and fab.

{{% alert title="Warning" color="warning" %}}
Font Awesome style tags must be placed on the left only with wording on the right.  If you fail to follow this one rule, the alt for image buttons would fail.
{{% /alert %}}

Editing `includes/languages/english/YOURTEMPLATE/button_names.php`  Showing some sample lines.
```go
    define('BUTTON_IN_CART_ALT', '<i class="fas fa-cart-plus"></i> Add to Cart');  
    define('BUTTON_LOGIN_ALT', '<i class="fas fa-sign-in-alt"></i> Sign In');
    define('BUTTON_LOOKUP_ALT', '<i class="far fa-eye"></i> Lookup');
```

Editing `includes/templates/YOURTEMPLATE/css/stylesheet_css_buttons.css`  I use hover, click, RGB color and shape CSS rules on my buttons to make them stand out and not look so boxy.. In my opinion, CSS button far surpass what we could do with image buttons. Instead of locking you to a code block, Google for a CSS button generator to create your own button CSS code.

Example 2 was the one I used on my site and may not be the only option you have! 
