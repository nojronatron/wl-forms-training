# READ ME

This directory will be used to store artifacts for a proposed training class to introduce development of custom Winlink Forms.

## Directory Structure

```text
. (root): README
|
\_ .vscode: Recommended VSCode Extensions for this project.
|
\_ boilerplate: Minimal required code samples.
|
\_ 1-hello-world: First template with most basic features.
|
\_ 2-hello-form: First template and form with only required features.
|
\_ 3-form-buildup: More advanced Form example.
|
\_ 4-form-style: Example styled form.
|
\_ 5-txrx-forms: Minimal Sender and Receiver Forms.
|
\_ tools: Scripts, utilities.
```

## Recommended VSCode Extensions

Below are recommended VS Code extensions to help create, update, and debug files in this project. If they do not install automatically, you can [install/enable them manually](#how-to-installenable-extensions).

### Recommended Extensions

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

After installing Winlink Express, look in its installation folder for two files:

- `SkeletonForm.html`: Starter Form file. Add CSS, JavaScript, and a template file to get going quickly.
- `TemplateHelp.txt`: Keywords, usages, and examples for building Templates.

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
