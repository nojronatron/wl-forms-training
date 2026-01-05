# README-3

## Purpose

Build out Form features to improve capabilities.

## Javascript

JavaScript, in conjunction with Web APIs are the "action" components of websites:

- Adds capabilities to a 'static' website built with HTML.
- Can convert values and perform math on inputs, so that correct output values are provided to the template/Winlink Message.
- Enables developer to make decisions and change the form while it is loaded in the user's browser.

Developing websites with JavaScript is not simple, however it is not hard to find solutions to problems you encounter.

This module does not intend to teach you JavaScript so that you can walk-away ready to write a website.

The goal is to introduce commonly used aspects and code patterns to apply and get going quickly with Winlink Forms.

You can copy-paste as much (or as little) of the code as you wish.

> The more you know about JavScript and Web APIs, the more you can do.

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

It is usually good practice to referentially load javascript from one or more files:

- `<script src="path/to/script.js" deferred></script>`
- Improves readability and maintainability.
- Enhances collaborative contributions, limiting opportunity for merge conflicts in the repository.
- For Winlink Express distribution, especially in offline scenarios, having to distribute more files and troubleshoot form usage and operation will be more difficult.

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

## Loading Form Data From File

This is a little simpler than saving data to a file, but it is still necessary to:

1. Set an HTML Element to an input of type "file".
2. Optionally create a button the user can press to start loading a file.
3. Allow the user to locate the file to load.
4. Parse the loaded data. This can be difficult depending on the type of data such as Numbers vs. Date vs. Strings.
5. Load the Form elements with the file data. Larger forms with more form fields results in more code necessary to complete the task.

```html
<input type="file" id="txtfiletoread" accept=".txt" />
<input name="loadbtn" type="button" class="loadDataButton" id="loadbtn" value="Load Race data" title="Load data from a file." />
```

This is the outdated way to set a click event: `<input type="button" onclick="document.getElementById('txtfiletoread').click();">Load File</input>`

Instead, keep HTML easy to read and maintain:

```html
<section>
    <input type="button" name="SaveButton" id="saveButton" value="Save Data" />
    <input type="button" name="LoadButton" id="loadButton" value="Load Data" />
    <input type="file" id="txtfiletoread" accept=".txt" />
</section>
```

Use `addEventListener()` to trigger the FileReader API code:

```javascript
const fileSelector = document.getElementById('txtfiletoread');

const loadButton = document.getElementById('loadButton');
loadButton.addEventListener('click', () => {
  fileSelector.click();
});

fileSelector.addEventListener('change', (event) => {
  const file = event.target.files[0]; // Get the first selected file
  if (file) {
    readFileData(file);
  }
});

function readFileData(file) {
    const fileReader = new FileReader();

    // this subsection of code is not run until FileReader has tried to load file data
    fileReader.onload = (e) => {
        // prompts user for a filepath and name
        const content = e.target.result;
        console.log('File content: content');

        // parse the JSON data for convenient access
        let jsonData = JSON.parse(content);

        // check for valid data and log an error if empty
        if (jsonData === undefined || jsonData.length < 1) {
            console.error('JSON string data is empty. No file data to load.');
        } else {
            console.log("File content parsed as JSON:", jsonData);

            // assign the values to the input elements
            document.getElementById('myCallsign').value = jsonData.MyCallsign;
            document.getElementById('yourCallsign').value = jsonData.YourCallsign;
        }
    };

    // check for fileReader error and log a message if for example file not found
    fileReader.onerror = (e) => {
      console.error("Error reading file:", e.target.error);
    };

    // Read the file as text
    fileReader.readAsText(file);
}
```

And then use CSS to hide the "file" type input element to keep the UI tidy:

```css
#txtfiletoread {
  display: None;
}
```

## Storing Data Locally

Here is an exercise to try:

1. Add the `saveToLocalStorage()` function code to the `<script>` area of `styled-form.html`.
2. Create a button called "Store In Browser" on `styled-form.html` (in the `<body>`, probably next to the other buttons).
3. Create an event listener (`addEventListener('click' () => {});`) that calls the function below, taking a value from an input element (try `myCallsign`).
4. Save the changes.
5. Load the form into a browser.
6. Open the Developer Tools and click on the Application tab, Local storage node, `file://` node.
7. The key-value data should appear in the child node after clicking your new Store In Browser button.

```javascript
function saveToLocalStorage(itemKey, itemValue) {
    var existingItem = localStorage.getItem(itemKey);

    if (existingItem.length > 0) {
        localStorage.removeItem(itemKey);
    }

    console.log('Storing item to browser memory:', itemKey, itemValue);
    localStorage.setItem(itemKey, itemValue);
}
```
## JavScript Built-In Objects

Primitives: Simple representations of values.

Objects:

- More robust data representations with built-in state and capabilities, such as Arrays and Date objects.
- Other representations: Undefined, Not a Number, Null, etc.

JavaScript is full other other functionality. Probably the most commonly used are `map()` and `forEach()`. This is true specifically for Winlink Forms.

- Both iterate over collections (arrays) of items.
- Both accept a array and a function as input arguments.
- `map()`: Returns a new array of items resulting from calling the function on every item in the provided array.
- `forEach()`: Executes the provided function once for each array element.

Parsing Strings (i.e. Is this a string and if so return its value):

- Fairly simple due to a JavaScript feature called [String Coersion](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String#string_coercion).
- Stick with using [string primitives](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String#string_coercion).
  - String literals: " " or ' '
  - String concatenation: `"Hello" + " " + "World!"` or ```let hello="Hello"; let world="World!";console.log(`${hello} ${world}`);```
  - No need to use `new String()` to create strings.
- Use `indexOf()`, `match()` (a regular expression function), `replace()`, and `substring()` to verify and manipulate values of a string.

Parsing Numbers:

Parsing a Number is a little tougher due to several ways they are presented in JavaScript:

- Floating-point (rational) numbers: The default, most common handling.
- Binary.
- Hexadecimal.
- Not A Number (NaN).
- null.
- undefined.

Parsing other JavaScript Objects:

- Look up the Object type on MDN to determine the best method: [JavaScript Standard Built-In Objects](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects)

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
- JavaScript [Beginner's Tutorials](https://developer.mozilla.org/en-US/docs/Web/JavaScript#beginners_tutorials) on Mozilla Developers Network
