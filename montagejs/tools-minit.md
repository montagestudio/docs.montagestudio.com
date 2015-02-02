---

layout: docs
title: minit | MontageJS utility

this-page: tools-minit

---

# Using `minit`

The MontageJS initializer, [minit](https://github.com/montagejs/minit), is a multipurpose command line utility that provides a convenient way to kickstart and serve your MontageJS projects locally. With `minit` you can quickly generate blank application projects, directories, and add components to an existing project.

## Basic Examples of Using `minit`

Run the following commands from within your project directory:

* To create a new project:

    ```sh
    $ minit create:app -n app-name
    ```

    This generates a new directory `app-name`, which contains the default MontageJS application directories with production dependencies.

* To add a component to a project:

    ```sh
    $ minit create:component -n component-name
    ```

    This generates a new UI component `component-name.reel` in the `ui` directory of the current application directory. It contains default HTML, CSS, and JS files for your component.

* To spin up a local server for previewing the current project in the browser:

    ```sh
    $ minit serve &
    ```

    The ampersand `&` flag ensures that you don't have to open a second Terminal window while working on your project. To close the server, run `minit` again then hit `Ctrl C`.

* To update to the latest version of `minit`:

    ```sh
    $ npm install -g minit@latest
    ```

* For a complete list of `minit` options:

    ```sh
    $ minit --help
    ```

See also the [minit repo on Github](https://github.com/montagejs/minit).
