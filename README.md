# Winlink Templates And Forms Training Materials

This directory stores information and references for a training class that introduces Winlink Template and Form development.

Warning: Coding HTML, JavaScript, and CSS is an intermediate-level software development skillset.

Materials are set up in modules to build upon each other. By the time you are done with Module 4, you will have the basis for a functional, well designed and styled form.

This material is not comprehensive. As much as possible, I have reduced information down to bare minimums so that those new to web development can get onboarded and start creating/editing basic Winlink Templates and Forms.

## Terminology

Winlink Form: An HTML webpage with a specially crafted Form element designed to work directly with Winlink Express to simplify data input using a familiar web-based user interface.

Winlink Template: A plain text file with Winlink specific syntax that can help rapidly define a standardized Message Layout, and integrate easily with Winlink Forms.

## Project Directory Structure

A compact overview of the repository layout with short descriptions.

```text
. (root): README
|
\_ 1-hello-world - Beginner template: hello-template.txt
\_ 2-hello-form - Simple form + template: hello-form.html, hello-template.txt
\_ 3-form-functionality - Intermediate form + template example: hello-form.html, hello-template.txt
\_ 4-form-style - Styled form example: hello-form.html, hello-tempate.txt
\_ 5-txrx-forms - Transmit/Receive example forms: tx-form.html, rx-form.html, tx-rx-template.txt
\_ boilerplate - WDT's starter form example and an updated HTML 5 version for reference
\_ tools - Helper script copies Template and Form file(s) to your Winlink Express installation
```

Notes:

- Each folder contains a README file with additional information.
- Example folders (1–5) contain progressive learning samples — start with `1-hello-world`.

## Module Instructions

Instructions and background information in these modules will get increasingly more complex and lengthy.

- Module 1 Create a basic Winlink Template: [Hello World](./1-hello-world/README-1.md)
- Module 2: Create a basic Winlink Form [Hello Form](./2-hello-form/README-2.md)
- Module 3: Add [Form Functionality](./3-form-functionality/README-3.md)
- Module 4: Add [Form Style](./4-form-style/README-4.md)
- Module 5 (Bonus): Create a [Form Viewer](./5-txrx-forms/README-5.md)

Understanding the basics introduced in Modules 1 and 2 are probably the most critical short-term goals.

Longer term, it is up to you to seek resources and training to learn more about web development with HTML, CSS, and JavaScript. These skills will help you to build effective, attractive, and widely usable Winlink Forms.

## Recommended Configurations

Included Settings and Configuration files:

- `.vscode/settings.json`: VSCode specific. Enable/Disable format on save. Sets 'Prettier' as default formatter.
- `eslintrc.json`: Opinionated JS linting, focused on ECMA 2015/ES 6. Highly recommended to follow (more) modern standards.
- `htmlhintrc`: Opinionated HTML 5 code style suggestions, based on HTML 5 standards. Recommended to meet most browser expectations.
- `.prettierrc`: Opinionated HTML 5 formatting suggestions. Edit as you see fit.

## Recommended VSCode Extensions

Below are recommended VS Code extensions to help create, update, and debug files in this project. If they do not install automatically, you can [install/enable them manually](#how-to-installenable-extensions).

- bradlc.vscode-tailwindcss — Tailwind CSS IntelliSense (autocomplete & utility class suggestions for Tailwind projects).
- davidanson.vscode-markdownlint — Markdown linter (keeps README and docs consistent and clean).
- jon-rumsey-dev.jr-markdowntoc-vscode — Markdown TOC (auto-generates table of contents for long docs).
- digitalbrainstem.javascript-ejs-support — EJS support (syntax highlighting and snippets for .ejs templates used in HTML/EJS projects).
- dbaeumer.vscode-eslint — ESLint (JS/TS linting to surface errors and enforce code style).
- esbenp.prettier-vscode — Prettier (automatic code formatting for JS/HTML/CSS/Markdown).
- ms-vscode.live-server — Live Server (run a lightweight dev server with live reload for HTML/CSS/JS testing).
- ms-vscode.vscode-typescript-next — TypeScript/JS preview features (optional; provides the latest TypeScript/JS language features).

If you want this list trimmed further or expanded with recommended themes or Git/GitHub helpers, tell me which categories to include.

### How To Install/Enable Extensions

In VS Code:

1. Open the Extensions view (Ctrl+Shift+X).
2. Search by name or ID, then click Install.

Optional: To enable only for this workspace click the gear for the extension and then click "Enable (Workspace)".

You can also install VS Code Extensions from a PowerShell terminal:

```powershell
# Install an extension by its ID
code --install-extension <publisher.extension-id>
```

## Getting Help With Templates and Forms

After installing Winlink Express, look in its root installation folder for two files:

- `SkeletonForm.html`: Starter Form file. Add CSS, JavaScript, and a template file to get going quickly (with caveats noted in [Boilerplate Directory](#boilerplate-directory) comments, below).
- `TemplateHelp.txt`: Keywords, usages, and examples for building Templates.

Go to Winlink.org and peruse "HOW - TO Recipes" to find the following helpful resources:

- `insertion_tags.zip`: Contains `Insertion Tags.txt`. A reference of 'Commands' and 'Insertion Tags', with a few usage examples.
- `create_templates.pdf`: Outlines the basics of Templates and Forms, usage of Templates directories, creating a low-complexity form and a display file. Includes an example template and form with form viewer file including CSS styling.
- `rms_express_html_forms.zip`: Contains a PDF version of 'RMS_Express_HTML_Forms' presentation by W4PHS. It has older screenshots in examples, but the concepts are largely the same.
- `rms_express_message_templates.zip`: PDF describes Template basics. Includes a sampling of Control Fields and Insertion Tags for prompting users for data and moving data between Forms and Templates.

Use the Winlink Express Help system:

- Navigate to Setup > Form Settings. This is very high-level information focused on Winlink Express settings, with some Forms advice.
- Navigation to Operations > Templates and HTML Forms. Very brief overview of Forms and who is responsible for the Standard Templates. Links-out to Winlink.org How - To Recipes.

### Boilerplate Directory

Provides basic starting points for new Winlink Forms. There are 2 files:

- [SkeletonForm.html](./boilerplate/SkeletonForm.html): Generated by the Winlink Development Team.
- [SkeletonForm-Updated.html](./boilerplate/SkeletonForm-Updated.html): Updated by me to meet HTML 5 standards (nearly universal support).

There are issues with the WDT's skeleton form:

- Attribute `action` has hard coded 'localhost' instead of using WDT's standard `{Form_Server}` placeholder.
- Buttons and other input types should be surrounded by `<div>` or other structural elements for simplified layout and style application.
- Paragraph element `<p>` should be used for text, not layout or functional elements.
- Form element has `method` and `enctype` attributes defined, so the Submit button does not need them.

## Copy Helper Tool

PowerShell helper script `Copy-TemplateFormFilesToWinlink.ps1` copies template and form files into your Winlink Express templates folder.

Two common usages are shown below.

```powershell
# Just copy the template file(s) from srcPath
.\Copy-TemplateFormFilesToWinlink.ps1 -srcPath 'C:\path\to\templates'
```

```powershell
# Copy template file(s) and form file(s) from srcPath
.\Copy-TemplateFormFilesToWinlink.ps1 -srcPath 'C:\path\to\templates' -includeForms
```

The script will copy all `*.txt` template files from the specified `-srcPath`, and if `-includeForms` is provided it will also copy `*.html` form files.

_Note_: The script does not distinguish between multiple forms and template files, it simply copies them all.

## Thanks to the Winlink Developer Team

The Winlink Developer Team (WDT) is a group of volunteers that take time out of their day to make Winlink (the system, the app, and the feature sets) work, providing support through a public forum, and producing regular updates to program, system, and documentation. They deserve our thanks and support.
