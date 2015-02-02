MontageJS & Montage Studio Docs
===


## Contributing

For contribution to non-API MontageJS docs & Montage Studio docs, please submit a PR against a `.md` file in this repo.

For contribution to MontageJS API docs, please submit a PR against [MontageJS repo](https://github.com/montagejs/montage) using [JSDoc](http://usejsdoc.org/).


## Setting up Local Jekyll Environment

The docs site uses [Jekyll](http://jekyllrb.com/) and is automatically built/deployed via [GitHub Pages](https://help.github.com/articles/using-jekyll-with-pages/).

First you need [Ruby](https://www.ruby-lang.org) >= 2.0.0, RubyGems (comes with Ruby >= 1.9) and [Bundler](bundler.io). Once installed, clone this repo then run `bundle install` in repo directory. This will get you a local environment in sync with [GitHub Pages' dependencies](https://pages.github.com/versions/).

Now run `bundle exec jekyll serve`, then browse to `http://localhost:4000`. Changed files will be automatically watched and rebuilt. You can close the server with `Ctrl c`.


## Building MontageJS API Docs

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
