# README Module 5

Bonus material!

## Purpose

Describe simple Form Viewer design in Winlink Express.

## Overview

A Form Viewer is just another Winlink Form without any of the submission functionality.

The goal of the viewing Form is to take data presented in a Winlink Template, and set the data into the form fields.

## Requirements

1. Received message must have values provided by a form (i.e. was generated with a Template).
2. Form data (stored in XML format) must be attached to message.
3. A display file named after the html Form must exist in a Templates directory.
4. Update the form fields:
    - Use the following syntax `{var valueName}` where you want values to appear.

The updated fields in the HTML Form will set to XML Form Data values.

Description from the Winlink Development Team:

> "When Winlink Express opens a message, it checks to see if the message has an attached file providing values from a form. The file
attachment name will be "RMS_Express_Form_formname.xml". If it finds a form data attachment, it first looks for the corresponding html
display file in the \callsign\Templates\ folder. If it doesn't find it there, it looks in C:\RMS Express\Global Folders\Templates\. If the display file is found, it is opened, and any insertion fields in the html file are replaced by the values sent from the input form. Use {var field_name} insertion fields to insert the form values." _-[winlink_create_templates.pdf]_

## Simplified How-To

1. Copy the input form and rename it adding `-viewer` to the end of the filename.
2. Remove any functions that aren't needed in the `-viewer` form.
3. Remove any button elements that aren't needed in the `-viewer` form.
4. Remove input elements (but leave the labels and edit them to indicate the data they are describing).
5. Remove the Form element.
6. Add paragraph elements, adding the `{var variableName}` placeholders for the data.

Note: It is worth looking at CSS to clean-up any unintended effects of missing elements.

Alternative: Create a new form from scratch, focusing just on displaying the necessary data in a simple but effective layout and style.

## Install

Copy files into Winlink Express `Global Folders\Templates` directory:

- `5-txrx-forms\txrx-template.txt`
- `5-txrx-forms\tx-form.html`
- `5-txrx-forms\tx-form-viewer.html`

## Use

1. Open Winlink Express.
2. Click 'New Message'
3. Click 'Select Template'
4. Click `txrx-template.txt` in the Global Templates directory.
5. Click the 'Select' button and the default browser will launch, displaying the `tx-form.html` form.
6. Complete the form by adding values to the text boxes.
7. Click Save button to download the form data to a file.
8. Click Submit button and the form data is transferred to the new message window.

When you send the form to another Winlink Express station that also has `txrx-template.txt` and `tx-form-viewer.html` installed and they open the received message, their default browser will open to display the receive form and its data.

## Development and Testing

Once you've filled out the Form and submitted it:

1. Switch back to Winlink Express and save the message in Drafts.
2. Open the Drafts folder and locate the message. _Note the paperclip icon_.
3. Click the paperclip icon and your default browser will open, displaying the Viewer form (and the entered data).
4. Take note of the URL in the browser: it is a temporary local file! You can make changes to the Viewer html and then click on the paperclip icon again to load the Viewer html with your changes _and_ the existing data, without having to fill-out (or receive) another form.

## Resources

- TemplateHelp.txt
- Insertion Tags.txt
- Winlink_Create_Templates.pdf
