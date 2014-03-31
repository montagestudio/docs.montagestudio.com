---

layout: montage-studio
title: Montage Studio Releae Notes - Montage Studio Documentation

this-page: release-notes

---

# Release Notes

Product: Montage Studio

Version: alpha (early preview)

Release Date: March 27, 2014

Montage Studio is a development environment that helps streamline the development of MontageJS applications.

## Enhancements

* Added scene editor custom editing environment for 3D scenes
* Improved project bootstrapping progress and error reporting
* Added support for opening SVG and ICO images
* Added LibraryItem for PromiseController
* Added support to indicate deletion of objects and elements in live preview/editing
* Improved styling of modal status interface
* Improved behavior of menus
* Added owner in git branch used for editing
* Changed default preview protocol from https to http to avoid issues when consuming http webservices
* Visually chunk preview access code, ignore whitespace and casing in actual use
* Improved `npm install` behavior; now runs only if node_modules directory is not present in project

## Fixes
 
* Fixed setting window title when displaying activity detail panel
* Fixed offset of childless nodes in DOM explorer
* Fixed renaming an object to the same label
* Fixed importing external objects when merging LibraryItem templates with external references

## Known Issues / Limitations

Montage Studio is alpha software. Please report bugs at [mailto:feedback@montagestudio.com](mailto:feedback@montagestudio.com) for performance and stability issues, data loss, missing or unimplemented features, behavioral or aesthetic issues, and feature and enhancement requests. Provide as much context as possible, including the browser and version you use, detailed steps to reproduce, and a link to your GitHub repository if possible.

The following problems are known:

* Preview access codes: Cannot be revoked
* Package explorer: Cannot move files with drag and drop
* Drag-and-drop file management: Problems with large files
* Performance: UI can be slow
* Stage: It's not very helpful; please ignore its existence
* DOM Explorer: Cannot edit text nodes
* Editing: Changes made to HTML, CSS, and JS files using the Text editor may not be in sync with what is shown in the Component editor.
* Project list (Project page): If you have a large number of repositories not all Montage repositories will appear in the list
* Live preview/editing:

    * Only available for projects using montage 0.14.3 and later (operations might fail otherwise)
    * Undo doesn't work
    * Adding an element or a component after a node with `data­-param=”*”` fails
    * Components that haven't been loaded yet by the preview will not get the changes
    * Adding an element or a component to a childless component doesn't work
    * Changes to a component or element inside a Condition when it's invisible in the preview will not show
    * Changes to a component or element of a Substitution element that is not visible in the preview will not show

# Version: alpha (early preview)

Release Date: March 6, 2014

## Features

This alpha version of Montage Studio includes the following features:

* Live preview/editing: Preview changes in realtime as you assemble your application (see also Known Issues):

    * Add element
    * Add component
    * Add binding
    * Remove binding
    * Add event listener
    * Remove event listener
    * Change object label
    * Change object property
    
* Third-party preview: Send access codes to friends or clients so they can preview your project (while you're editing!)
* GitHub authentication and integration: Pull from and push to GitHub
* Dependency editor: Visually manage npm dependencies
* Text editor with syntax highlighting: Edit HTML, CSS, and JS component files
* Drag-and-drop file management: Upload/Download files from/to the desktop
* Project loader: Initializes new projects and fetches dependencies
* Open existing MontageJS projects (MontageJS version: 0.14.3 and later, for best results with live preview/editing)
* One (server-side) workspace per project

## Known Issues / Limitations

Montage Studio is alpha software. Please report bugs at [mailto:feedback@montagestudio.com](mailto:feedback@montagestudio.com) for performance and stability issues, data loss, missing or unimplemented features, behavioral or aesthetic issues, and feature and enhancement requests. Provide as much context as possible, including the browser and version you use, detailed steps to reproduce, and a link to your GitHub repository if possible.

The following problems are known:

* Preview access codes: Cannot be revoked
* Package explorer: Cannot move files with drag and drop
* Drag-and-drop file management: Problems with large files
* Performance: UI can be slow
* Stage: It's not very helpful; please ignore its existence
* DOM Explorer: Cannot edit text nodes
* Editing: Changes made to HTML, CSS, and JS files using the Text editor may not be in sync with what is shown in the Component editor.
* Project list (Project page): If you have a large number of repositories not all Montage repositories will appear in the list
* Live preview/editing:

    * Only available for projects using montage 0.14.3 and later (operations might fail otherwise)
    * Undo doesn't work
    * Adding an element or a component after a node with `data­-param=”*”` fails
    * Components that haven't been loaded yet by the preview will not get the changes
    * Adding an element or a component to a childless component doesn't work
    * Changes to a component or element inside a Condition when it's invisible in the preview will not show
    * Changes to a component or element of a Substitution element that is not visible in the preview will not show


Last updated March 30, 2014

