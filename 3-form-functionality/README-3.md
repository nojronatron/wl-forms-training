# README-3

## Purpose

Build out Form features to improve capabilities.

## Javascript

JavaScript, in conjunction with Web APIs are the "action" components of websites:

- Adds capabilities to a 'static' website built with HTML.
- Can convert values and perform math on inputs, so that correct output values are provided to the template/Winlink Message.
- Enables developer to make decisions and change the form while it is loaded in the user's browser.

The more you know about JavScript and Web APIs, the more you can do.

## What This Module Covers

This training module is _not comprehensive_:

- Introduction to one simple use case for Javascript in a Winlink Form.
- Overview of good practices when writing Javascript to enhance Winlink Forms you develop.

## What to Expect

If you have none or very little programming experience:

- Can be difficult to understand what is going on.
- Will require additional outside help to get going, including training courses (free and/or paid) available online and in-person.
- Might be helpful to pair-up with an experienced programmer to "pair program": One person coding at the keyboard, the other person researching and instructing the keyboardist, and both discussing what (and how) to implement.

If you are an experienced programmer:

- This content might appear to be obvious and oversimplified
- Can pick-up the concepts and get going right away enhancing a Winlink Form.

The idea is to introduce the capabilities so you can pick it up and run with it (tm).

## Web APIs

These are built into modern browsers, allowing Javascript to interact with the browser document.

- Enable editing HTML Elements. Use the `id` field to allow Javascript to find and change element attributes such as visibility or style (Style/CSS is covered in the next module).
- Intercept click and other events to add functionality.
- Validate user inputs to ensure poorly formed data is unlikely to make it into the Message.
- Enable saving form-entered data to a file, or loading the form data _from_ a file.
- Allows access to the browser memory to temporarily store data from Form use to Form use (i.e. Storing your Callsign or a fragment of data from the prior form submission).

## Advice

Some examples here (and elsewhere) are going to break lots of standards and best practices.

- Try to stick with ECMA 2015/ES 6 standards to wide browser compatibility and modern capabilities and performance.
- Avoid loading javascript inline unless there is good reason for it:
  - Must limit the number of files to distribute.
  - Performance and maintainability aren't a big concern.

Inline Javascript:

- Load the script in a single `<script>` element either in the `<head>` of the document, or right before the end of the closing `</body>` element:
- Most of the time add the `<script>` element at the end of the `<body>` block. This keeps the Javascript interpreter from blocking page rendering for better perceived page performance.
- Only add `<script>` inside the `<head>` element when it is _required_ in order to render the page at all.

It is best practice to referentially load javascript from one or more files:

- `<script src="path/to/script.js" deferred></script>`
- Improves readability and maintainability.
- Enhances collaborative contributions, limiting opportunity for merge conflicts in the repository.

## Helpful Tools

Browser Developer Tools:

- Modern browsers have this built-in.
- Menu > More Tools > Developer Tools.
- CTRL + SHIFT + I
- `Inspector` or `Elements` Tab: Interact with HTML, CSS, and "events" that make up the structure, style, and behavior (respectively) of the web page.
- Console Tab: Display output from "console log" statements.
- Network Tab: Shows network interactions between Web API (the browser) and remote services.
- Application Tab: Displays browser Local Storage, Cookies, and other storage types.

## Basic Javascript

Semicolon: Defines the end of a line of code `;`

'//': Everything following this on the same line is a comment and is not executed.

Javascript "Console Log":

- `console.log("")`: Add this to any area inside `<script>` block to output information to the Developer Tools' _Console_ tab.

Template Literal: Concatenate text with variable values (strings). ```var word="world!"; console.log(`Hello ${word}`;```

Function: Keyword defines an encapsulated code block that can be referenced from elsewhere. `function sayHello() { console.log('Hello World!')};`

## Web API

Web API allows Javascript interaction with the web page through pre-defined functions and properties.

For most Winlink Forms, the most useful Web API tools are probably:

- Selecting an HTML Element to get or set one of its attributes: `let myCallsignElement = document.getElementById('myCallsign')`. Access the element using myCallsignElement to change an attribute or add/remove event listener (see next subsection).
- Managing document load and unload using Javascript.
- Enabling document download (and possibly upload).

## Events

These are things like button click ('click') or when tabbing away from a text box ('blur').

Onload ('onload') allows javascript to run a function while the web page is loading, before the user can interact with the page.

Two ways to set an event "handler":

1. Javascript + WebAPI: `addEventListener('click', function() {...});`
2. HTML inline attribute 'onClick': `<input type="button" onclick="myFunction();">Click me</input>`

Javascript + WebAPI is modern, widely supported, provides wide flexibility in defining event-based actions, and is easier to maintain.

Using HTML attribute `onClick=""` is still supported in most browsers but:

- It is falling out of support.
- Is more difficult to maintain because it is mixed-in with HTML.
- Has more limited capability than using Web API add/removeEventListener() functions.
- Unable to handle Event features like bubbling.

Try to avoid using inline handlers like 'onClick' except for in the most basic of projects.

## Transferring Data From Form To Template

1. Define a Winlink Template with Tags, named appropriately for what data they will display.
2. Within the `<form>` element, add some `<input type="text">` elements so a user can input data.
3. Name each `input` element with the `name` attribute that matches an existing _Tag_ in step 1.
4. When the user complets the form and clicks the _Submit_ button, data is transferred to the Winlink Template file for processing.
5. The Winlink Template matches `<input>` element's `name` attribute with existing `var` Tags, and copies the data from the Form to the message.

Define Template Tags:

```text
Msg:

<var myCall>
<var toCall>
```

Define Form Names that match Template Tags:

```html
<div>
    <label for="mycall">Enter your callsign:</label>
    <input type="text" name="mycall" id="myCallsign" />
    <label for="tocall">Enter recipients callsign:</label>
    <input type="text" name="tocall" id="yourCallsign" />
</div>
```

## Saving Form Data To File

```javascript
// Saves form data to Downloads folder
function downloadFile(fileContent, fileName) {
    // 1. Create a Blob from the content ('application/json' is a good portable alternative)
    const myFile = new Blob([fileContent], { type: 'text/plain' });

    // 2. Create a URL for the Blob
    const fileURL = URL.createObjectURL(myFile);

    // 3. Create a temporary anchor element
    const dlBtn = document.createElement('a');
    dlBtn.setAttribute('href', fileURL);
    dlBtn.setAttribute('download', fileName); // Suggests a file name for the download

    // 4. Append to the DOM and programmatically click the link
    document.body.appendChild(dlBtn);
    dlBtn.click();

    // 5. Clean up by removing the link and revoking the URL
    document.body.removeChild(dlBtn);
    URL.revokeObjectURL(fileURL);
}
```

## Install

Put files into Winlink Express `Global Folders\Templates` directory:

- `tagged-template.txt`
- `functional-form.html`

If you define the javascript in its own file, copy it to the same directory as well.

## Use

1. Open Winlink Express.
2. Click 'New Message'
3. Click 'Select Template'
4. Click `tagged-template.txt` in the Global (or callsign) directory.
5. Click the 'Select' button and the default browser will launch, displaying the `functional-form.html` form.
6. Complete the form by adding values to the text boxes.
7. Click Save button to download the form data to a file.
8. Click Submit button and the form data is transferred to the new message window.

## Resources

- TemplateHelp.txt
- Insertion Tags.txt
- Many online resources including [Mozilla Developer Network (MDN)](https://mdn.com)
