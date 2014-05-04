---

layout: montage-studio
title: Using Montage Studio - Montage Studio Documentation

prev-page: ide-at-a-glance
this-page: overview-using-montage-studio

---

# Using Montage Studio

>**Note:** We are in the process of finalizing this document based on the latest version of the Montage Studio beta. Sorry about the inconvenience.

Montage Studio makes it easier for you to assemble complex and powerful single-page web applications using the MontageJS framework. This guide introduces you to the key features of Montage Studio. For a hands-on introduction to using Montage Studio, see the [Quick Start](tutorial-simple-to-do.html) tutorial, which shows you how to assemble a simple to-do application.
      
# Develop Applications

Montage Studio integrates user interface assembly, code editing, asset management, and dependency management within a single workspace window. This window is your primary interface for developing and managing your project.

## Work in the Browser

The workspace window is divided into three areas&#8212;the menu bar at the top, the project explorer on the left, and an editor area.

<figure>
    <img src="/images/montage-studio/ide-overview/fig01.png" alt="Single-window envrionment" style="width: 550px;">
    <figcaption>Montage Studio</figcaption>
</figure>

* The menu bar provides quick access to common menus and commands.
* The project explorer provides access to the files and folders that make up your project.
* The editor area reconfigures its content depending on the context (e.g., editing a component, a source file, or the package.json file, which holds various metadata relevant to the project).

## Edit Components, Code, and More

When you develop applications in Montage Studio, you use the component editor, text editor, and package manager. Editors are associated with resource types; as you select resources in the project explorer, the resource is opened in the appropriate editor, in a tab, in the editor area. For example, when you select a user interface component (.reel directory) in the project explorer, Montage Studio opens it in the component editor; select a component's HTML, CSS, or JavaScript file, and Montage Studio opens the file in the built-in text editor; select package.json, and Montage Studio opens the file in the package manager.

When building an application in Montage Studio, you will use the following editors:

* **Component editor:** To quickly assemble user interface components and describe their relationships.
* **Text editor:** To add your own code to a component's source files or edit your application's readme file.
* **Package manager:** To update the metadata that identifies your project and specifies your project's dependencies.

You can also use the following custom editing environments: 

* **Flow editor:**  To create flow patterns that move specified content along a Bézier path. The flow editor is accessible only from within the component editor, and only if you use a Flow component in your project.

* **Scene view editor (under development):** To manipulate a 3D scene. Like the flow editor, it is acccessible only from within the component editor, when your application uses the Scene View component.

To start using Montage Studio, you must be logged in to your GitHub user account. To start a new project, click New on the Montage Studio welcome page.

<!-- figure>
    <img src="/images/montage-studio/ide-overview/fig02.jpg" alt="Montage Studio welcome page" style="width: 550px;">
    <figcaption>Montage Studio welcome page</figcaption>
</figure -->
          
# Maintain Your Project

When you create a project, Montage Studio initializes a Git source code repository with your new project, installs the essential files and dependencies that are required in development, and then exposes these resources in the project explorer. 

## Understand the Project Structure

A _project_ is the source for your application; it comprises a collection of files and directories needed to assemble, preview, and test your application and includes:

* **assets**, a folder for organizing global style sheets, images, and other assets.
* **node_modules**, a directory that contains the dependencies to which the project is linked as you build your application.
* **test** and **run-tests.html**, for creating and running Jasmine-based unit tests that exercise features of your application. (The dependencies required to run unit tests are included in the node_modules directory.)
* **ui**, a directory that contains the user interface components of your application.
* **index.html**, the entry-point document for your application, which instantiates the Main user interface component and all its child components (in short: your application), when loaded in the browser.
* **package.json**, which holds meta data that describes the application and the dependencies included in the node_modules directory.
* **readme.md**, which summarizes the structure of the project and provides some hints on unit testing your application. (This readme file will be included in the production-ready build of your final application, so be sure to replace its contents with information about your application before deploying it or passing it on to a client.)

<figure>
    <img src="/images/montage-studio/ide-overview/fig03.jpg" alt="Project explorer" style="width: 175px;">
    <figcaption>The project explorer</figcaption>
</figure>

When working in Montage Studio, your focus will be on the contents of the ui directory, which is the default directory for the user interface components that make up your application.

You can expand the default project directory as necessary; for example, depending on the application, you may want to add the following folders to keep your project organized:

* _locale_, for localized content.
* _scripts_, for JS libraries that have to be loaded using a `<script>` tag.

To add folders, right-click in the project explorer and select New Folder.

## Manage Project Dependencies and Details

When you create a new project, Montage Studio adds the following dependencies to the nodes_modules directory:

* **montage**, the MontageJS framework.
* **digit**, a mobile-optimized user interface widget set.
* **montage-testing**, which is required for unit testing. 

Montage and digit provide most, if not all, of the components and functionality you need to assemble complex single-page web applications. If necessary, you can add dependencies and prebuilt components from the npm repository, or include custom libraries that you can place, for example, in the assets folder of your project (or a scripts folder).

To add dependencies, or update the existing dependencies and project information, you need to edit the package.json file. This file contains the metadata that identifies your project and is used to handle your project's dependencies. When you select it in the project explorer, Montage Studio opens the file in the package manager. Using the package manager, you can:

* Provide details on your application such as name, version number, license and author information, and a brief description.
* Add packages from the npm repository.
* Review details on the installed packages and update them to the latest version.
* Search the npm repository for ready-to-use components or dependencies you may want to add to your project.

<figure>
    <img src="/images/montage-studio/ide-overview/fig04.jpg" alt="Package manager" style="width: 550px;">
    <figcaption>The package manager</figcaption>
</figure>

When adding dependencies, you have two options: 

* To add a particular package, click the Package Dependencies + button, enter the required name and version or Git URL, and then click Add.
* To find a module by name, use the Search Packages box to find the module you want, and then click Install to add it to your dependencies.

To update an existing dependency, select it in the Package Dependencies group to expose its metadata under Dependency Information, and then click Update on the Actions card.

## Close or Reopen a Project

Before closing a project, be sure to save your changes; Montage Studio currently does not save changes automatically.

Montage Studio gives you two options to leave a project: close it or log out. 

* To close a project, select Project > Close Project from the menu bar or click the Montage Studio icon in the upper left on the menu bar. This returns you to the project page, where you can start a new project or select an existing one. 
* To exit Montage Studio, choose _Your Name_  > Log Out on the right of the menu bar from wihtin a project or click Log Out on the Welcome page. This returns you to the Montage Studio sign-in page.
    
# Assemble a User Interface

Montage Studio does not provide a visual approach to building graphical user interfaces. Instead of laying out views (for example, by dropping prebuilt user interface elements on a "canvas"), you assemble user interface components that represent distinct functional areas of an application such as navigation, data display, data entry, and so on. These components are stored in the ui directory of your project and identified with a .reel extension. 

A user interface component consists of three files that control the component's structure (HTML), appearance (CSS), and behavior (JavaScript). When you craft your application in Montage Studio, you modify the HTML documents or templates (in MontageJS speak) of the components in the UI directory of your project. More specifically, you assemble a component tree of user interface elements in the DOM explorer, and then declare how you want these DOM elements to behave by specifying UI-related information (such as properties or bindings) using the objets in the template explorer.

<figure>
    <img src="/images/montage-studio/ide-overview/fig05.jpg" alt="Component editor" style="width: 550px;">
    <figcaption>The component editor</figcaption>
</figure>

## Add Items from the Library

The component editor has three main areas: the library (on the right), the DOM explorer (in the middle), and the template explorer (on the left). The library lists the dependencies that you can use in the current project. The DOM explorer and the template explorer are where you drag the dependencies' configruable objects you want to use.

The library is divided into three groups:

* The group at the top (named after the current project) lists the components in the ui directory of your project (for example, main.reel).
* The montage group provides the controllers that are part of the MontageJS framework.
* The digit groups exposes the touch-optimized components of the Digit widget set.

<figure>
    <img src="/images/montage-studio/ide-overview/fig06.jpg" alt="The library" style="width: 175px;">
    <figcaption>The library (icon view)</figcaption>
</figure>

You can minimize the groups by clicking the triangle icon in the top left of a group's title bar and switch between list and icon views using the list/icon button to the right of the Search box.


## Style the Application

Coming soon.


## Find Files Quickly

Montage Studio supports fuzzy search: Press Cmd+E or use the Go To menu to locate a file or asset whose filename contains a specified string of letters. From the search results list, select the file you want to open.

## Look Up Documentation for a Library Item

Montage Studio Help is still under development. For complete reference information about prebuilt components, refer to the API reference of the MontageJS framework and the Digit ui set in the docs:

* <a href="http://docs.montagestudio.com/api/AbstractButton.html" target="_blank">MontageJS API</a>
* <a href="http://docs.montagestudio.com/montagejs/theme-digit-components.html" target="_blank">Digit API</a>

# Use Images and Animations

Coming soon

## Add Icons, Images, and Flow-like Animations

Coming soon

## Manipulate 3D Scenes

Coming soon

For a short video that demonstrates how you can use Montage Studio for work with 3D content, check out <a href="http://www.youtube.com/watch?v=Jfem-Q9Kouc&feature=youtu.be" target="_blank">this video</a>.

# Write code

Montage Studio has a bare bones text editor, which supports syntax coloring, undo and redo, and (partial) code completion. Error highlighting, find and replace, code folding, and other advanced text editing features are under development. If you depend on these features for writing your code, you can drag a component's individual HTML, CSS, or JavaScript file to your preferred text editor; when finished editing, drag the edited file back to the respective component (.reel directory).

The built-in text editor complements your development workflow by letting you add your own code, write custom components, refactor existing components, or define the appearance of your application _after_ you assemble the views and model of your MontageJS application using the component editor.

<figure>
    <img src="/images/montage-studio/ide-overview/fig12.jpg" alt="The text editor" style="width: 550px;">
    <figcaption>The text editor</figcaption>
</figure>

To use code completion, press Ctrl+spacebar; the text editor provides a popup list of available names, functions, and more to choose from. Select an item in the list and press Return to insert the selection at the current cursor position. To close an open statement or tag, press Ctrl+spacebar.

# Save and Revert Changes

Presently, Montage Studio does not save changes to source and project files automatically, so be sure to save (Project > Save All) regularly as you assemble your application and before you log out of Montage Studio.

Every time you choose Project > Save All, Montage Studio commits the changes you made since your last save to the `_mb_master` branch of your project's GitHub repository. The Git status counter on the menu bar tracks how far ahead of the master branch your project is. Every time you save your project, Montage Studio commits your changes, and each commit increments the number by 1.

<figure>
    <img src="/images/montage-studio/ide-overview/fig13.jpg" alt="The Git status counter" style="width: 225px;">
    <figcaption>The Git status counter</figcaption>
</figure>

You can revert a change using the Undo, Redo, and Delete commands in the Edit menu. Use Undo to reverse the most recent changes in the editor, or Redo to keep the change you just undid. Use Delete to remove the currently selected item (for example, template card or node) from the component editor.

# Preview and Share

At any point in development, you can check your progress by clicking the Run button at the top of the project explorer. This opens the application in live view mode in a new browser window.

<figure>
    <img src="/images/montage-studio/ide-overview/fig14.jpg" alt="The Run button" style="width: 175px;">
    <figcaption>The Run button</figcaption>
</figure>

When in live view mode, you cannot only view but also interact with a build of your application in development. As you modify your application in Montage Studio, the live view rendering of the application updates in real time: every character you type, every component you modify, every element you replace is rendered instantly after saving the change, without manual reload, for all open live view windows. The live view URL can be opened in a different browser, computer, or device. This is particularly useful for cross-browser and cross-device testing as well as for soliciting feedback from peers, team members, or clients, who can see and interact with what you've been working on&#8212;no need to install additional software or go through any complicated setup.

>**Note:** Live view presently only works in conjunction with the component and flow editors. Changes you make to your templates or style sheets in the text editor, for example, are not picked up in real time.

With live view mode, you can:

* Try out different designs, features, or behaviors before committing to a change.
* Show different states of the same application in multiple windows to test how a change might affect each view.
* Share your progress or an idea with clients and peers in real time to discuss or review.

To run the application in another browser (locally or on another computer or device), open the live view URL in that browser. Live view applications are served over an http (or https) connection. Opening a live view URL in a browser other than the one you develop in triggers the Montage Studio server to serve a page with an Enter Access Code text box and to generate an access code. The access code appears in the info bar (below the menu bar) in Montage Studio. To proceed with live view, enter the access code and press Return. Likewise, when sharing your live view URL with others, you also need to give them the Montage Studio&#8211;generated access code so they can experience your application.

<!-- figure>
    <img src="/images/montage-studio/ide-overview/fig15.jpg" alt="Access code for sharing" style="width: 225px;">
    <figcaption>Access code example for sharing the application in development</figcaption>
</figure -->

# Prepare for Deployment

Building MontageJS applications is divided into a development phase and a production phase. When your application is finished, you need to get it ready for deployment. In Montage Studio, you have two options; you can:

* Publish a build of your application to GitHub (Project > Mop > Publish to Github Pages). This has the benefit that your application will be hosted by GitHub (although it can take a bit for GitHub to finish publishing the pages).

* Download a production-ready build of your application to your system (Project > Mop > Download). You can then copy the downloaded application folder to a web server of your choice for deployment. The index.html file included in this folder is the entry point to your application: double-click the file to open the application in your default browser.
