---
title: Demo Data 
description: Example product and configuration data for new users 
category: first_steps
weight: 10
---

When you install Zen Cart, one of the prompts asks if you wish to install 
the demo data.  Doing so is an excellent way to see a store which is fully set up, allowing you to explore the features of Zen Cart.

Here are some common scenarios which are shown in the demo data.  To view a particular product using its id, use the URL 

```
index.php?main_page=product_info&products_id=YOURPRODUCTID
```

For example, `product 123` would mean the URL above would be 

```
index.php?main_page=product_info&products_id=123
```

- attribute with weight - product 34 has radio buttons that increase the product's weight
- attribute with price - product 1 has two dropdown attributes that increase the product's price; product 34 has radio buttons that increase the product's price. 
- attribute quantity discount - product 159 demonstrates this feature.
- call for price - products 40, 41 and 174 demonstrate the use of the `call for price` setting.
- color swatches -  product 54 shows the use of color samples on a product.  Note that product 44 also offers multiple colors but does not show swatches. 
- combo product - product 173 may be purchased as a downloaded or a shipped physical product.
- customer uploads - product 34 has attributes called "Logo Front" and "Logo Back" which are images the customer would upload. 
- document products - products 170 is a document which is not for sale; product 171 is a document which is for sale. 
- downloads - product 166 has a downloadable attribute to show how to attach a digital media file to a product; product 180 shows a PDF file being attached to a product. 
- downloads, multiple - product 133 has multiple downloads.
- dropdown attributes - product 1 has dropdown attributes.
- free products - products 39, 57, 42 and 43 show how to create a free product.
- free shipping - products 51, 52, 99, 107 demonstrate this feature.
- gift certificates - product 28-32 and 47 demonstrate this feature.
- pricing by attributes - product 47 shows how to modify the price according to which radio button is selected.  (Note that `priced by attributes` differs from `attributes with prices` see [attribute pricing](/user/products/attribute_pricing/)). 
- pricing by length - products 154 and 165 are sold by length.
- pricing by letter - product 134 has per letter pricing.
- pricing by word - product 131 has per word pricing.
- quantity discounts - products 127 and 176 demonstrate this feature.
- quantity limits - products 105 and 106 have maximum purchase quantities; products 53-56 have other quantity restrictions. 
- sales - search for "Sale" 
- specials - search for "Special" 

Demonstrations of many other features can be found simply by searching for the feature name.

### Demo Images 

After Zen Cart 1.5.8, the demo images are not deployed by default.

If you wish to use the demo images to make the demo data look more realistic, they may be obtained from the `zc_install/demo_images` folder, i.e. 

```
cd images
unzip ../zc_install/demo_images/images.zip
```

