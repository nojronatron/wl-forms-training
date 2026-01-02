# READ ME

This directory stores information and references for a training class that introduces Winlink Template and Form development.

Coding HTML, JavaScript, and CSS is an intermediate-level software development skillset.

As much as possible, I have reduced information down to bare minimums so that those new to web development can get onboarded and start creating/editing Winlink Templates and Forms.

## Directory Structure

A compact overview of the repository layout with short descriptions.

```text
. (root): README
|
\_ 1-hello-world - Beginner template: hello-template.txt
\_ 2-hello-form - Simple form + template: hello-form.html, hello-template.txt
\_ 3-form-buildup - Intermediate form + template example: hello-form.html, hello-template.txt
\_ 4-form-style - Styled form example: hello-form.html, hello-tempate.txt
\_ 5-txrx-forms - Transmit/Receive example forms: tx-form.html, rx-form.html, tx-rx-template.txt
\_ boilerplate - WDT's starter form example and an updated HTML 5 version for reference
\_ tools - Helper script copies Template and Form file(s) to your Winlink Express installation
```

Notes:

- Each folder contains a README file with additional information.
- Example folders (1–5) contain progressive learning samples — start with `1-hello-world`.

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

- In VS Code: open the Extensions view (Ctrl+Shift+X), search by name or ID, then click Install. To enable only for this workspace: click the gear for the extension -> "Enable (Workspace)".
- From a terminal (PowerShell):

```powershell
# Install an extension by its ID
code --install-extension <publisher.extension-id>
```

## Getting Help With Templates and Forms

After installing Winlink Express, look in its root installation folder for two files:

- `SkeletonForm.html`: Starter Form file. Add CSS, JavaScript, and a template file to get going quickly.
- `TemplateHelp.txt`: Keywords, usages, and examples for building Templates.

Go to Winlink.org and peruse "HOW - TO Recipes" to find the following helpful resources:

- `insertion_tags.zip`: Contains `Insertion Tags.txt`. A reference of 'Commands' and 'Insertion Tags', with a few usage examples.
- `create_templates.pdf`: Outlines the basics of Templates and Forms, usage of Templates directories, creating a low-complexity form and a display file. Includes an example template and form with form viewer file including CSS styling.
- `rms_express_html_forms.zip`: Contains a PDF version of 'RMS_Express_HTML_Forms' presentation by W4PHS. It has older screenshots in examples, but the concepts are largely the same.
- `rms_express_message_templates.zip`: PDF describes Template basics. Includes a sampling of Control Fields and Insertion Tags for prompting users for data and moving data between Forms and Templates.

Use the Winlink Express Help system:

- Navigate to Setup > Form Settings. This is very high-level information focused on Winlink Express settings, with some Forms advice.
- Navigation to Operations > Templates and HTML Forms. Very brief overview of Forms and who is responsible for the Standard Templates. Links-out to Winlink.org How - To Recipes.

### SkeletonForm

`SkeletonForm.html` provides a basic starting point for creating a custom Winlink Form.

Becuase it violates some HTML 5 standards and WDL standards, it can cause developer headaches later:

- Attribute `action` has hard coded 'localhost' instead of using WDT's standard `{Form_Server}` placeholder.
- Buttons and other input types should be surrounded by 'div' or other structural elements for simplified layout and style application.
- Paragraph element 'p' should be used for text, not layout or functional elements..
- Form elements should have `method` and `enctype` attributes defined, so the Submit button (input of type `submit`) does not need them defined.

My recommendation is to update it to HTML 5 standards before relying on it to build out a custom form.

### TemplateHelp.txt

`TemplateHelp.txt` provides references to many common template commands and tags.

## Copy Helper Tool

PowerShell helper script `Copy-TemplateFormFilesToWinlink.ps1` copies template and form files into your Winlink Express templates folder.

Two common usages are shown below.

```powershell
# Dry-run (show what would be copied, do not copy):
.\Copy-TemplateFormFilesToWinlink.ps1 -srcPath 'C:\path\to\templates' -includeForms $true -WhatIf
```

```powershell
# Real run (perform the copy):
.\Copy-TemplateFormFilesToWinlink.ps1 -srcPath 'C:\path\to\templates' -includeForms $true
```

The script will copy all `*.txt` template files from the specified `-srcPath`, and if `-includeForms` is provided it will also copy `*.html` form files. Use `-WhatIf` to preview actions first.

_Note_: The script does not distinguish between multiple forms and template files, it simply copies them all.

## Thanks to the Winlink Developer Team

The Winlink Developer Team (WDT) is a group of volunteers that take time out of their day to make Winlink (the system, the app, and the feature sets) work, providing support through a public forum, and producing regular updates to program, system, and documentation. They deserve our thanks and support.
