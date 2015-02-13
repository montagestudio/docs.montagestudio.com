---

layout: montage-studio
title: Package Explorer - Montage Studio Documentation

prev-page: ide-menu-bar
this-page: ide-package-explorer
next-page: ide-component-editor

---

# Package Explorer

The Package explorer provides access to the files and folders of your project.

<figure>
    <img src="{{site.baseurl}}/images/montage-studio/ide-overview/fig03.jpg" alt="The Package explorer" style="width: 225px;">
    <figcaption>The Package explorer</figcaption>
</figure>

Clicking the triangle next to a folder expands the folder; clicking the folder icon shows the folder in the Finder; clicking a file icon opens the file in its default application.

When assembling a MontageJS application, your focus will be on the contents of the ui folder, which is the default directory for user interface components. User interface components are identified with a .reel suffix. When you select a component, Montage Studio opens it in the Component editor. The Component editor supports browser-style tabs, so you can open and work on multiple components at the same time.

The following table describes the default files and folders installed with every new project.

Folder / File | Description
------------ | -------------
assets | Contains global styles and images for your application.
index.html | Is the entry-point document for the application.
node_modules | Contains the code dependencies required in development: Montage, the core framework, and Digit, a mobile-optimized user interface widget set.
package.json | Describes the application and the dependencies included in the node_modules directory.
README.md | Is the default readme file; be sure to replace its contents with a description of your application.
run-tests.html | Is a page to run Jasmine tests manually in the browser.
test | Contains tests for the application. By default, this directory includes all.js, a module that points the test runner to all jasmine specs.
ui | Contains the application user interface components. By default, this directory contains one component: main.reel (the Main user interface component).

(For additional information, see the readme.md file of your project)
