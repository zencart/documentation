---
title: Lighthouse 
description: How can I use Google Lighthouse to test accessibility? 
category: tools
weight: 10
---

##  Introduction:

Google Lighthouse, a powerful utility integrated into Google Chrome's Developer Tools, offers you an effective means to evaluate and improve your website's accessibility. In this article, we will explore how you can leverage Lighthouse to meet accessibility standards.

## Accessing Lighthouse 

In Google Chrome, right-click and select "Inspect." 

![Inspect](/images/browser_inspect.png)

A dialog will come up with a number of options on the top menu bar.  Click "Lighthouse," which will be on the right-hand side.

![Lighthouse](/images/lighthouse.png)

Sometimes it can be best to do this in an Incognito window if you have a lot of browser extensions. 

## Understanding Lighthouse:

Lighthouse is an open-source automated tool that assesses the quality and performance of web pages. Originally designed for auditing web performance, it has since expanded to include audits for various aspects of web development, including accessibility. The accessibility audit examines a website for potential barriers that may impede users with disabilities from accessing and interacting with its content.

* **Running the Accessibility Audit** - To utilize Lighthouse for accessibility auditing, You can simply open your website in Google Chrome, access the Developer Tools (F12 key or right-click and choose "Inspect"), and navigate to the "Lighthouse" tab. From there, they can select the "Accessibility" option and run the audit.

* **Analyzing the Accessibility Report** - Once the audit is complete, you will receive an accessibility report detailing issues that need attention. The report is divided into categories, each highlighting specific elements affecting accessibility, such as contrast ratios, semantic structure, keyboard navigation, and more. Each item is accompanied by a severity level, indicating its impact on users, and suggestions for improvement.

* **Addressing Accessibility Issues** - You can prioritize addressing the flagged issues after reviewing the report. Lighthouse not only identifies the problems but also provides guidance on how to rectify them. For example, it may suggest adding alternative text to images, correctly labeling form elements, or improving focus states for keyboard navigation.

* **Ensuring Keyboard Accessibility** - One of the key aspects of web accessibility is ensuring that all functionalities are operable through keyboard inputs alone, as some users rely on assistive technologies like screen readers or keyboard navigation. Lighthouse evaluates a website's keyboard accessibility, and you can use this feedback to make necessary adjustments, such as implementing focus styles and avoiding elements that solely rely on mouse interactions.
* **Assessing Color Contrast** - Color contrast is essential for users with visual impairments. Lighthouse assesses the color contrast of text and background elements, and you can make necessary changes to ensure content remains easily legible for all users.

* **Testing Screen Reader Compatibility** - Screen readers are vital tools for users with visual impairments, and Lighthouse helps identify potential issues that might hinder their proper functioning. By addressing these issues, you can significantly improve your website's compatibility with screen readers.

* **Mobile Responsiveness and Accessibility** - Accessibility is not limited to desktop users alone. Lighthouse evaluates a website's performance on mobile devices and ensures that mobile users, including those with disabilities, can access content seamlessly.

## Conclusion:

Lighthouse provides a valuable resource for you to assess your website's accessibility and identify areas that require improvement. By utilizing this tool and acting on its recommendations, you can make significant strides in meeting accessibility standards and creating a more user-friendly and inclusive online experience for all visitors.
