---
search: exclude
title: Image Syntax
sidebar: none
permalink: image-syntax.html
toc: false
---
<span style="color:red">Don't try to look at this file as rendered html. It'll be way wrong. Just look at in as an .md in Typora.</span>span>

The following line shows the syntax to use for inline images.

{% include inline_image.html file="filename.png" alt="" %}

For example:

{% include inline_image.html file="image-20220929091528372.png" alt="" %}

Initial setup steps:

* In Typora, configure **File > Preferences > Images** to match:

  ![image-20221005102602385](../../images/image-20221005102602385.png)

Though not ideal, the easiest image capture and placement steps we have so far are:

*  Copy/paste the line into the Typora .md file.
*  In Figma, copy the desired component image and paste it to the **---Technical Doc---** page.
*  Rename the pasted image *same-name-as-md-file.png* and at the same time copy the name to the clipboard.
*  Export the pasted image as PNG.
*  Wait for the copy complete message to appear at the bottom of the Figma window.
*  Move the PNG from the downloads folder to C:\Dev\healthcare-research-hub-home\images.
*  In Typora, double-click the word *filename* and type ctrl-v to paste the name saved in the clipboard.
*  Review the results in the local web.

> The filename must not include any path info - just the filename.

Alternate steps:

*  Copy/paste the line into the Typora file.
*  In Figma, copy the desired component image and paste it to the **---Technical Doc---** page.
*  Right-click the pasted image and select **Copy/Paste as > Copy as PNG**.
*  Wait for the copy complete message to appear at the bottom of the Figma window.
*  Double-click the word *filename* and type ctrl-v to paste the image into the Typora file.
*  Double check the image because it will disappear in the next step. :-(
*  Delete the following bold text:
   {% include inline_image.html
       file="**![image-20220929091528372](../../../images/**image-20220929091528372.png**).png**" alt="" %}
   So that it looks like this:
   {% include inline_image.html file="image-20220929091528372.png" alt="" %}
* Review the results in the local web.

> The filename must not include any path info - just the filename.