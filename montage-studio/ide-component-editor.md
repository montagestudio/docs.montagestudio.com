---

layout: montage-studio
title: Component Editor - Montage Studio Documentation

prev-page: ide-package-explorer
this-page: ide-component-editor
next-page: ide-text-editor

---

# Component Editor

This is where you perform your core development tasks. The Component editor consists of five areas: Template explorer, Stage, DOM explorer, Properties inspector (hidden by default), and Library.

<figure>
    <img src="/images/montage-studio/ide-overview/fig04.jpg" alt="coming soon" style="width: 550px;">
    <figcaption>The Component Editor</figcaption>
</figure>

The Component editor supports browser-style tabs, so you can open and work on multiple components at the same time.

## Library

 The Library is a tabbed container that holds all the items at your disposal to assemble an application. 
 
 The Library tab provides access to the components, controllers, and converters (aka prototypes in MontageJS speak) that can be used in the current project. It is divided into three collapsible groups: 
 
 * **Project** (the top group, which is identified by the name of the current project) lists the components in the UI folder of your project.
 * **Montage** shows the converters and controllers that are part of the core MontageJS framework.
 * **Digit** exposes the touch-optimized components of the Digit widget set. 
 
 You can minimize the groups by clicking the triangle icon in the top left of a group's title bar.
 
 The Search box at the top enables you to quickly find a component, and the icon to the right lets you switch between List and Grid views of the contents of the Library tab.
 
 The Assets tab provides access to the binaries and other content stored in the Assets folder of your project. (Note: This feature is still a work in progress and not fully functional yet.)
 
## DOM Explorer

This is where you add the user interface components you want to use in your application. The DOM explorer presents a lower-level DOM tree view of the current template. This tree follows the same structure as the DOM tree of the elements with which the components are associated in the template (for example, a button component is associated with a button HTML element).

When building your user interface, you drag prebuilt components from the Library to the DOM explorer to form a component tree. This component tree represents the structure of the DOM tree of the elements that make up the user interface of your application. You define the behavior of these elements in the Template explorer.

>**Note:** If you are familiar with MontageJS development, the DOM explorer is where you expose the DOM elements of an HTML document. Dragging items from the Library to the DOM explorer and arranging them is the equivalent of adding semantic markup to an HTML document. Each element in the DOM explorer has a corresponding object in the Template explorer. The Template explorer is where you define the behavior of an HTML document's elements or markup; the objects listed in the Template explorer correspond to the objects in the document's serialized object graph.

## Template Explorer

The Template explorer is populated by the objects used in the component's HTML document (or template in MontageJS speak). This is where you define data bindings and event listeners. 

The more complex the user interface component you are working on, the longer the list of objects that populate this area. You can use the Search box at the top to quickly locate objects, or click the Bindings and Listeners icons to the left of the Search box to hide binding and listener details and thus simplify the scrollable view.

## Property Inspector

The Properties inspector (by default hidden from view) enables you to view and modify the properties of objects. It automatically slides into view and appears to the left of the Library when objects are added to or selected in the Template explorer.

## Stage

The Stage provides a context-free presentation of the current component's content. Don't look here for a preview of “coming attractions”; what you currently get is closer to a wireframe than a prototype.
