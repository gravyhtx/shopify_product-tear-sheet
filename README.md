# Shopify // Tear Sheet
<br>
Print a simple Tear Sheet on Product pages made in Shopify's Liquid templating language with localstorage.
<br><br>
<i>** Some coding knowledge required. **</i>
<br><br>
<h3>TABLE OF CONTENTS</h3>

- [Description](#description)<br>
- [Product&nbsp;Elements](#product-elements)<br>
- [Installation](#installation)<br>
<br>

## Description

__DETAILS__

Tear sheets are used to provide your clients a print out or downloadable PDF of the just the essential information needed from a product to save for considering a future purchase decision. These are great additions to your site and most options aren't free.

This project uses some easy to use code using local storage to get and set product information to automatically open a new tab and print as a simple Tear Sheet and close after the document is printed, saved, or cancelled. When a user triggers an `onclick` event on an input tag button this code will open a new tab with data populated on a standard blank page without leaving your Shopify website's URL. A function uses native Shopify Liquid variables of the `current_variant` to grab all the details needed from the product page which uses the variant's unique ID plus a unique descriptor to set these variables as items in local storage.

Once data is set in local storage a new page is opened in a separate tab using a blank HTML layout from the `tear_sheet.liquid` Template. The basic HTML data is set using stripped down head tag from the theme layout to create a blank space to populate `{{ content_for_layout }}` with items set in local storage.
<br>

__TIPS__

* If you want to add "Dimensions" of the product you can put that info in the __"Barcode"__ input on the product editor page. This code grabs `{{ current_variant.barcode }}` but you can pretty much enter whatever text you want and call it displayed as whatever information you want it to be called. It doesn't necessarily need to be the "Barcode"... same goes for __"SKU"__, but for the purposes of this demo the "SKU" is used as it was intended and the "Barcode" is used to display the dimensions.

* When you print the Tear Sheet in edit mode, you will likely have a bar at the bottom that will get printed. To close this you will need to hide that bar. Either by enter
    - Comment out the "PRINT WINDOW" code on `page.tear-sheet.liquid` from lines [224-254](https://github.com/gravyhtx/shopify_product-tear-sheet/blob/main/Templates/page.tear-sheet.liquid).
    - Open the Tear Sheet and choose to close preview on the bottom bar.
    - Close this tab and remove the comments previously set at [224-254](https://github.com/gravyhtx/shopify_product-tear-sheet/blob/main/Templates/page.tear-sheet.liquid) on `page.tear-sheet.liquid`
    - Reopen Tear Sheet and it should now print without the bottom bar.
        <p><i>** If this doesn't work you may need to figure this one out yourself and let me know what you did so I can <a href="https://github.com/gravyhtx/shopify_product-tear-sheet/issues" target="_blank">update this README</a>. **</i></p>
        <p><i>This same concept can be applied to any HTML code with Vanilla JavaScript. You'll grab the elements to insert into the tear sheet based on your own variables or grabbing elements from the DOM in place of the Liquid syntax.</i></p>
<br>

## Product Elements

This is a list of all the elements grabbed from the product page used in this project:
- Title
- Image
- Description
- SKU
- Barcode (or "Dimensions")
- Price
<br><br>
<h3>Shopify Liquid Varibles</h3>

__Title:__ `{{ product.title }}`<br>
__Image:__ `{https://cdn.shopify.com/path/to/{{product.featured_image}}`<br>
__Description:__ `document.getElementById('descPrint').innerHTML` _[get all HTML code inside description]_<br>
__SKU:__ `{{ current_variant.sku }}`<br>
__Barcode:__ `{{ current_variant.barcode }}`<br>
__Price:__ `{{ current_variant.price | money }}`<br><br>

The `current_variant` variable is pimarily where we are getting the data from the each page's unique elements. This may not be the name of the variable on your theme so look for an assignment to the `product.selected_or_first_available_variant` which in the Debut theme assigns the variable at `{%- assign current_variant = product.selected_or_first_available_variant -%}` on line `11` found in `Snippets/product-template.liquid`. The product page code on the Theme I am working with is called `product.liquid` in the same folder, `Snippets/product-template.liquid`. If necessary on your Theme, find the `product.selected_or_first_available_variant` and either use the varible your theme has set, create your own variable, or use `product.selected_or_first_available_variant` instead of the `current_variant` variable as used in `product.liquid` as found in this repository.

<br>

## Installation

The folders in this repository are named after the same folder locations found in the Shopify Liquid Code Editor. If you're unfamiliar with how to get to the editor, check the Shopify Documentation, specifically by <a href="https://help.shopify.com/en/manual/online-store/os/using-themes/change-the-layout/theme-code" target="_blank">clicking here</a>. I included some comments in the `.liquid` files but let's go over how to install these files.


<h3>Setup</h3>

This code requires a page to be made in your store so we can create a path for our new tear sheet page to be printed without leaving your domain (instead of creating a new "about:blank" window). In order to do this we need to add and edit a couple files into your code editor folders.

First, create a new file in the Layout folder called `tear_sheet.liquid` and replace with the code found in the [Layouts](https://github.com/gravyhtx/shopify_product-tear-sheet/blob/main/Layout/tear_sheet.liquid) folder in this repository. This will serve to create a blank HTML page for our Tear Sheet so that there will be no influence from the `theme.liquid`.

Navigate to the Templates folder next and click "Add a new template". You will need to choose "page" from the dropdown and enter "tear-sheet" in the input to create a template for `page.tear-sheet.liquid` where you will enter the code found in the [Templates](https://github.com/gravyhtx/shopify_product-tear-sheet/blob/main/Templates/page.tear-sheet.liquid) folder.

You can now create your Tear Sheet page in your "SALES CHANNELS" by navigating from "Online Store" > "Pages" and add a new page called "Tear Sheet". Once created, this page will be located in the URL as `/pages/tear-sheet` so we can create a path for our new tear sheet page to be printed without leaving your domain (instead of creating a new "about:blank" window).

__THIS IS VERY IMPORTANT!__ Before saving this page, you will select the Template from the dropdown menu under "Template suffix" and choose `page.tear-sheet.liquid` which is the file you set up in Templates. If you don't see it then make sure you have this file in your Templates folder in the Code Editor.

Ok. Now you can save your "Tear Sheet" page.

You have now created a blank page ready to accept values from local storage based on the items you will set in your Product page's code. In order to set items you must add code to `product.liquid` found in the [Snippets](https://github.com/gravyhtx/shopify_product-tear-sheet/blob/main/Snippets/product.liquid) folder.

Go back to the Code Editor and you will find a file usually called something like `product-template.liquid` or `product.liquid` in your "Snippets" folder. You may have to look around but it's going to be wherever the main product content code is Here you will need to add two things to this file. You will need a clickable button and some script to save the [Product&nbsp;Elements](#product-elements) that will populate your Tear Sheet.

Add all of the script from [Snippets/product.liquid](https://github.com/gravyhtx/shopify_product-tear-sheet/blob/main/Snippets/product.liquid) to the end of the `product.liquid` file in the "Snippets" folder of your Code Editor. Be sure to edit the path to your logo on line `37` (after the 'imgPrint' variable) before you're ready to test this out.

Last, use the HTML found in [`Product_Page/tear-sheet-button.html`](https://github.com/gravyhtx/shopify_product-tear-sheet/blob/main/Product_Page/tear-sheet-button.html) and add the code wherever you want to have the clickable "TEAR SHEET" button. I had to add it in a Custom HTML module and style it to fit on my project.

Now you should have a clickable button on every product page. When you click on that button the script will grab all the [Product&nbsp;Elements](#product-elements), set those values in local storage, open the "Tear Sheet" page in a new tab, and automatically open the Print dialogue which will close the tab once the user chooses to print, save, or cancel. Each time you go to a new product page or refresh the current product page `localstorage` will be cleared and ready to accept new values without unnecessarily using up the user's localstorage.
<br><br>


_Note: As mentioned above, different themes may have the Product page code in other folders. You may need to dig around to find where the main HTML inside the Product pages is located. Experiment with implementing the `<input>` button found in this repository's `product.liquid` code. You can choose to use a different tag but this code should execute the same way if you make the necessary changes to your code to trigger the `printDiv()` function._
<br><br>

_Made with love by Grävy Design Co. // @gravyhtx_