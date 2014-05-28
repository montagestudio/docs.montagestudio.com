---

layout: montage-studio
title: Styling MontageJS Applications = Montage Studio Documentation

this page: styling-montagejs-applications

---

# Styling MontageJS Applications

>**Note:** We are in the process of finalizing this document based on the latest version of the Montage Studio beta. Sorry about the inconvenience.

As you assemble the user interface components that make up your application, you realize quickly that the assembled components leave quite a bit to be desired in terms of visual styling. Out of the box, what you get are some minimally styled controls arranged in the order in which they appear in your root document’s markup. Chances are, even in development, before the application is finished, you (or your designer) may want to start to apply some styling to position the elements on the page as intended.

This article provides a high-level overview of how to style MontageJS applications. You will learn about styling individual components, setting global styles, using skins, customizing components, and creating your own user interface set.

# Getting Started

The first step to understanding how to style MontageJS applications is to understand how a MontageJS project is organized.

MontageJS applications are assembled out of multiple user interface components. These components are stored in the UI directory of your project and identified by a .reel extension. Each component in this directory presents a particular portion or view of your application and consists of three files that control the component’s structure (HTML), presentation (CSS), and behavior (JavaScript). At the top of the view hierarchy is main.reel, the main user interface component, which is provided with every new MontageJS project; think of it as the container that uses all the other components in this directory for the presentation.

Separating the structure, presentation, and behavior of user interface components into different files makes it easy for a designer to step in and control the look of your application. While developers work on the functionality of the app, assembling components into functional areas, designers can work on the look and feel of the app. The process is:

1. Identify the components in the project’s UI directory.

    Most likely, the items in this directory will not be listed in any particular hierarchical order; each component, however, corresponds to a functional area or view of your application. Determine how the components should be laid out based on your initial sketch, design comp, or prototype—for example, navigation, main content, footer, and so on.
    
2. Style the individual components.

    All of the components in the UI directory of your project start off with an almost blank style sheet, waiting for you to bring it to life by adding your meticulously crafted rules. The only content we pass along is the class name of the component’s root element (for example, in the case of a component named foo-bar.reel, the class name would be `FooBar`).
    
    To control the appearance and positioning of an individual component, you have to edit that component’s HTML and CSS files:
    
    <ul>
        <li>Add CSS class names to the markup of your component’s HTML file.</li>
        <li>Add the CSS statements to the component’s CSS file.</li>
    </ul>
    
    <figure style="margin-top:1em">
        <img src="/images/montage-studio/styling-overview/fig01.png" alt="Add the CSS statements to the component’s CSS file">
        <figcaption><strong>Figure 1.</strong> Add the CSS statements to the component’s CSS file.</figcaption>
    </figure>
    
    As a rule, only add styles to a component’s CSS file that are part of that component. This ensures that the styles of a component are loaded only when needed. Feel free to use our [naming conventions](http://docs.montagestudio.com/montagejs/naming-conventions.html#toc_3) on what to call the classes.
    
3. Set global styles.

    Styles you want to set on a global level may include fonts, font size, or color. Global styles are stored in a separate file in the assets/style/ directory. By default, every new MontageJS project includes style.css for your global styles. However, you can add any number of additional global style sheets. An optional CSS reset or normalize.css file also goes into the assets/style/ directory.
    
    Global style sheets are linked from the `head` element in the index.html document of your project.
    
    <figure>
        <img src="/images/montage-studio/styling-overview/fig02.jpg" alt="Global style sheets are linked in the index.html document">
        <figcaption><strong>Figure 2.</strong> Global style sheets are linked in the index.html document.</figcaption>
    </figure>
        
# Editing CSS Resources

Montage Studio currently does not provide any visual authoring tools or inspectors to help you edit CSS. When editing HTML and CSS files in Montage Studio, you have two options: you can use the built-in text editor or an external editor of your choice.

## Using the Built-in Editor

Montage Studio uses CodeMirror to provide basic text editor functionality. When you select a component’s HTML or CSS file in the project explorer, Montage Studio opens it in the built-in text editor.

Be sure to run the application source in live view mode when you are using the built-in editor; each time you modify a component’s CSS or HTML file, live view instantly updates to show the latest changes.

To launch live view, click the Run button and move the resulting tab to a new window so you can see the preview while editing the resources in Montage Studio. (For more details on live view mode see the section [Preview and Share](http://docs.montagestudio.com/montage-studio/overview-using-montage-studio.html#toc_18)).

<figure>
    <img src="/images/montage-studio/styling-overview/fig03.jpg" alt="Click Run to launch live view mode" style="max-width: 194px;">
    <figcaption><strong>Figure 3.</strong> Click Run to launch live view mode.</figcaption>
</figure>

## Using a Third-Party Editor

To use a third-party editor: Drag the CSS (or HTML) file you want to work on to your desktop and then open it in your preferred editor. When finished editing the file, save your changes and drag the file back to the component; Montage Studio will upload the file and replace the online version with your edited version.

<figure>
    <img src="/images/montage-studio/styling-overview/fig04.png" alt="Drag edited files to their respective components" style="max-width: 500px;">
    <figcaption><strong>Figure 4.</strong> Drag edited files to their respective components.</figcaption>
</figure>

To see how the application looks at this point, click the Run button.

# Layout and Positioning

The MontageJS framework currently does not provide traditional layout components to help position your user interface components. Nor do you have to use a special language (like MXML, for example) to lay out user interface components. Instead of using a containing element, you use CSS to lay out and align the user interface elements of your application. If your application targets modern browsers, you can use the flexbox layout module. Flexbox makes creating layouts for different screen sizes a lot easier and allows for greater flexibility when positioning child elements. To get started with flexbox, refer to the following resources:

* <a href="http://css-tricks.com/snippets/css/a-guide-to-flexbox/" target="_blank">A Complete Guide to Flexbox</a>
* <a href="http://webkit-flex.atomeye.com/" target="_blank">Webkit Flexbox Patterns</a>
* <a href="http://bennettfeely.com/flexplorer/" target="_blank">Flexplorer</a>
* <a href="http://the-echoplex.net/flexyboxes/" target="_blank">Flexy Boxes</a>

# Using the Digit UI Set

By default, every new MontageJS project includes the [Digit package](http://docs.montagestudio.com/montagejs/theme-digit-components.html) as a dependency. Digit is a touch-friendly UI set optimized for use with tablets and mobile devices.

<figure>
    <img src="/images/montage-studio/styling-overview/fig05.png" alt="Some Digit UI set components" style="max-width: 275px;">
    <figcaption><strong>Figure 5.</strong> Some Digit UI set components.</figcaption>
</figure>

>**Note:** If you've used MontageJS before, you may be familiar with the [Matte](http://docs.montagestudio.com/montagejs/theme-matte-components.html) and [Native](http://docs.montagestudio.com/montagejs/theme-native-components.html) UI sets, which are currently not supported. If you wanted to use either set instead of Digit, you would need to edit the package.json file of your project to add the dependency. The decision to use a widget set other than Digit should be made before you start assembling your application; the UI sets are currently not fully interchangeable. For more details on editing the package.json file, see [Manage Project Dependencies and Details](http://docs.montagestudio.com/montage-studio/overview-using-montage-studio.html#toc_6).

# Using Skins

Skins are presets that allow you to change the look of your application without changing the underlying functionality. Digit comes with four predefined skins: default, wireframe, light, and dark.

* **Default:** The default skin uses a single flat color and has a transparent background. Out of the box, the default color is black, but you can easily specify a different color as explained in the “Changing Colors” section. The default skin is best suited as a starter look or to try out new looks without having to override much.

    <figure>
        <img src="/images/montage-studio/styling-overview/ill01.png" alt="The default skin" style="width: 100px;">
    </figure>

* **Wireframe:** The wireframe skin is simplistic and uses only a grey tone. It is best used for prototyping. Use this skin if you want reviewers or clients to focus on the functionality first, without getting hung up on the look and feel of the application.

    <figure>
        <img src="/images/montage-studio/styling-overview/ill02.png" alt="The wireframe skin" style="width: 100px;">
    </figure>

* **Light / dark:** The light and dark skins use gradients and shadows and can be used individually or together in the same application; for example, you could use the dark skin for a sidebar and the light skin for the main area.

    <figure>
        <img src="/images/montage-studio/styling-overview/ill03.png" alt="The light and dark skins" style="width: 200px;">
    </figure>
    
## Using a Particular Skin

Every new MontageJS project you create uses the light skin. If you want to use a different skin, you need to change the `data-montage-skin` property in the outer `<div>` of the Main component’s template (main.html).

<figure>
    <img src="/images/montage-studio/styling-overview/fig06.png" alt="Change the `data-montage-skin` property to use a different skin">
    <figcaption><strong>Figure 6.</strong> Change the data-montage-skin property to use a different skin.</figcaption>
</figure>

* To use the dark or wireframe skin, change the property to `dark` or `wireframe`; for example, `data-montage-skin="wireframe"`.
* To use the flat default skin, remove the `data-montage-skin` attribute.

## Using Multiple Skins

To use multiple skins in the same project, you have to add the respective skins on sibling elements (MontageJS does not support nesting skins). For example, to use a light header, a dark footer, and a default main area, you would use the following markup (in the Main component’s template, for example).

```html
<body>
    <header data-montage-skin="light"></header>
    <main></main>
    <footer data-montage-skin="dark"></footer>
</body>
```

# Customizing Components

If you would like to customize a component from the Digit UI set, you can simply override the existing rule with your own CSS as outlined in the following use cases.

## Customizing a Component in a Single Area

Let’s say you added a Digit button to a Header component (header.reel); however, instead of the default round button you would like a square button. To accomplish this, you first add a new class to the button’s markup, for example, `Header-button`:

```html
<header class="Header">
    <button data-montage-id="button" class="Header-button">Button</button>
</header>
```

Then, in the header.css file, you can override it with:

```css
.Header-button.digit-Button {
    border-radius: 0;
}
```

Note that the selector has the Digit button class (`digit-Button`) chained to it. This is necessary because you do not know which class is loaded first; by adding a stronger specificity you ensure that the custom style is prioritized.

## Customizing a Component in Multiple Areas

In this case, you want to use a custom button class that you can apply in different areas of the application. In your markup, add the custom class, for example, `my-Button`:

```html
<button data-montage-id="button" class="my-Button">Button</button>
```

In your global style sheet, add the following:

```css
.my-Button.digit-Button {
    border-radius: 0;
}
```

## Customizing a Component across the Application

In this scenario, you add a class to the root element:

```html
<html class="MyApp">
```

And then use that class to override a component like this:

```css
.MyApp .digit-Button {
    border-radius: 0;
}
```

Be sure to add these styles to the global style sheet (/assets/style/style.css). You can also collect these types of styles in a separate style sheet that is linked off the application’s index.html file, for example:

```html
 <link rel="stylesheet" href="assets/style/style.css" />
 <link rel="stylesheet" href="assets/style/mystyles.css" />
```

## Customizing All of the Components in a UI Set

In theory, customizing all of the components in a UI set can be achieved as described in the previous section, by assigning styles for every component you use. In practice, however, this can make your application hard to maintain, and you may run into issues with nested components. Instead, you are better off creating your own UI set as described in the section “Creating a Custom UI Set.”

## Changing the Default Size

The Digit UI set uses `em`-based units with the `font-size` property to control size-related CSS properties; this makes it easy to change the size of components simply by specifying the `font-size` property.

* To change the size of a single component, change the `font-size` property in the component’s CSS file.

    <figure>
        <img src="/images/montage-studio/styling-overview/fig07.jpg" alt="Modify a component's size by changing the `font-size` property">
        <figcaption><strong>Figure 7.</strong> Modify a component's size by changing the font-size property.</figcaption>
    </figure>
    
* To change the size of all child components, add a `font-size` property to the parent element.
* To change the size of components globally, use the root selector: `html { font-size: 20px; }`.


Alternatively, you can also use the `font-size` property inside a media query; for example:

```css
@media (min-width: 800px) {
    .html {
        font-size: 20px;
    }
}
```

This allows you to adjust the the presentation for different screen sizes.

## Changing the Default Color

When using the Digit UI set, you are not limited to the default colors of the skins provided.

### Changing the Color of the Default Skin

Out of the box, the default skin is black, but you can easily specify a different color by adding a color property to the root (HTML) element, for example, `color: red;`; this causes all of your components to inherit the new color.

In general, all components can be colorized with the `color` property.

```css
.MyButton.digit-Button {
    color: red;
}
```

<figure>
    <img src="/images/montage-studio/styling-overview/ill04.png" alt="Add a color property to the root element to change the default color" style="width: 95px;">
</figure>

This approach also works for components that use a background color&#8212;like the handle of the Slider component&#8212;because the background color is set to use `currentColor`, which is mapped to `color`.

```css
.MySlider.digit-Slider {
    color: dodgerblue;
}
```

<figure>
    <img src="/images/montage-studio/styling-overview/ill05.png" alt="Add a color property to the root element to change the default color" style="width: 167.5px;">
</figure>

Colors are inherited; so you can colorize child components by using the `color` property on a parent; or the entire application by using the root `html` selector.
```css
html {
    color: dodgerblue;
}
```

<figure>
    <img src="/images/montage-studio/styling-overview/ill06.gif" alt="Colorize child components by using the `color` property on a parent">
</figure>

### Changing the Color of the Wireframe, Light, and Dark Skins

To change the color of the the other Digit skins, you first have to identify the properties you have to override. For example, if you wanted a green version of the light button, you would override it using these rules:

```css
.MyButton.digit-Button {
    text-shadow: 0 1px 0 hsla(0, 0%, 100%, 0.4);
    border-color: hsl(140, 100%, 34%);
    background-image: linear-gradient( hsl(140, 100%, 54%), 
                                       hsl(140, 100%, 44%) );
    box-shadow: inset 0 1px 1px hsla(0, 100%, 100%, 0.77),
                inset 0 -1px 1px hsla(0, 0%, 0%, 0.04),
                0 1px 0 hsla(0, 0%, 100%, 0.6);
}
```

<figure>
    <img src="/images/montage-studio/styling-overview/ill07.png" alt="Identify the properties you have to override" style="width: 93px;">
</figure>

>**Note:** Depending on the browsers you want to support, you may have to add vendor prefixes for the gradients.

# Creating a Custom UI Set

Overriding Digit is great for minor changes. However, if you wanted to create a UI component that differs vastly in appearance from the components provided, it would be easier to create your own UI set. In outline, you would:

1. Add a custom component to your application source.
2. Copy the structure (HTML) and behavior (JavaScript) from the original Digit component to your custom component's HTML and JS files. (Refer to the <a href="https://github.com/montagejs/digit/tree/master/ui" target="_blank">Digit repo</a> on GitHub.)
3. Style the component as desired.

For example, if you wanted to create a custom button, you would follow these steps:

1. Click Add Component at the bottom of the project explorer (or choose File > New > Component).

    <figure>
        <img src="/images/montage-studio/styling-overview/ill08.png" alt="Click Add Component.">
    </figure>

2. Enter a name in the Create Component dialog box (for example, **button**) and click Create.

    <figure>
        <img src="/images/montage-studio/styling-overview/ill09.png" alt="Enter a name for the component.">
    </figure>
    
    Montage Studio adds the new component to the UI directory of your project.
    
    <figure>
        <img src="/images/montage-studio/styling-overview/ill10.png" alt="Enter a name for the component.">
    </figure>
    
3. Copy the HTML and JS code of the <a href="https://github.com/montagejs/digit/tree/master/ui/button.reel" target="_blank">Digit button</a> component into your custom component to ensure it functions as designed.
    
4. Add your own CSS statements.
 
5. To use your new custom button, just drag it from the library to the DOM explorer.
 
     <figure>
        <img src="/images/montage-studio/styling-overview/ill11.png" alt="Enter a name for the component.">
    </figure>
 
>**Note:** Be sure to strip the `digit-` prefix from the markup, so there is no conflict when using a corresponding Digit component in the same application.
