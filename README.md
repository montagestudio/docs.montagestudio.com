This is the repo for the [docs.montagestudio.com](http://docs.montagestudio.com) site.

## Contributing
If you find any bugs or want to contribute, feel free to create an issue or send a pull request.

## Jekyll
The site uses Jekyll for templates and includes. You can find more infos on [jekyllrb.com](http://jekyllrb.com/).

### Install
First you need Ruby >= 2.0.0 and RubyGems, see [details](http://jekyllrb.com/docs/installation/). Once installed run:

    gem install jekyll

Then `cd` into your montagejs.org directory and run:

    jekyll serve

Now you should see the site at `http://localhost:4000`. You can close the server with `Ctrl c`.

Changes will be automatically watched and rebuilt.

## Building and deploying

> TODO: Update README _build script since the home example and apps are not part of this repo anymore. Only the API.

First install the build dependencies:

```bash
$ cd _build
$ npm install
$ cd ..
```

The apps, API docs and home example can all be built individually:

```bash
$ _build/build.js apps
$ _build/build.js api
$ _build/build.js home
```

or several at the same time:

```bash
$ _build/build.js home apps
```

or you can shortcut and build all the things:

```bash
$ _build/build.js all
```

The resulting files go into a directory, e.g. `api`, then Jekyll compiles any file with [YAML front matter](http://jekyllrb.com/docs/frontmatter/), or puts any file without YAML front matter verbatim in `_site`.

### API docs

To build *just* a subset of the API docs, or build docs for a specific version, use the `_build/jsdoc/jsdoc.js` command. It takes arguments for which project and version docs you want to build.

```bash
# Locally checked out Montage
$ _build/jsdoc/jsdoc.js montage npm-link $PWD/api
# Version of Montage
$ _build/jsdoc/jsdoc.js montage v0.13.9 $PWD/api
# Version of Digit
$ _build/jsdoc/jsdoc.js digit v0.4.0 $PWD/api
```
