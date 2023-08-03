---
title: Accessibility Overview
description: WCAG and Section 508
category: accessibility
weight: 5
---

Before you read this article, please be sure you are familiar with [Basic Terms](/user/first_steps/basic_terms/) used in describing Zen Cart files. 

## What is Accessibility? 

Web Content Accessibility Guidelines (WCAG) were developed with the goal of providing a single shared standard for web content accessibility that meets the needs of individuals, organizations, and governments internationally.  You'll find a great article on the [W3C Web Design and Applications page](https://www.w3.org/standards/webdesign/accessibility) that explains this initiative.

What follows are just a few of the things that Zen Cart users should consider when creating or editing their template and site.  Think of it as a quick triumvirate of accessibility steps to think about.  These three are the most common accessibility standards that should be considered when adding anything to your site.

## Visual Problems

Whether you know it or not, there are many accommodations for access in our daily lives.  Signal lights (red, yellow, green) are all top to bottom or left to right.  You'll find this is a worldwide standard.  Is this because everyone buys from the same signal light manufacturer?  It's actually because one out of every twelve men and one out of every two hundred women is "color blind".  The more accurate description is color deficient.  The signals are the same because the main color deficiencies are in the red (Protan) and green (Deutan) defects.  With them always in the same order, the color-deficient person decides to go or stop based on the location of the light rather than the color.

If we look at just the 2017 US statistics, that would mean that over thirteen million men and eight hundred and thirty thousand women will have a problem looking at a website that contains reds or greens.  That translates to five percent of the US people having problems with colors on a website.

This does not take into account the number of folks who are legally or totally blind.  In this case, we would need to add another twelve million to our list.  This brings us to almost a full ten percent of the US Population alone that is going to have difficulty with website colors.  Half of those will have a problem even seeing the site.  Just search for "website reading programs for the visually impaired" and just the 70+ million responses might convince you that they are a hot topic.

What can we do about the colors of our Zen Cart templates?  As of Zen Cart 1.5.7, the responsive_classic template meets the accessibility standards.  The way the colors are handled is with contrast.  Even a person who cannot see red will be able to read the red text if it "stands out" against its background.  For instance, you would think that red (#FF0000) on a white (#FFFFFF) background would not be difficult for someone to read.  

<div border="1" style="background:#FFFFFF; border: 1px solid black; padding: 5px;">
<font color="#FF0000">This is text in color #FF0000 on a white background.</font>
</div>
<br>

In fact, the contrast ratio this produces is 3.99 to 1, which fails three out of five of the web contrast checks.  The red would need to darken to #B30000 in order to meet the minimum 7.2 to 1 ratio and pass all five tests.  

<div border="1" style="background:#FFFFFF; border: 1px solid black; padding: 5px;">
<font color="#B30000">This is text in color #B30000 on a white background.</font>
</div>
<br>

See the [WebAIM Contrast Checker](https://webaim.org/resources/contrastchecker/) for more details.

Can we improve this message further?  Yes we can!  

People with visual impairments may not realize that the red message you are displaying is a serious error (rather than just a status message).  You can enhance the accessibility of messages using icons or other images that re-enforce what you are saying. 

<div border="1" style="background:#FFFFFF; border: 1px solid black; padding: 5px;">
<i class="fas fa-exclamation-triangle" title="error" style="color: #B30000"></i><font color="#B30000"></i>This is an error message!</font>
</div>
<br>

You could also use a stop sign, or high/medium/low icons to ensure your message is understood by the visually impaired.  And what's best is that this is a win-win, because it helps your fully sighted viewers recognize the importance of the message too. 

## What Am I Looking At?

Accessibility is not just about the visually challenged.  What about the folks in developing countries or a remote ranch in Texas or Montana?  What's the average internet speed in the Alaskan Bush?  You might wonder what they would have in common but, probably just because you're in your home or office with megabytes of bandwidth.  There are folks who are still using virtual dial-up speed to surf the net!

"What am I supposed to do about their problem?" you might ask.  The answer is Alternative Text for Images.  How does that help their problem?

Many folks are forced to turn off the display of images in their browser just to get the page to load on their low-speed connection.  The Alternative Text (alt tag) is a vital tool that can be used to "tell" the browser what the image is that they are not seeing.

Zen Cart uses image `alt` tags to help describe images.  For example, in the demo data set, product 27's image appears on the product info page like this: 

```
<img="images/hewlett_packard/lj1100xi.gif" alt="Hewlett Packard LaserJet 1100Xi Linked">
```

This HTML is rendered by a browser like this: 

<img src="/images/product_info_image.png" alt="Product Info Page - Main Image" />
<br><br>

When images are turned off, it is rendered in the browser like this:  

<img src="/images/product_info_no_image.png" alt="Product Info Page - Main Image" />
<br><br>


The `alt` tags Zen Cart uses come from the title of the product, category, or item.  If you look at the demo items added to a site  without their images turned on, the display of the Hardware category looks like a dual listing of everything when, in fact, it's just the alt tag providing that second and vital bit of information.

Why use the title instead of the model number or some other information?  Consider the person using a reader and hearing "HD600D".  Accessibility, in this case, is doing your best to let the reader know what the item is or does.  In this case, the alt="Garage Door Opener Model HD600D" would be a LOT more helpful.

Any time you add an image to your site, make sure the alt tag is included and understandable by your customer.

## Pyrotechnics on a Site?

Remember the number of visually challenged individuals in the US?  Well, there's another 1.2 percent of the population that can be affected by "Special Effects" on your website.  Remember the big rage of blinking text in the \'80s and \'90s?  Well, there are a lot of folks who got physically ill from the blinking.  Fast-moving sliders, quick pop-ups, and even color changes on hover can be a problem for these folks.

## What should I test? 

Testing every single page on your site is not practical or even required.  You can get good coverage starting with these tests: 

- Home Page 
- Category Listing page (if you have categories with a depth of 2 or greater)
- Product Listing page 
- Product Info page 
- Shopping Cart page 

Once you've done that, look for non-product pages on your site: 
- See what links are included in the site map - custom pages, define pages, etc. 
- See what links are in the header, sideboxes and footer of your home page.  

## Where's My Help?

As the digital landscape evolves, web accessibility has become a crucial aspect of website development. Ensuring that all users, regardless of disabilities or impairments, can access and interact with online content is not only ethically important but also a legal requirement in many jurisdictions. 

The following articles include important items you should check on your site, commonly used test programs, and other useful tools. By using a combination of these tools, you can gain valuable insights into potential barriers and take necessary steps to make your websites accessible to all users, regardless of their abilities or disabilities.

### Accessibility Tools

The following free tools are valuable in assessing the accessibility of a website.  Most will only test the current page and none are infallible.  Along with viewing the website's actual code, using several of the following tools on any site where accessibility compliance is in doubt is a good practice.

* [Accessibility Checker from Siteimprove](/user/accessibility/tools/siteimprove/)
* [ANDI from SSA](/user/accessibility/tools/andi/)
* [Contrast Ratio Tool from Siege Media](/user/accessibility/tools/siegemedia/)
* [DevTools free version from Axe](/user/accessibility/tools/devtools/)
* [Lighthouse](/user/accessibility/tools/lighthouse/)
* [WAVE from WebAIM](/user/accessibility/tools/wave/)

### Accessibility Widgets 

[Accessibility Widgets](/user/accessibility/tools/widgets/), like the one on this site in the lower right corner, are a popular aid to accessibility.  If you'd like to get a widget for your site, you may purchase one from a [Zen Cart Certified hosting partner](https://ada4zencart.com/index.php?main_page=index&referrer=C4ADA_11659651175).

### Other Useful Tools

Yes, there are several other free tools that can be included in the list to help you meet accessibility standards and ensure your websites are more inclusive. Here are a few notable ones:

* [AChecker](https://websiteaccessibilitychecker.com/checker/index.php) - an open-source accessibility evaluation tool that allows you to upload your web pages for assessment against WCAG standards. It offers detailed reports and guidance for improving accessibility.
* [HTML_CodeSniffer](https://squizlabs.github.io/HTML_CodeSniffer/) - a bookmarklet that scans web pages for accessibility issues, providing feedback based on WCAG guidelines. It is a free, easy-to-use tool that can be added to any browser.
* [NoCoffee Vision Simulator](https://uxpro.cc/toolbox/nocoffee/) - a browser extension that simulates various visual impairments, such as color blindness and low vision, allowing you to experience how your content appears to users with these disabilities.
* [NVDA (Non Visual Desktop Access) Screen Reader](https://www.nvaccess.org/download/) - a free, open-source screen reader for Windows. You can use NVDA to test your website's compatibility with screen readers and ensure a seamless experience for users with visual impairments.
* [VoiceOver](https://www.apple.com/voiceover/info/guide/_1121.html) - a built-in screen reader on macOS and iOS devices. Anyone with access to Apple devices can use VoiceOver to test their websites' accessibility for users with visual impairments.

### Important Accessibility Concerns

* [ALT Text](/user/accessibility/concerns/alt_text/)
* [ARIA Labels](/user/accessibility/concerns/aria_labels/)
* [Color Contrast](/user/accessibility/concerns/color_contrast/)


---
<!-- please keep this at the end --> 
{{< faq_questions >}}
