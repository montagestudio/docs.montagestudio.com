---

layout: montage-studio
title: Montage Studio Quick Start - Montage Studio Documentation

this-page: tutorial-simple-to-do

---

# Quick Start: Build a Simple To-Do Application

This tutorial will show you how to assemble a simple to-do application in Montage Studio using the MontageJS framework. It should take you no more than ten minutes to complete this tutorial.

## Requirements

This tutorial assumes that you have read the <a href="ide-at-a-glance.html" target="_blank">overview</a> section of the Montage Studio documentation to familiarize yourself with the Montage Studio user interface.

## The Final Application

Your goal is to assemble a simple application that enables users to create a list of things to do, mark tasks as completed, and keep track of the number of tasks that remain to be done. The application has five elements: a title, a button to add new tasks, text fields to enter tasks, check boxes to mark tasks as completed, and a counter (or badge) that keeps track of the remaining tasks in the list.

<figure>
    <img src="/images/montage-studio/tutorials/simple-to-do/fig01.png" alt="The final to-do application for this tutorial" style="width: 400px;">
    <figcaption><strong>Figure 1.</strong> Your task: To assemble a simple to-do application.</figcaption>
</figure>

Conceptually, the application breaks down into a list view (with a task item child view) and a controller for managing the underlying content. 

## Getting Started

To get started, go to <a href="https://work.montagestudio.com" target="_blank">work.montagestudio.com</a> and create a new project (for example, **my-to-do**), if you haven't done so already. After Montage Studio has initialized the project and installed the dependencies, select main.reel in the ui folder of your project; this opens the Main user interface component in the component editor.

## MontageJS Basics

MontageJS is an open source client-side framework, used within Montage Studio to build rich, single-page appllications. Building MontageJS applications is divided into a development (creating the application) phase and a production (optimizing the application) phase. In development, you assemble an application out of encapsulated components. These components are stored in the ui directory of your project and identified by a .reel suffix.

<figure>
    <img src="/images/montage-studio/tutorials/simple-to-do/fig02.jpg" alt="The components that make up the final application" style="width: 225px;">
    <figcaption><strong>Figure 2.</strong> The components that make up the final application.</figcaption>
</figure>

When you assemble a MontageJS application, you modify the HTML documents (AKA templates in MontageJS speak) of the components in the ui directory. To change the appearance of components, you edit the components' CSS files.

The to-do application that you are about to build consists of two components: main.reel and task.reel (which you will create shortly). Main.reel is the main user interface component of the application; think of it as the MontageJS equivalent of a website's index page or the principal screen of your single-page application: it can contain any number of subcomponents for the presentation and behavior of an application. Task.reel encapsulates the task item child view of the application's list view and is included in the Main component.

## Assembling the Application

>**Note:** To keep steps short, the following applies: When instructed to add a Foo controller to the _template explorer_, grab it from the Montage group in the library library of configurable objects. When instructed to add a Foo node to the _DOM explorer_, drag Foo from the Digit group to the DOM explorer.

### Add the Title

To add the title to the template:

1. Add a Title node as a child element of the owner node.

    <figure>
        <img src="/images/montage-studio/tutorials/simple-to-do/fig03.jpg" alt="Adding a Title node" style="width: 250px;">
        <figcaption><strong>Figure 3.</strong> Add a Title node.</figcaption>
    </figure>

    This also adds an instance of the Title component to the template explorer and opens the context-sensitive properties inspector (to the left of the library).

2. In the properties inspector, in the Value text field, replace Title with Things To Do.

    <figure>
        <img src="/images/montage-studio/tutorials/simple-to-do/fig04.jpg" alt="Adding a Title value" style="width: 550px;">
        <figcaption><strong>Figure 4.</strong> Add a Title node to the DOM explorer and then change its default text value.</figcaption>
    </figure>
    
    Next, to present the task items of the application, you need a list view.

### Add a List View and Controller

To add a list view:

1. Add a List node as a sibling of the Title (h1) node.

    <figure>
        <img src="/images/montage-studio/tutorials/simple-to-do/fig05.jpg" alt="Adding a List node" style="width: 250px;">
        <figcaption><strong>Figure 5.</strong> Add a List node to the DOM explorer.</figcaption>
    </figure>

    >**Note:** If you accidentally insert the List node as a child element, simply drag the List node up and to the left until the left end of the blue insertion marker aligns with the left side of the h1 node.

    The underlying content (or model) of the list is managed by a RangeController.

2. From the Montage group, drag a RangeController to the template explorer.

    Next, you need to tell the List component to receive its content from the instance of the RangeController you just added.

3. Select the List component in the template explorer to reveal its properties, then drag the RangeController proxy icon to the List contentController field in the properties inspector. (To set the value, you can also type **@rangeController** in the field.)

    <figure>
        <img src="/images/montage-studio/tutorials/simple-to-do/fig06.jpg" alt="Setting the List object to receive content" style="width: 550px;">
        <figcaption><strong>Figure 6.</strong> Set the List to receive its content from the RangeController.</figcaption>
    </figure>

### Add the Task Button

To add a task button:

1. Add a Button node as a sibling between the Title (h1) and List (ul) nodes.

    <figure>
        <img src="/images/montage-studio/tutorials/simple-to-do/fig07.jpg" alt="Adding a Button node" style="width: 250px;">
        <figcaption><strong>Figure 7.</strong> Add a Button node as a sibling of the Title (h1) and List (ul) nodes.</figcaption>
    </figure>

2. In the properties inspector, replace the default label (Button) with **New Task**.

    Next, you need to wire up the button so it does what it's supposed to do when clicked: add inputs to the list. To do this you need to set the RangeController to observe the new task button for “action.” This can be accomplished through a simple drag-and-drop operation.

    <figure>
        <img src="/images/montage-studio/tutorials/simple-to-do/diagram01.png" alt="Wiring up a button" style="width: 451px;">
    </figure>

3. On the Button card, drag the Add Listener (+) button to the RangeController card.

    This opens the Button's Listener dialog box, with the event type (action) and listener (rangeController) conveniently filled in. (Alternatively, you can also click Add Listener [+] and then drag the RangeController proxy icon to the Listener field in the dialog box.)

    <figure>
        <img src="/images/montage-studio/tutorials/simple-to-do/fig08.jpg" alt="Wiring up the button" style="width: 550px;">
        <figcaption><strong>Figure 8.</strong> Drag the Add Listener (+) button to the RangeController to wire up the button.</figcaption>
    </figure>
    
4. Enter **addContent** in the optional Method Name field and click Define Listener. (When you specify a method name, MontageJS injects an actionEventListener with the target action configured for you.)

5. Save your changes (press Cmd+S or select Project > Save All from the menu bar). 

6. To take a peek at what you've build so far, click the Run button at the top of the project explorer.

    <figure>
        <img src="/images/montage-studio/tutorials/simple-to-do/fig09.jpg" alt="Click Run to preview" style="width: 250px;">
        <figcaption><strong>Figure 9.</strong> Click the Run button to preview your application.</figcaption>
    </figure>

    Montage Studio will serve your application in a new tab in the browser. If you followed the instructions, you should see the title of the application and the New Task button. At this point, you can add any number of item placeholders to the list view by clicking New Task.
    
    <figure>
        <img src="/images/montage-studio/tutorials/simple-to-do/fig10.png" alt="Application preview" style="width: 225px;">
        <figcaption><strong>Figure 10.</strong> The view and model are in place.</figcaption>
    </figure>

Next, add a component that presents the individual tasks (task item child view). Technically, this can be accomplished by using the prebuilt ListItem component from the Digit group. For this exercise, however, you will create a new component that encapsulates the presentation of a task from scratch.


### Create a Task Component

To add a new component:

1. RIght-click the ui folder in the project explorer and select New Component.

2. In the Create Component text box, replace "my-component" with **task**, and then click Create.

    Montage Studio adds the new component to the UI folder of your project and opens its template in a new tab in the component editor. (Note also that the Task component has been added to the project group at the top of the library.)
    
3. Add a Checkbox node as a child element of the owner node.

    To ensure the component works as intended, you need to bind it to a task's completed state. This is controlled by the owner of the current document.

    <figure>
        <img src="/images/montage-studio/tutorials/simple-to-do/diagram02.png" alt="Binding a task to a completed state" style="width: 451px;">
    </figure>

4. In the template explorer, click Add Binding (+) on the Checkbox card.

5. In the Target Path field enter **checked**, in the Source Path field enter **@owner.task.completed**, and then click the two-way direction button—you want changes on either side to affect the other.

    >**Note**: This version of Montage Studio includes a rudimentary autocomplete feature: selecting a suggested value and pressing Tab advances the cursor to the next input field; pressing Return accepts the current selection and keeps the current field in focus.

    <figure>
        <img src="/images/montage-studio/tutorials/simple-to-do/fig11.jpg" alt="Application preview" style="width: 451px;">
        <figcaption><strong>Figure 11.</strong> Establish a two-way binding between the target and its source.</figcaption>
    </figure>

6. Click Define Binding.
    
    Next, you want to add a text field adjacent to the check box.

7. Add a TextField node as a sibling of the Checkbox node.

8. In the template explorer, click Add Bindings (+) in the textField card.

9. In the Target Path field, enter **value**, click the two-way direction button, and in the Source Path field enter **@owner.task.title**.

    <figure>
        <img src="/images/montage-studio/tutorials/simple-to-do/diagram03.png" alt="Defining bindings" style="width: 451px;">
    </figure>
    
10. Click Define Binding and save your changes.

    <figure>
        <img src="/images/montage-studio/tutorials/simple-to-do/fig12.jpg" alt="The completed Task component" style="width: 550px;">
        <figcaption><strong>Figure 12.</strong> The completed Task component in the component editor.</figcaption>
    </figure>

### Add the Task Component to the List

Next, you need to add the new Task component as a child to the List node in the Main component.

1. Click the main.reel tab.

    You want to replace the placeholder li node with the task list item you just created.
    
2. Drag the Task component from the project group in the library on the li node in the DOM explorer.

    <figure>
        <img src="/images/montage-studio/tutorials/simple-to-do/fig13.jpg" alt="Adding the Task component" style="width: 400px;">
        <figcaption><strong>Figure 13.</strong> Drag the Task component on the li node (left) to replace the placeholder li node with the new task list node (right).</figcaption>
    </figure>

    >**Note**: You can also drag the task component to the template explorer and then drag the Task's proxy icon to the li node.

    This adds a task1 card to the template explorer as a child of the list card.
       
    Next, you need to set up a binding so that the children of your task list can be found. You know the binding drill by now…

3. Click Add Binding (+) in the task1 card.

4. In the Bindings dialog box, enter **task** in the Target Path field; keep the one-way direction default setting. 

    You want to bind the task object to the list object, so enter **@list:iteration.object** in the Source Path field.

5. Click Define Binding and save your changes. 
    
Click Run again to preview your changes and you will see the same title and New Task button as before; but now you can add any number of inputs by clicking New Task.

<figure>
    <img src="/images/montage-studio/tutorials/simple-to-do/fig14.png" alt="The New Task button" style="width: 225px;">
    <figcaption><strong>Figure 14.</strong> Click New Task to add undefined list items.</figcaption>
    </figure>

You're almost done. The only element still missing is a badge to keep track of the remaining tasks.

### Add a Task Badge

To add and wire up a task badge follow these steps:

1. Add a Badge widget as a sibling between the button and ul nodes in the DOM explorer.

    <figure>
        <img src="/images/montage-studio/tutorials/simple-to-do/fig15.jpg" alt="Adding a badge element" style="width: 250px;">
        <figcaption><strong>Figure 15.</strong> Add a badge between the button and ul nodes.</figcaption>
    </figure>
    
2. In the template explorer, click Add Bindings (+) on the badge card.

3. In the Target Path field, enter **value**; keep the one-way direction setting; and in the Source Path field enter **@rangeController.organizedContent.filter{!completed}.length**.

    This captures all tasks that have not been marked as completed (checked).

4. Click Define Binding and save your changes.

Click Run again and take the application for a spin: Click New Task to add any number of inputs, fill in the blank text fields with things to do, select a check box to mark a task as completed, and watch the badge count down on the number of remaining tasks.

## Add Some Style

As should be clear by now, Montage Studio does not provide a visual approach to building graphical user interfaces. Instead of laying out views, you assemble user interface components that represent distinct functional areas of an application. To change the look and feel of the application, you have two options: depending on what you want to accomplish, you can apply global styles or you can use styles on the component level. For example, to center the application horizontally, you would modify the global style sheet:

1. In the project epxlorer, expand the assets and style folders and select style.css:

2. Add the following statements to the style sheet:

    ```
    .Main {
        padding: 1em;
        text-align: center;
    }
    
    .Task {
        padding: .5em;
        text-align: center;
    }
    ```

To have a task item appear dimmed when completed, you need to create a binding on the task.reel owner and modify the component's CSS file.

1. Switch to the task.reel tab.

2. In the template explorer, click the owner's Add Binding (+) button.

3. For the Target Path enter **classList.has('completed')**, keep the one-way direction, and in the Source Path field enter **task.completed**.

4. Click Define Binding and save your changes.

    Next, you will edit the component's CSS file.
    
5. In the project explorer, expand the task.reel directory, select task.css, and enter the following: **.Task.completed {opacity: 0.2;}**.

6. Save your changes and click Run.

    At this point, any item you cross off your list will appear dimmed.

Feel free to experiment further, adding classes to a component's template and CSS statements to its CSS file, for example, or try to add a button that removes completed tasks from the list.

There's one more thing you need to do when you've finished your application: prepare it for deployment.

## Prepare for Deployment

As mentioned above, building MontageJS applications is divided into a development phase and a production phase. When your application is finished, you need to get it ready for deployment. In Montage Studio, you have two options; you can:

* Publish a build of your application to GitHub (Project > Build > Publish to Github Pages). This has the benefit that your application will be hosted by GitHub (although it can take a bit for GitHub to finish publishing the pages).
* Download a production-ready build of your application to your system (Project > Build > Download). You can then copy the downloaded application folder to a web server of your choice for deployment. The index.html file included in this folder is the entry point to your application: double-click the file to open the application in your default browser.

##Summary

Montage Studio makes it a breeze to assemble the moving parts of a MontageJS application. Instead of writing a lot of code, you can work in a drag and drop environment to quickly:

* Define a component tree of user interface elements in the DOM explorer.
* Declare the behavior of the markup in the template explorer.
* Modify the properties of selected objects in the Property inspector.

And because MontageJS uses logic-less, component-oriented templates, designers can focus on HTML and CSS, while developers implement the behavior and business logic. That's separation of concerns at its most elegant.

## Next Steps

To learn more about Montage Builder and MontageJS, refer to the following resources

* [Montage Studio documentation](/montage-studio/).
* [MontageJS documentation](/montagejs/).

For feedback and support, go to our [Forum](http://forum.montagestudio.com/).

