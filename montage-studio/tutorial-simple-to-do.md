---

layout: montage-studio
title: Montage Studio Quick Start - Montage Studio Documentation

this-page: tutorial-simple-to-do

---

# Quick Start: Build a Simple To-Do Application

This tutorial will show you how to build a simple to-do application in Montage Studio. The objective is to familiarize you with the power and potential of Montage Studio for creating rich HTML5 applications that use the MontageJS framework. It should take you no more than ten minutes to complete this tutorial.

## Requirements

This tutorial assumes that you have read the <a href="ide-at-a-glance.html" target="_blank">overview</a> section of the Montage Studio documentation to familiarize yourself with the Montage Studio user interface.

## The Final Application

Your goal is to assemble a simple application that enables users to create a list of things to do, mark tasks as completed, and keep track of the number of tasks that remain to be done. The application has five elements: a title, a button to add new tasks, text fields to enter tasks, check boxes to mark tasks as completed, and a counter (or badge) that keeps track of the remaining tasks in the list.

<figure>
    <img src="/images/montage-studio/tutorials/simple-to-do/fig01.png" alt="The final to-do application for this tutorial" style="width: 400px;">
    <figcaption><strong>Figure 1.</strong> Your task: To assemble a simple to-do application.</figcaption>
</figure>

Looking at it through the eyes of a MontageJS developer, the application breaks down into a list view (with a task item child view) and a controller for managing the underlying content, split across two user interface components: Main and Task (which will become clear shortly as you assemble the application).

## Getting Started

To get started, go to <a href="https://work.montagestudio.com" target="_blank">work.montagestudio.com</a> and create and initialize a new project (for example, **my-to-do**), if you haven't done so already. After Montage Studio has initialized the project and installed the dependencies, select main.reel in the ui folder of your project; this opens the Main user interface component in the Component editor.

## Assembling the Application

>**Note:** To keep steps short, when instructed to add a Foo node to the DOM explorer, drag Foo from the Digit group in the Library to the DOM explorer. When instructed to add a Foo controller to the Template explorer, grab it from the Montage group in the Library.

### Add the Title

To add the title to the template:

1. Add a Title node as a child element of the owner node.

    <figure>
        <img src="/images/montage-studio/tutorials/simple-to-do/fig02.png" alt="Adding a Title node" style="width: 225px;">
        <figcaption><strong>Figure 2.</strong> Hover over the owner node while dragging to reveal the child element drop area.</figcaption>
    </figure>

    Adding the Title node also adds an instance of the Title component to the Template explorer and opens the context-sensitive Properties inspector to the left of the Library.

2. In the Properties inspector, in the Value text field, replace Title with Things To Do.

    <figure>
        <img src="/images/montage-studio/tutorials/simple-to-do/fig03.png" alt="Adding a Title value" style="width: 550px;">
        <figcaption><strong>Figure 3.</strong> Add a Title node to the DOM explorer and change its default text value.</figcaption>
    </figure>
    
    Next, to present the task items of the application, you need a List view.

### Add a List View and Controller

To add a List view:

1. Add a List node as a sibling (or next element) of the Title (h1) node. (Remember to hover over an existing node to reveal the available drop areas.)

    <figure>
        <img src="/images/montage-studio/tutorials/simple-to-do/fig04.jpg" alt="Adding a List node" style="width: 225px;">
        <figcaption><strong>Figure 4.</strong> Add a List node to the DOM explorer.</figcaption>
    </figure>

    >**Note:** If you accidentally add the List node as a child element, simply drag the List node and hover over a parent node to reveal the next and previous element drop areas again.

    The underlying content (or model) of the list is managed by a RangeController.

2. Drag a RangeController to the Template explorer.

    Next, tell the List component to receive its content from the instance of the rangeController you just added.

3. Select the List component in the Template explorer to reveal its properties, then drag the RangeController proxy icon to the List contentController field in the Properties inspector. (To set the value, you can also type **@rangeController** in the field.)

    <figure>
        <img src="/images/montage-studio/tutorials/simple-to-do/fig05.png" alt="Setting the List object to receive content" style="width: 550px;">
        <figcaption><strong>Figure 5.</strong> Set the List to receive its content from the RangeController.</figcaption>
    </figure>

### Add the Task Button

To add a task button:

1. Add a Button node as a sibling between the Title (h1) and List (ul) nodes.

    <figure>
        <img src="/images/montage-studio/tutorials/simple-to-do/fig06.jpg" alt="Adding a Button node" style="width: 225px;">
        <figcaption><strong>Figure 6.</strong> Add a Button node as a sibling of the Title (h1) and List (ul) nodes.</figcaption>
    </figure>

2. In the Properties inspector, replace the default label (Button) with **New Task**.

    Next, you need to wire up the button so it does what it's supposed to do when clicked: add inputs to the list. To do this you need to set the RangeController to observe the new task button for “action.” This can be accomplished through a simple drag-and-drop operation.

    <figure>
        <img src="/images/montage-studio/tutorials/simple-to-do/diagram01.png" alt="Wiring up a button" style="width: 451px;">
    </figure>

3. On the Button card, drag the Add Listener (+) button to the RangeController card

    This opens the Button's Listener dialog box, with the event type (action) and listener (rangeController) conveniently filled in. (Alternatively, you can also click Add Listener [+] and then drag the RangeController proxy icon to the Listener field in the dialog box.)

    <figure>
        <img src="/images/montage-studio/tutorials/simple-to-do/fig07.png" alt="Wiring up the button" style="width: 550px;">
        <figcaption><strong>Figure 7.</strong> Drag the Add Listener (+) button to the RangeController to wire up the button.</figcaption>
    </figure>
    
4. Enter **addContent** in the optional Method Name field and click Define Listener. (When you specify a method name, MontageJS injects an actionEventListener with the target action configured for you.)

5. Save your changes. 

6. To take a peek at what you've build so far, click the Run button at the top of the Package explorer.

    <figure>
        <img src="/images/montage-studio/tutorials/simple-to-do/fig08.jpg" alt="Click Run to preview" style="width: 225px;">
        <figcaption><strong>Figure 8.</strong> Click the Run button to preview your application.</figcaption>
    </figure>

    Montage Studio will serve your application in a new tab in the browser. If you followed the instructions, you should see the title of the application and the New Task button. At this point, you can add any number of item placeholders to the list view by clicking New Task.
    
    <figure>
        <img src="/images/montage-studio/tutorials/simple-to-do/fig09.png" alt="Application preview" style="width: 225px;">
        <figcaption><strong>Figure 9.</strong> The view and model are in place.</figcaption>
    </figure>

Next, add a component that presents the individual tasks (task item child view). Technically, this can be accomplished by using the prebuilt ListItem component from the Digit group. For this exercise, however, you will create a new component that encapsulates the presentation of a task from scratch.


### Create a Task Component

To add a new component:

1. Click Add Component at the bottom of the Package explorer.

2. In the Save As text box, replace "my-component" with **task**, and then click Create.

    Montage Studio adds the new component to the UI folder of your project and opens its template in a new tab in the Component editor. (Note also that the Task component has been added to the project group at the top of the Library.)
    
3. Add a Checkbox node as a child element of the owner node.

    To ensure the component works as intended, you need to bind it to a task's completed state. This is controlled by the owner of the current document.

    <figure>
        <img src="/images/montage-studio/tutorials/simple-to-do/diagram02.png" alt="Binding a task to a completed state" style="width: 451px;">
    </figure>

4. In the Template explorer, click Add Binding (+) on the Checkbox card.

5. In the Target Path field enter **checked**, in the Source Path field enter **@owner.task.completed**, and then click the two-way Direction button—you want changes on either side to affect the other.

    >**Note**: This version of Montage Studio includes a rudimentary autocomplete feature: selecting a suggested value and pressing Tab advances the cursor to the next input field; pressing Return accepts the current selection and keeps the current field in focus.

    <figure>
        <img src="/images/montage-studio/tutorials/simple-to-do/fig10.jpg" alt="Application preview" style="width: 451px;">
        <figcaption><strong>Figure 10.</strong> Establish a two-way binding between the target and its source.</figcaption>
    </figure>

6. Click Define Binding.
    
    Next, you want to add a text field adjacent to the check box.

7. Add a TextField node as a sibling (next element) of the Checkbox node.

8. In the Template explorer, click Add Bindings (+) in the textField card.

9. In the Target Path field, enter **value**, click the two-way Direction button, and in the Source Path field enter **@owner.task.title**.

    <figure>
        <img src="/images/montage-studio/tutorials/simple-to-do/diagram03.png" alt="Defining bindings" style="width: 451px;">
    </figure>
    
10. Click Define Binding and save your changes.

    <figure>
        <img src="/images/montage-studio/tutorials/simple-to-do/fig11.jpg" alt="The completed Task component" style="width: 550px;">
        <figcaption><strong>Figure 11.</strong> The completed Task component in the Component editor.</figcaption>
    </figure>

### Add the Task Component to the List

Next, you need to add the new Task component as a child to the List node in the Main component.

1. Click the main.reel tab.

    You want to replace the placeholder li node with the task list item you just created.
    
2. Drag the Task component from the project group in the Library on the li node in the DOM explorer.

    <figure>
        <img src="/images/montage-studio/tutorials/simple-to-do/fig12.png" alt="Adding the Task component" style="width: 400px;">
        <figcaption><strong>Figure 12.</strong> Drag the Task component on the li node (left) to replace the placeholder li node with the new task list node (right).</figcaption>
    </figure>

    >**Note**: Alternatively, you can also drag the task component to the Template explorer and then drag the Task's proxy icon to the li node.

    Next, you need to set up a binding so that the children of your task list can be found. You know the binding drill by now…

3. Click Add Binding (+) in the task1 card.

4. In the Bindings dialog box, enter task in the Target Path field; keep the one-way Direction default setting. 

    You want to bind the task object to the list object, so enter **@list:iteration.object** in the Source Path field.

5. Click Define Binding and save your changes. 

    <figure>
        <img src="/images/montage-studio/tutorials/simple-to-do/fig13.jpg" alt="The complete list" style="width: 550px;">
        <figcaption><strong>Figure 13.</strong> Your list is complete.</figcaption>
    </figure>
    
Click the Run button again to preview your changes and you will see the same title and New Task button as before; but now you can add any number of inputs by clicking New Task.

<figure>
    <img src="/images/montage-studio/tutorials/simple-to-do/fig14.png" alt="The New Task button" style="width: 225px;">
    <figcaption><strong>Figure 14.</strong> Now the New Task button works: Each click adds a new undefined list item.</figcaption>
    </figure>

You're almost done. The only element still missing is a badge to keep track of the remaining tasks.

### Add a Task Badge

To add and wire up a task badge follow these steps:

1. Add a Badge widget as a sibling between the button and ul nodes in the DOM explorer.

    <figure>
        <img src="/images/montage-studio/tutorials/simple-to-do/fig15.jpg" alt="Adding a badge element" style="width: 225px;">
        <figcaption><strong>Figure 15.</strong> Add a badge between the button and ul nodes.</figcaption>
    </figure>
    
2. In the Template explorer, click Add Bindings (+) on the badge1 card.

3. In the Target Path field, enter **value**; in the Source Path field, enter **@rangeController.organizedContent.filter{!completed}.length**.

    This captures all tasks that have not been marked as completed (checked).

4. Click Define Binding and save your changes.

That's it. Click Run again and take the application for a spin: Click New Task to add any number of inputs, fill in the blank text fields with things to do, select a check box to mark a task as completed, and watch the badge count down on the number of remaining tasks.

##Summary

Montage Studio makes it a breeze to assemble the moving parts of a MontageJS application. Instead of writing a lot of code, you can use the Component editor and the integrated library of Montage and Digit components to:

* Define a component tree of user interface elements in the DOM explorer.
* Declare the behavior of the markup in the Template explorer.
* Modify the properties of selected objects in the Property inspector.

## Next Steps

To learn more about Montage Builder and MontageJS, refer to the following resources

* [Montage Studio documentation](/montage-studio/).
* [MontageJS documentation](/montagejs/).

For feedback and support, go to our [Forum](http://forum.montagestudio.com/).

