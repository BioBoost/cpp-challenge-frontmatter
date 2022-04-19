# C++ Challenge - FrontMatter

Front Matter is structured metadata that lives at the top of your content files that allows you to add custom variables to your projects. It is typically used with static web page generators and such tools.

It can also be useful in the context of exercises or challenges for a programming course :). Take for example a C++ challenge that contains a `README.md` file for the user, which also contains a small portion of front matter data for a unit test framework or other tool.

The front matter must be the first thing in the file and must take the form of valid YAML set between triple-dashed lines.

Let's take a look at a basic example:

```yaml
---
name: hello-world
description: Display hello world in the terminal.
difficulty: easy
tags: terminal,output,iostream
finished: false
---
```

Below the front matter the actual markdown or other content can then be placed.

## Your Assignment

Your assignment consists of creating a command line tool that can both generate the front matter as well as parse it.

### Generating Frontmatter

The first tool should be able to generate a `README.md` file with a front matter section at the top. The actual content for this front matter should be retrieved from the user using a wizard tool (ask input from the user step by step).

The following information should be requested from the user:

* **name**: the name of the challenge. For example `Hello World`.
  * The name of the challenge should be used as is for the first markdown heading.
  * The front matter `name` should be the lower cased version where spaces are replaced by dashes `-`. In this case `hello-world`.
* **description**: a small description of the challenge. Typically one-liner. For example `Display hello world in the terminal.`.
* **difficulty**: the difficulty of the challenge. Possible options are `easy`, `normal` and `hard`.
* **tags**: a comma-separated list of keywords. For example: `terminal,output,iostream`
* **finished**: a boolean indicating if the student finished the challenge or not. Options are `true` and `false`.
* The name of the output file, which defaults to `README.md`.

After requesting the information from the user the application should generate a `README.md` file (or other filename if changed by user) with the content shown below (of-course with the front matter data provided by the user):

```
---
name: hello-world
description: Display hello world in the terminal.
difficulty: easy
tags: terminal,output,iostream
finished: false
---

# Hello World

Please describe challenge here
```

### Parsing

A second tool should be able to parse the front matter of a given markdown file (default `README.md`) in the current directory. The user should be able to select what information should be extracted from the front matter by using command line argument options.

For example:

```bash
frontparse --name
```

Would output:

```
hello-world
```

When providing more than one options, you can separate the data using a newline:

```bash
frontparse --name --tags
```

Outputting:

```
hello-world
terminal,output,iostream
```

If the user does not specify a filename as first argument, `README.md` should be assumed. If the user does specify a filename as first argument, that file should be opened instead. For example:

```shell
frontparse project.md --name
```

Feel free to use a library such as `getopt` or similar to parse the command line arguments.

You should not hardcode the available front matter options in the application. Just take in the options the user provided and check if it is available as a front matter item. If it is, output the content to the terminal. If it is not, output an empty line.

Also make sure that the application provides decent error handling and does not crash if something goes wrong.

## General

Below are some general guidelines for this assignment:

* Make sure to create two separate projects for this.
  * The front matter generator should be called `frontgen`
  * The front matter parser should be called `frontparse`
* Both applications should have a `--help` flag that provides some basic information to the user. Checkout how other command line applications display help.
* Make sure to commit regularly and to add decent log messages. I should be able to track your progress through the commit history.
* Make sure that both projects have `Makefile` to compile the applications
* Both applications should be linux compatible.
* Provide a decent README for both projects ! Describe the tool, how to set it up, how it works, what to expect, ...

You can find an example markdown file in the directory `./hello-world`.
