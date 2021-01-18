# Shopify Tear-Sheet
Add a button on your Product pages that prints a simple Tear Sheet.

## Description 
FORMAT: Shopify Liquid templating language

Tear sheets are used to provide your clients a print out or downloadable PDF of the just the essential information needed from a product to save for considering a future purchase decision. These are great additions to your site and most options aren't free.

This project uses some easy to use code using local storage to get and set product information to automatically print as a simple Tear Sheet and close after the document is printed, saved, or cancelled. When a user triggers an onclick event on an input tag button this code will open a new tab with data populated on a standard blank page without leaving your Shopify website's URL. A function uses native Shopify Liquid variables of the "current_variant" to grab all the details needed from the product page which uses the variant's unique ID plus a unique descriptor to set these variables as items in local storage.

Once data is set in local storage a new page is opened in a separate tab using a blank HTML layout from "tear_sheet.liquid" Template. The basic HTML data is set using stripped down head tag from the theme layout to create a blank space to populate "content_for_layout" with items set in local storage.


#### TIPS
- If you want to add "Dimensions" of the product you can put that info in the "Barcode" input on the product editor page. This code grabs "current_variant.barcode" but you can pretty much enter whatever text you want and call it displayed as whatever information you want it to be called.
- When you print the Tear Sheet in edit mode, you will likely have a bar at the bottom that will get printed. To close this you will need to hide that bar.
    1. Comment out the print code on "page.tear-sheet.liquid" at lines 144-145.
    2. Open the Tear Sheet and choose to close preview
    3. On that page choose to hide that bar (far right)
    4. Go back to the previous page (your Tear Sheet) and it should be gone now.
    5. Close this page and remove the comments at 144-145 on "page.tear-sheet.liquid"
    6. Open Tear Sheet again and it should now print without the bottom bar <br>
        <i>** If this doesn't work you may need to figure this one out yourself and let me know what you did so I can update this README! **</i>

## PRODUCT ELEMENTS
- Title
- Image
- Description
- SKU
- Barcode (or "Dimensions")

## Installation

Describes where to add code and place files.
