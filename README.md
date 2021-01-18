# Shopify Tear-Sheet
<br>
Print a simple Tear Sheet Product pages with Shopify Liquid templating language.
<br><br>
<h3>TABLE OF CONTENTS</h3>

- [Description](#description)<br>
- [Product&nbsp;Elements](#product-elements)<br>
- [Installation](#installation)<br>
<br><br>

## Description

__DETAILS__

Tear sheets are used to provide your clients a print out or downloadable PDF of the just the essential information needed from a product to save for considering a future purchase decision. These are great additions to your site and most options aren't free.

This project uses some easy to use code using local storage to get and set product information to automatically open a new tab and print as a simple Tear Sheet and close after the document is printed, saved, or cancelled. When a user triggers an `onclick` event on an input tag button this code will open a new tab with data populated on a standard blank page without leaving your Shopify website's URL. A function uses native Shopify Liquid variables of the `current_variant` to grab all the details needed from the product page which uses the variant's unique ID plus a unique descriptor to set these variables as items in local storage.

Once data is set in local storage a new page is opened in a separate tab using a blank HTML layout from the `tear_sheet.liquid` Template. The basic HTML data is set using stripped down head tag from the theme layout to create a blank space to populate `{{ content_for_layout }}` with items set in local storage.
<br><br>

__TIPS__

* If you want to add "Dimensions" of the product you can put that info in the __"Barcode"__ input on the product editor page. This code grabs `{{ current_variant.barcode }}` but you can pretty much enter whatever text you want and call it displayed as whatever information you want it to be called. It doesn't necessarily need to be the "Barcode"... same goes for __"SKU"__, but for the purposes of this demo the "SKU" is used as it was intended and the "Barcode" is used to display the dimensions.

* When you print the Tear Sheet in edit mode, you will likely have a bar at the bottom that will get printed. To close this you will need to hide that bar.
    - Comment out the print code on `page.tear-sheet.liquid` at lines 144-145.
    - Open the Tear Sheet and choose to close preview
    - On that page choose to hide that bar (far right)
    - Go back to the previous page (your Tear Sheet) and it should be gone now
    - Close this page and remove the comments at 144-145 on `page.tear-sheet.liquid`
    - Open Tear Sheet again and it should now print without the bottom bar
        <p><i>** If this doesn't work you may need to figure this one out yourself and let me know what you did so I can <a href="https://github.com/gravyhtx/shopify_product-tear-sheet/issues" target="_blank">update this README!</a> **</i></p>
        <br><br>

## Product Elements
This is a list of all the elements grabbed from the product page used in this project:
- Title
- Image
- Description
- SKU
- Barcode (or "Dimensions")
- Price

## Installation

Describes where to add code and place files.
