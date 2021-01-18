# Shopify Tear-Sheet
Add a simple, free Tear Sheet function to your Product pages.

## Description 
FORMAT: Shopify Liquid templating language

This project uses some easy to use code using local storage to get and set product information to automatically print as a simple Tear Sheet and close after the document is printed, saved, or cancelled. When a user triggers an onclick event on an input tag button this code will open a new tab with data populated on a standard blank page without leaving your Shopify website's URL. A function uses native Shopify Liquid variables of the "current_variant" to grab all the details needed from the product page which uses the variant's unique ID plus a unique descriptor to set these variables as items in local storage.

Once data is set in local storage a new page is opened in a separate tab using a blank HTML layout from "tear_sheet.liquid" Template. The basic HTML data is set using stripped down head tag from the theme layout to create a blank space to populate "content_for_layout" with items set in local storage.

## PRODUCT ELEMENTS
- Title
- Image
- Description
- SKU
- Barcode (or "Dimensions")


## Installation

Describes where to add code and place files.
