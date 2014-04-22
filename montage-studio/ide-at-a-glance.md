---

layout: montage-studio
title: Montage Studio At a Glance - Montage Studio Documentation

this-page: ide-at-a-glance
next-page: overview-using-montage-studio

---

# Montage Studio At a Glance

<a href="http://work.montagestudio.com" target="_blank">Montage Studio</a> is a new development environment that uses the open source <a href="http://montagejs.org" target="_blank">MontageJS framework</a> to help you build complex and responsive single-page applications in the cloud. It is designed to bring drag-and-drop ease to assembling MontageJS applications and help manage your development workflow, from creating and managing a project to previewing, testing, and preparing an application for production.

>**Note**: Montage Studio is beta software. Our team of engineers is updating the code base on a daily basis, so some screenshots may not accurately reflect what is in the current build.

## Leverage the Power of the MontageJS Framework

MontageJS is an open source client-side framework for building scalable, easy-to-maintain web applications. It was built from the ground up to help solve common challenges of building complex applications and features a flexible component model that promotes code reuse, a managed draw cycle that helps minimize browser reflow, reactive data binding to keep rich UIs in sync with data models, and implicit event delegation to help improve performance. Although you can build MontageJS applications using the command line and a text editor, Montage Studio simplifies the process by automating the set-up and build processes, reducing the amount of code you have to write, and providing a drag-and-drop evironment for assembling user interface components. Incidentally, Montage Studio is built using MontageJS.

## Work in a Streamlined, Integrated Environment

The Montage Studio development environment integrates component and code editing, asset management, and dependency management. The workspace is divided into three main areas: menu bar, project explorer, and editor area.

<figure>
    <img src="/images/montage-studio/ide-at-a-glance/fig01.png" alt="Single-window envrionment" style="width: 550px;">
    <figcaption>Montage Studio</figcaption>
</figure>

* The menu bar at the top provides quick access to common menus and commands.
* The project explorer on the left provides access to the files and directories of your project.
* The editor area reconfigures its content depending upon the currently selected resource type; for example, when you select a component (or .reel directory such as main.reel) in the project explorer, Montage Studio opens it in the component editor; select a component's HTML, CSS, or JavaScript file, and Montage Studio opens the file in the built-in text editor; select package.json, and Montage Studio opens the file in the package manager.

### Component Editor

The component editor enables you to assemble components and describe their relationships in a drag and drop environment. The assembled components usually represent the functional areas of an application and are stored in your project's ui directory.

<figure>
    <img src="/images/montage-studio/ide-at-a-glance/fig01a.jpg" alt="Component editor" style="width: 550px;">
    <figcaption>Component editor</figcaption>
</figure>

### Text Editor

The built-in text editor complements your development workflow by letting you modify a component's HTML, CSS, or JavaScript files without leaving the Montage Studio environment. You can add your own code, write custom components, refactor existing components, define the appearance of your application, or simply edit your application's readme file. 

<figure>
    <img src="/images/montage-studio/ide-at-a-glance/fig01b.jpg" alt="Text editor" style="width: 550px;">
    <figcaption>Text editor</figcaption>
</figure>

### Flow Editor

The flow editor is a special editing environment that enables you to create a flow pattern that moves specified content along a Bézier path (see, for example, the film strip feature in the Popcorn sample application). You can access the flow editor through the properties of the Flow component from within the component editor.

<figure>
    <img src="/images/montage-studio/ide-at-a-glance/fig01c.jpg" alt="Flow editor" style="width: 550px;">
    <figcaption>Flow editor</figcaption>
</figure>

### Scene View Editor

With Montage Studio you can integrate WebGL content into complex applications, and the scene view editor makes manipulating the individual elements of a 3D scene just as easy as manipulating conventional HTML elements in the DOM. Similar to the flow editor, it is acccessible only from within the component editor, through the SceneView component.

<figure>
    <img src="/images/montage-studio/ide-at-a-glance/fig01d.jpg" alt="Scene view editor" style="width: 550px;">
    <figcaption>Scene view editor</figcaption>
</figure>

### Package Manager

The package manager provides a visual environment in which to edit the meta data in your project's package.json file. It also makes it easy to update a project's existing dependencies or add packages from the npm repository. 

<figure>
    <img src="/images/montage-studio/ide-at-a-glance/fig01e.jpg" alt="Dependency editor" style="width: 550px;">
    <figcaption>Package manager</figcaption>
</figure>

## Preview, Share, and Edit Your Work in Live View

Live view mode gives you an interactive preview of your application in development. Live view mode runs your application in a separate browser window and updates in real-time when you continue to work on the application. The live view URL can be opened in another browser or even on another computer or device, which is great for cross-browser testing and for sharing your work with your team or clients.

<figure>
    <img src="/images/montage-studio/ide-at-a-glance/fig01f.jpg" alt="Live view mode" style="width: 550px;">
    <figcaption>Live view</figcaption>
</figure>

## Use Git Source Control and Collaboration Features

Montage Studio supports the Git source control system. After you log in to<a href="http://work.montagestudio.com" target="_blank">Montage Studio</a> with your Github account, you see the Montage Studio welcome page, which displays a list of your current repositories; when you create a new project,  Montage Studio automatically sets up a new repository on GitHub and clones it as a workspace container that is dedicated to that particular project. While you work, your saved changes are written to workspace and then pushed to that project's GitHub repository, to a shadow branch that can be merged at any time. 

# Next Steps

To get started with Montage Studio refer to the following resources:

* For an overview of the development environment and features: [Using Montage Studio](overview-using-montage-studio.html)
* To learn how to build a simple application: [Quick Start tutorial](tutorial-simple-to-do.html)
* Questions? Check out the [FAQ](faq.html)
