---

layout: docs
title: Set Up MontageJS Development - Getting Started Part 1

this-page: montagejs-setup

redirect_from:
    - /docs/getting-started.html
    - /docs/Quick-Start.html

---

Getting Started with MontageJS
===

MontageJS is an HTML5 framework for building rich single-page applications (SPAs). The framework features mobile-optimized user interface widgets, logic-less templates, reusable components, simple and two-way bindings between components and objects, implicit event delegation, a managed draw cycle, and powerful command line tools for kickstarting and compiling SPA projects.

## Next-gen Front-end Development

Most frameworks provide you with a download link to code libraries. The entire framework typically includes a lot more functionality than needed for any given application. Including whole frameworks and libraries creates a lot of overhead and downloaded bytes, problematic in a web app environment with bandwidth and processing constraints.

MontageJS takes a different approach. You do not need to download or link to a prebuilt, kitchensink-style framework in your application. MontageJS uses the [**CommonJS**](http://commonjs.org) module system and is part of the [**npm**](http://npmjs.org) package ecosystem. This makes it easy for developers to set up a client-side development environment and organize their code base. In development, you `require` the modules and components that provide just the functionality you need. For production, you use [**mop**](tools-mop.html), the Montage optimizer, to analyze your project and its dependencies, and then create a minified and optimized version of your source code, which includes only those modules and components your application actually uses.

## Setting Up MontageJS Development

Before you can start building applications with MontageJS, you need to set up your development environment. The setup involves installing the following software package and command line tools:

* [Node.js and npm](http://nodejs.org)
* [Minit](tools-minit.html), the MontageJS initializer

You also need a recent stable release of an evergreen browser, e.g. Chrome, Safari, Firefox, etc.

### Before You Begin

<a href="http://nodejs.org/download/" target="_blank">Download</a> and run the prebuilt Node.js installer for your platform from the Node.js website if you haven't already. MontageJS uses Node.js and npm, which is part of the Node.js installation, for its command line tools and for version and code dependency management in development.

### Step 1: Install minit

The minit command line tool provides a convenient way to kickstart your MontageJS projects. With minit you can quickly generate an application template that includes everything you need to start building a mobile-optimized SPA. Use the following commands to install the latest version of minit for your platform:

* **Mac OS X / Linux:** Open a Terminal window and type:

    ```
    $ sudo npm install -gq minit@latest
    ```

    > **Note:** Minit does not need `sudo` access; npm uses `sudo` to make command line utilities such as minit available system wide. Also, when run as root, npm will downgrade permissions before running any build scripts that package authors specified. For more details see the npm <a href="https://npmjs.org/doc/README.html" target="_blank">readme</a>.

* **Windows:** Open the Command Prompt and type:

    ```
    npm install -gq minit@latest
    ```

### Step 2: Create a New Project

To create a new MontageJS project, enter the following command at the prompt (<em>app-name</em> = a short and descriptive name of your choice):

```
$ minit create:app -n app-name
```

This generates the _app-name_ directory—which includes the MontageJS code dependencies—in your current directory.

>**Note:** For a brief overview of the files and folders included in a default MontageJS project, see the readme file in the "app-name" project directory.


### Step 3: Verify Your Setup

To verify your setup:

1. Switch to the _app-name_ directory and use minit to serve your project:

    ```
    $ cd app-name
    $ minit serve &
    ```

    >**Note:** In development, MontageJS applications rely on the XMLHttpRequest (XHR) API to load components and modules (which is why you need a server to preview your project in progress); `minit serve &` sets up a local on-demand web server. The ampersand (`&`) option ensures that you don't have to open a second Terminal window while working on your project.

2. Point your browser to http://localhost:8083/.

    If all went well, you should see a blank page with a version reference in the upper left corner of the page (see Figure 1).

    <figure>
    	<img src="/images/docs/montagejs-setup/fig01.jpg" alt="MontageJS development is set up." style="width: 451px;">
    	<figcaption><strong>Figure 1.</strong> MontageJS development is set up.</figcaption>
    </figure>

You are now ready to start coding.

## Next Steps

* To learn how to build a simple MontageJS application, continue with [Hello MontageJS](http://montagejs.org/docs/hello-montagejs.html)
* To explore MontageJS on your own, check out other docs, articles & demos using the left navigation

