---
title: Accessibility Overview
description: WCAG and Section 508
category: accessibility
weight: 5
---

Before you read this article, please be sure you are familiar with [Basic Terms](/user/first_steps/basic_terms/) used in describing Zen Cart files. 

### What is Accessibility? 

Web Content Accessibility Guidelines (WCAG) is developed through the W3C process in cooperation with individuals and organizations around the world, with the goal of providing a single shared standard for web content accessibility that meets the needs of individuals, organizations, and governments internationally.  You'll find a great article on the [W3C Web Design and Applications page](https://www.w3.org/standards/webdesign/accessibility).

What follows are just a few of the things that Zen Cart users should consider when creating or editing their template and site.  Think of it as a quick triumvirate of accessibility steps to think about.  These three are the most common accessibility standards that should be considered when adding anything to your site.

#### Visual Problems

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

#### What Am I Looking At?

But Accessibility is not just about the visually challenged.  What about the folks in developing countries or a remote ranch in Texas or Montana?  What's the average internet speed in the Alaskan Bush?  You might wonder what they would have in common but, probably just because you're in your home or office with megabytes of bandwidth.  There are folks who are still using virtual dial-up speed to surf the net!

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

#### Pyrotechnics on a Site?

Remember the number of visually challenged individuals in the US?  Well, there's another 1.2 percent of the population that can be affected by "Special Effects" on your website.  Remember the big rage of blinking text in the \'80s and \'90s?  Well, there are a lot of folks who got physically ill from the blinking.  Fast-moving sliders, quick pop-ups, and even color changes on hover can be a problem for these folks.

#### Where Can I find ...?

The manager at your local grocery will keep the milk, bread, and eggs separate.  Not to meet some federal, state, or local standard, but to make you go throughout the store while shopping rather than go to one counter and leave.  Is it good practice for your website?  Probably not.  If I'm looking for the latest team tee shirts for my wife and me, what would be the most convenient way to shop for those?  Maybe mixing the men's and women's together in one product is over the top but, having a separate product for each size or color can go the other way and frustrate the customer.  Imagine having to go to one page for the shirt, another for the color, and another for the size.  You might think no one would do that but, it happens.  Zen Cart provides the Attributes Controller to help you consolidate the options for an item and make shopping easier for your client.

Additionally, from the SEO standpoint, search engines frown upon separate products for each option and reward logical attribute use.

### Where's My Help?

As the digital landscape evolves, web accessibility has become a crucial aspect of website development. Ensuring that all users, regardless of disabilities or impairments, can access and interact with online content is not only ethically important but also a legal requirement in many jurisdictions. 

The following articles include Important items you should check on your site, commonly used test programs, and other useful tools. By using a combination of these tools, website owners can gain valuable insights into potential barriers and take necessary steps to make their websites accessible to all users, regardless of their abilities or disabilities.

- [Accessibility Tools](/user/accessibility/accessibility_tools/)
- [Accessibility Concerns](/user/accessibility/accessibility_concerns/)

---
<!-- please keep this at the end --> 
{{< faq_questions >}}
