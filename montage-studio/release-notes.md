---

layout: montage-studio
title: Montage Studio Releae Notes * Montage Studio Documentation

this-page: release-notes

---

# Release Notes

Product: Montage Studio

Version: beta

Release Date: June 4, 2014

Montage Studio is a development environment that helps streamline the development of MontageJS applications.


## Enhancements

### UI/UX
* Adds keyboard shortcuts for switching tabs (Control + Option + Left or Right)
* Adds shortcut (Control + W) to close current opened file
* Enable drag-and-drop tab reordering
* Expands folder on click as opposed to clicks on the disclosure triangle
* Adds tooltips to property names in the property inspector
* Adds Show licenses item to Help menu
- Adds 3D wireframe view and other perspectives to the flow editor
* Improves appearance of the package manager
* Increases contrast and legibility of user interface text
* Improves appearance in Safari

### Commit / Package Management
* Renames work branch to montagestudio/{owner}/{branch}
* Adds feature to merge draft work into the actual branch
* Pushes previously uncomitted changes into recovery commit on launch
* Improves default commit messages and batching behavior
* Discovers Library items from inside dependencies

### Other
* Removes default content of repetition and list library items
* Opens the live view window in a new process where possible
* Uses a unique hash for live view URLs to allow for international user and project names

## Fixes

* Updates cached project list when creating a new project
* Allows whitespace ahead of markup in plain text drop into template
* Ensures a package's LibraryGroup is present when adding a new dependency
* Enables save menuItem only when project is dirty
* Ensures correct opening of files with space in file name
* Fixes error when pressing Esc to close dialog boxes
* Fixes build and download when build product already existed

## Known Issues / Limitations

Montage Studio is beta software. Please report bugs at [feedback@montagestudio.com](mailto:feedback@montagestudio.com) for performance and stability issues, data loss, missing or unimplemented features, behavioral or aesthetic issues, and feature and enhancement requests. Provide as much context as possible, including the browser and version you use, detailed steps to reproduce, and a link to your GitHub repository if possible.

The following problems are known:

* Preview access codes: Cannot be revoked
* Project explorer: Cannot move files with drag and drop
* Project explorer: Drag-and-drop file management: Problems with large files
* DOM explorer: Cannot edit text nodes
* Live preview/editing:

    * Only available for projects using montage 0.14.3 and later (operations might fail otherwise)
    * Undo does not work
    * Adding an element or a component after a node with `data­-param=”*”` fails
    * Components that haven't been loaded yet by the preview will not get the changes
    * Adding an element or a component to a childless component doesn't work
    * Changes to a component or element inside a Condition element that is not visible in the preview will not show
    * Changes to a component or element of a Substitution element that is not visible in the preview will not show

# Version: beta

Release Date: May 24, 2014

## Enhancements

* Improves resilience when dropping non-serialized text/markup on the template explorer
* Removes alphabetic order for the package maintainers list
* Uses icons to display menu shortcuts on OS X
* Adds inject dependencies to the current package at runtime so Library components are immediately available
* Improves Safari compatibility

## Fixes

* Ensures latest changes are available when reopening a document
* Ensures related editor is active when switching document tabs
* Ensures go to overlay preserves correct editor as active when changing documents
* Stops offering to remove owner component
* Prevents error when canceling folder creation
* Prevents deleting a component while editing its label using keyboard shortcuts
* Writes relative path to glTF bundle instead of an absolute URL

## Known Issues / Limitations

The following problems are known:

* Preview access codes: Cannot be revoked
* Project explorer: Cannot move files with drag and drop
* Project explorer: Drag-and-drop file management: Problems with large files
* DOM explorer: Cannot edit text nodes
* Live preview/editing:

    * Only available for projects using montage 0.14.3 and later (operations might fail otherwise)
    * Undo does not work
    * Adding an element or a component after a node with `data­-param=”*”` fails
    * Components that haven't been loaded yet by the preview will not get the changes
    * Adding an element or a component to a childless component doesn't work
    * Changes to a component or element inside a Condition element that is not visible in the preview will not show
    * Changes to a component or element of a Substitution element that is not visible in the preview will not show

# Version: beta

Release Date: May 6, 2014

## Enhancements

* Streams CSS changes live from the text editor to connected previews
* Adds in-app system status reporting from status.montagestudio.com
* Adds list of available editors for a file in a new Open with context menu
* Changes default GitHub authorization to public only; adds option to promote to private access
* Adds warning dialog box when closing the browser tab with unsaved changes
* Adds undo support to the package manager
* Adds background to the image viewer
* Adds the Add Component button to project explorer
* Converts Collada file into glTF bundle when used
* Features restyled login and welcome pages
* Adds Go menu for fuzzy search
* Adds option to specify dependency versions
* Adds options to handle extraneous dependencies
* Enables pressing Enter on any field of the binding or listener dialog boxes
* Adds cache repository list and way to manually refresh
* Improved performance

## Fixes

* Implements document synchronization across editors in Montage Studio; changes made in the component editor now appear in the text editor and vice versa
* Opening and closing listener and binding dialog boxes no longer records unnecessary changes
* Fixes path for creating a file/folder using the context menu in the project explorer
* Various bug fixes and improvements

## Known Issues / Limitations

The following problems are known:

* Preview access codes: Cannot be revoked
* Project explorer: Cannot move files with drag and drop
* Drag-and-drop file management: Problems with large files
* DOM explorer: Cannot edit text nodes
* Live preview/editing:

    * Only available for projects using montage 0.14.3 and later (operations might fail otherwise)
    * Undo does not work
    * Adding an element or a component after a node with `data­-param=”*”` fails
    * Components that haven't been loaded yet by the preview will not get the changes
    * Adding an element or a component to a childless component doesn't work
    * Changes to a component or element inside a Condition element that is not visible in the preview will not show
    * Changes to a component or element of a Substitution element that is not visible in the preview will not show

# Version: beta

Release Date: April 14, 2014

## Enhancements

* Adds sample project: Montage Studio now automatically forks and opens a sample project the first time a user logs in
* Specifies a destination when creating a new component/module
* Improves auto-focus input field in prompt dialog box
* Adds New Folder and Delete to the project explorer context menu
* Improves package manager UI
* Improves drag-and-drop behavior in the project explorer
* Improves performance when opening a component (.reel) for the first time
* Removes Component and Module buttons from project explorer; adds functionality to the project explorer's context menu and the Project menu
* Shows the name of the open document and project in the browser tab
* Accessibility improvements:

    * Adds Alt text for toolbar images
    * Adds label to document tab close button

## Fixes

* Fixes creating a binding with no source path and no target path
* Fixes creating empty listener
* Welcome page: Shows all repositories in the user’s Github account in the project list

## Known Issues / Limitations

The following problems are known:

* Preview access codes: Cannot be revoked
* Project explorer: Cannot move files with drag and drop
* Drag-and-drop file management: Problems with large files
* Performance: UI can be slow
* Stage: It's not very helpful; please ignore its existence
* DOM explorer: Cannot edit text nodes
* Editing: Changes made to HTML, CSS, and JS files using the Text editor may not be in sync with what is shown in the component editor.
* Live preview/editing:

    * Only available for projects using montage 0.14.3 and later (operations might fail otherwise)
    * Undo doesn't work
    * Adding an element or a component after a node with `data­-param=”*”` fails
    * Components that haven't been loaded yet by the preview will not get the changes
    * Adding an element or a component to a childless component doesn't work
    * Changes to a component or element inside a Condition element when it's invisible in the preview will not show
    * Changes to a component or element of a Substitution element that is not visible in the preview will not show
    
# Version: alpha (early preview)

Release Date: March 27, 2014

## Enhancements

* Adds scene editor custom editing environment for 3D scenes
* Improves project bootstrapping progress and error reporting
* Adds support for opening SVG and ICO images
* Adds LibraryItem for PromiseController
* Adds support to indicate deletion of objects and elements in live preview/editing
* Improves styling of modal status interface
* Improves behavior of menus
* Adds owner in git branch used for editing
* Changes default preview protocol from https to http to avoid issues when consuming http webservices
* Visually chunk preview access code, ignore whitespace and casing in actual use
* Improves `npm install` behavior; now runs only if node_modules directory is not present in project

## Fixes
 
* Fixes setting window title when displaying activity detail panel
* Fixes offset of childless nodes in DOM explorer
* Fixes renaming an object to the same label
* Fixes importing external objects when merging LibraryItem templates with external references

## Known Issues / Limitations

The following problems are known:

* Preview access codes: Cannot be revoked
* Project explorer: Cannot move files with drag and drop
* Drag-and-drop file management: Problems with large files
* Performance: UI can be slow
* Stage: It's not very helpful; please ignore its existence
* DOM explorer: Cannot edit text nodes
* Editing: Changes made to HTML, CSS, and JS files using the Text editor may not be in sync with what is shown in the Component editor
* Project list (Project page): If you have a large number of repositories not all Montage repositories will appear in the list
* Live preview/editing:

    * Only available for projects using montage 0.14.3 and later (operations might fail otherwise)
    * Undo doesn't work
    * Adding an element or a component after a node with `data­-param=”*”` fails
    * Components that haven't been loaded yet by the preview will not get the changes
    * Adding an element or a component to a childless component doesn't work
    * Changes to a component or element inside a Condition element when it's invisible in the preview will not show
    * Changes to a component or element of a Substitution element that is not visible in the preview will not show

# Version: alpha (early preview)

Release Date: March 6, 2014

## Features

This alpha version of Montage Studio includes the following features:

* Live preview/editing: Preview changes in real time as you assemble your application (see also Known Issues):

    * Add an element
    * Add a component
    * Add binding
    * Remove a binding
    * Add an event listener
    * Remove an event listener
    * Change an object label
    * Change an object property
    
* Third-party preview: Send access codes to friends or clients so they can preview your project (while you're editing!)
* GitHub authentication and integration: Pull from and push to GitHub
* Dependency editor: Visually manage npm dependencies
* Text editor with syntax highlighting: Edit HTML, CSS, and JS component files
* Drag-and-drop file management: Upload/Download files from/to the desktop
* Project loader: Initializes new projects and fetches dependencies
* Open existing MontageJS projects (MontageJS version: 0.14.3 and later, for best results with live preview/editing)
* One (server-side) workspace per project

## Known Issues / Limitations

The following problems are known:

* Preview access codes: Cannot be revoked
* Project explorer: Cannot move files with drag and drop
* Drag-and-drop file management: Problems with large files
* Performance: UI can be slow
* Stage: It's not very helpful; please ignore its existence
* DOM explorer: Cannot edit text nodes
* Editing: Changes made to HTML, CSS, and JS files using the Text editor may not be in sync with what is shown in the Component editor
* Project list (Project page): If you have a large number of repositories not all Montage repositories will appear in the list
* Live preview/editing:

    * Only available for projects using montage 0.14.3 and later (operations might fail otherwise)
    * Undo doesn't work
    * Adding an element or a component after a node with `data­-param=”*”` fails
    * Components that haven't been loaded yet by the preview will not get the changes
    * Adding an element or a component to a childless component doesn't work
    * Changes to a component or element inside a Condition element when it's invisible in the preview will not show
    * Changes to a component or element of a Substitution element that is not visible in the preview will not show


Last updated June 4, 2014

