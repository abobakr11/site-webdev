---
layout: angular
title: Webdev
description: A command line interface for Dart web development.
---

The [webdev][] package provides a command line interface (CLI) for users and
tools to build and serve web apps.
The `webdev` tool is built on [build_runner][] and replaces `pub build` and `pub
serve`. If you've previously used `build_runner`, you should no longer need to
use it directly, except to run tests from the command line.

## Installation

[Globally install][] webdev using pub:

```terminal
$ pub global activate webdev
```

[Globally install]: {{site.dartlang}}/tools/pub/cmd/pub-global

## Command: serve {#serve}

To launch a development server, which serves your app and watches for source
code changes, use the following command:

```
webdev serve [--release] [ [<directory>[:<port>]] ... ]
```

By default your app is compiled using [dartdevc][] and served from the `web`
directory on port `8080`:

```terminal
$ webdev serve
```

To build using [dart2js][], add the `--release` flag.

You can specify different directory-port configurations. For example, the
following command sets up an additional port to run component tests in the
browser at [localhost:8081](http://localhost:8081):

```terminal
$ webdev serve web test:8081
```

To run tests directly from the command line use [build_runner test][].

## Command: build {#build}

Use the following command to build your app:

```
webdev build [--no-release] --output [<dirname>:]<dirname>
```

The first build is the slowest. After that, assets are cached on disk and
incremental builds are faster.

By default, the `build` command uses the [dart2js][] web compiler to create a
production version of your app. Add `--no-release` to compile with [dartdevc][].
Using the `--output` option, you can control which top-level project folders are
compiled and where output is written.

For example, the following command uses the dartdevc to compile the project's
top-level `web` folder into the `build` directory:

```terminal
$ webdev build --no-release --output web:build
```

You can customize your build using build config files. For more information, see
[Build config files.](/tools/build_runner#config)

## More information

For a complete list of `webdev` options, run `webdev --help` or see the
[webdev package README.][webdev]

[build_runner]: /tools/build_runner
[build_runner test]: /tools/build_runner#test
[dart2js]: /tools/dart2js
[dartdevc]: /tools/dartdevc
[webdev]: https://pub.dartlang.org/packages/webdev
