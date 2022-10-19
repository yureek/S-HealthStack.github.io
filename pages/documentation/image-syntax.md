---
search: exclude
title: Image Syntax
sidebar: none
permalink: image-syntax.html
toc: false
---
Initial setup steps:

* In Typora, configure **File > Preferences > Images** to match:

  ![image-20221005102602385](../../images/image-20221005102602385.png){:.thinborder}

The easiest image capture and placement steps we have so far are:

*  In Figma, copy the desired component image and paste it to the **---Technical Doc---** page.

*  Rename the pasted image ***\<same-name-as-md-file\>*.png**.

*  Export the pasted image as PNG to **C:\Dev\healthcare-research-hub-home\images**.

   > When accessing Figma in a browser window, you have to manually move the file from the downloads folder.

*  Wait for the action completed message to appear at the bottom of the Figma window.

*  In Typora, from **Format > Image > Insert Local Images**, select the image.

* Images render to the web with a dropshadow by default.

  *  To remove the dropshadow, add  `{:.noborder}` to the image markdown syntax.
  *  To replace the dropshadow with a 1px border, add  `{:.thinborder}` to the image markdown syntax.


> The dropshadows and thin borders do not appear in the Typora editor. The `{:.class}` syntax is a GitHub-Flavored Markdown (GFM) proprietary extension. To see an example of the full syntax, click the image above.



**---- Everything below is now superceded by what is above. ---**

<span style="color:red">Don't try to look at this file as rendered html. It'll be way wrong. Just look at in as an .md in Typora.</span>

The following line shows the syntax to use for inline screenshots. theme-samsung.css adds a dropshadow by default.

{% include inline_image.html file="filename.png" alt="" %}

To remove the dropshadow, use:

{% include inline_image.html file="filename.png" class = "noborder" alt="" %}

To replace the dropshadow with a 1px border, use:

{% include inline_image.html file="filename.png" class = "thinborder" alt="" %}

For example, the image below uses:

{% include inline_image.html file="image-20221005102602385.png" class = "thinborder" alt="" %}

Initial setup steps:

* In Typora, configure **File > Preferences > Images** to match:

  ![image-20221005102602385](../../images/image-20221005102602385.png){:.thinborder}

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
       file="**![image-20220929091528372](../../../images/**image-20220929091528372.png**).png**"  class = "shadow" alt="" %}
   So that it looks like this:
   {% include inline_image.html file="image-20220929091528372.png" class = "shadow" alt="" %}
* Review the results in the local web.

> The filename must not include any path info - just the filename.