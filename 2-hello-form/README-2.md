# README-2

## Purpose

Add a Form to the template.

## Template Fields

The template needs to know what form it is associated with. This is accomplished with the `Form:` Field.

The `Form` Field must:

1. Be the first line of the template file.
2. Must have the exact name of the html file.
`Form: hello-form.html`

## Template Var Tags

Use `<var>` Tags to capture data sent from a Form so it can be stored in the Message.

Tags in the example [hello-form-template.txt](hello-form-template.txt) are used to put data into the message:

- The `To:` Field.
- The `Msg:` Field.

In more complex Forms, other Fields like `Subj:` can accept Form data, and additional Tags can be strung together to represent complex data captured by a Winlink Form.

## HTML Page Components

HTML is the language of document __structure__:

- A document has a type: "html" in this case.
- A document type has a language setting for a browser to read: "en" (English).
- An HTML document should have a HEAD and BODY.
- Head: Tells the browser the title of the web page, as well as other information to help it render the web page as intended.
- Body: The Layout and content of the web page. Includes HTML Elements like `<form>` and `<div>` which define various parts of the page.

Recommendation: Stick to the format provided in this example to simplify learning HTML and Winlink Forms.

All HTML elements must be opened and closed. Many HTML elements also have properties called `attributes` which define specific capabilities of the element.

One attribute, `ID` is special in that only one ID value can exist within an entire HTML document. The idea is to allow other frameworks and processes to "target" the element by its ID to do things like:

- Capture its value.
- Set other attributes like style (color, etc), or state (hidden or visible, etc).

More about HTML Element Attributes later.

## Winlink Form Requirements

A Winlink Form will not operate as intended without the following HTML elements:

- `<form>`: Must have an ID that you can name as you wish, and the attributes `post`, `action`, and `enctype` exactly as defined in [hello-form.html](hello-form.html)
- `<input>`: Must have attribute `type="submit"` and (by convention) have attributes `name="Submit" value="Submit"` (note the case-sensitivity).

For every Winlink Form you create, ensure the following:

- The `<Form>` element has these attributes: `method="post" action="http://{FormServer}:{FormPort}" enctype="multipart/form-data"`.
- The `<Form>` element has a unique `id`, named to your preference. For these exercises, just use "RMS_Express_form".
- The `<input>` element has these attributes: `name="Submit" value="Submit"`.

You can optionally add `class` and/or `id` attributes to the `<input>` element, but they are not required for Winlink Form functionality.

Everything else is optional! Depending on the goals of your form, you can add _many_ other elements with `id`, `class`, and other attributes.

## Transferring Data From Form To Template

1. Define a Winlink Template with Tags, named appropriately for what data they will display.
2. Within the `<form>` element, add some `<input type="text">` elements so a user can input data.
3. Name each `input` element with the `name` attribute that matches an existing _Tag_.
4. When the user complets the form and clicks the _Submit_ button, data is transferred to the Winlink Template file for processing.
5. The Winlink Template matches `<input>` element's `name` attribute with existing `var` Tags, and copies the data from the Form to the message.

## Install

Put files into Winlink Express `Global Folders\Templates` directory:

- `hello-form-template.txt`
- `hello-form.html`

## Use

1. Open Winlink Express.
2. Click 'New Message'
3. Click 'Select Template'
4. Click `hello-form-template.txt` in the Global (or callsign) directory.
5. Click the 'Select' button and the default browser will load the Form defined by `hello-form.html`.
6. Complete the form in the browser and click Submit.
7. The new message window is populated with the values from the form.

## Resources

- TemplateHelp.txt
- Insertion Tags.txt
