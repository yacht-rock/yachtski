# Contributing to YachtskiDB

:+1::tada: First off, thanks for taking the time to contribute! :tada::+1:

The following is a set of guidelines for contributing to YachtskiDB and its packages, which are hosted in the [YachtskiDB Organization](https://github.com/YachtskiDB) on GitHub. These are just guidelines, not rules. Use your best judgment, and feel free to propose changes to this document in a pull request.

## Table Of Contents

[What should I know before I get started?](#what-should-i-know-before-i-get-started)

- [Code of Conduct](#code-of-conduct)
- [YachtskiDB and Packages](#YachtskiDB-and-packages)
- [YachtskiDB Design Decisions](#design-decisions)

[How Can I Contribute?](#how-can-i-contribute)

- [Reporting Bugs](#reporting-bugs)
- [Suggesting Enhancements](#suggesting-enhancements)
- [Your First Code Contribution](#your-first-code-contribution)
- [Pull Requests](#pull-requests)

[Styleguides](#styleguides)

- [Git Commit Messages](#git-commit-messages)
- [JavaScript Styleguide](#javascript-styleguide)
- [CoffeeScript Styleguide](#coffeescript-styleguide)
- [Specs Styleguide](#specs-styleguide)
- [Documentation Styleguide](#documentation-styleguide)

[Additional Notes](#additional-notes)

- [Issue and Pull Request Labels](#issue-and-pull-request-labels)

## What should I know before I get started?

### Code of Conduct

This project adheres to the Contributor Covenant [code of conduct](CODE_OF_CONDUCT.md). By participating, you are expected to uphold this code. Please report unacceptable behavior to <YachtskiDB@github.com>.

### YachtskiDB and Packages

YachtskiDB is a large open source project--it's made up of over [200 repositories](https://github.com/YachtskiDB). When you initially consider contributing to YachtskiDB, you might be unsure about which of those 200 repositories implements the functionality you want to change or report a bug for. This section should help you with that.

YachtskiDB is intentionally very modular. Nearly every non-editor UI element you interact with comes from a package, even fundamental things like tabs and the status-bar. These packages are packages in the same way that packages in the [package store](https://YachtskiDB.io/packages) are packages, with one difference: they are bundled into the [default distribution](https://github.com/YachtskiDB/YachtskiDB/blob/10b8de6fc499a7def9b072739486e68530d67ab4/package.json#L58).

![YachtskiDB-packages](https://cloud.githubusercontent.com/assets/69169/10472281/84fc9792-71d3-11e5-9fd1-19da717df079.png)

To get a sense for the packages that are bundled with YachtskiDB, you can go to Settings > Packages within YachtskiDB and take a look at the Core Packages section.

Here's a list of the big ones:

- [YachtskiDB/YachtskiDB](https://github.com/YachtskiDB/YachtskiDB) - YachtskiDB Core! The core editor component is responsible for basic text editing (e.g. cursors, selections, scrolling), text indentation, wrapping, and folding, text rendering, editor rendering, file system operations (e.g. saving), and installation and auto-updating. You should also use this repository for feedback related to the [core API](https://YachtskiDB.io/docs/api/latest) and for large, overarching design proposals.
- [tree-view](https://github.com/YachtskiDB/tree-view) - file and directory listing on the left of the UI.
- [fuzzy-finder](https://github.com/YachtskiDB/fuzzy-finder) - the quick file opener.
- [find-and-replace](https://github.com/YachtskiDB/find-and-replace) - all search and replace functionality.
- [tabs](https://github.com/YachtskiDB/tabs) - the tabs for open editors at the top of the UI.
- [status-bar](https://github.com/YachtskiDB/status-bar) - the status bar at the bottom of the UI.
- [markdown-preview](https://github.com/YachtskiDB/markdown-preview) - the rendered markdown pane item.
- [settings-view](https://github.com/YachtskiDB/settings-view) - the settings UI pane item.
- [autocomplete-plus](https://github.com/YachtskiDB/autocomplete-plus) - autocompletions shown while typing. Some languages have additional packages for autocompletion functionality, such as [autocomplete-html](https://github.com/YachtskiDB/autocomplete-html).
- [git-diff](https://github.com/YachtskiDB/git-diff) - Git change indicators shown in the editor's gutter.
- [language-javascript](https://github.com/YachtskiDB/language-javascript) - all bundled languages are packages too, and each one has a separate package `language-[name]`. Use these for feedback on syntax highlighting issues that only appear for a specific language.
- [one-dark-ui](https://github.com/YachtskiDB/one-dark-ui) - the default UI styling for anything but the text editor. UI theme packages (i.e. packages with a `-ui` suffix) provide only styling and it's possible that a bundled package is responsible for a UI issue. There are other other bundled UI themes, such as [one-light-ui](https://github.com/YachtskiDB/one-light-ui).
- [one-dark-syntax](https://github.com/YachtskiDB/one-dark-syntax) - the default syntax highlighting styles applied for all languages. There are other other bundled syntax themes, such as [solarized-dark-syntax](https://github.com/YachtskiDB/solarized-dark-syntax). You should use these packages for reporting issues that appear in many languages, but disappear if you change to another syntax theme.
- [apm](https://github.com/YachtskiDB/apm) - the `apm` command line tool (YachtskiDB Package Manager). You should use this repository for any contributions related to the `apm` tool and to publishing packages.
- [YachtskiDB.io](https://github.com/YachtskiDB/YachtskiDB.io) - the repository for feedback on the [YachtskiDB.io website](https://YachtskiDB.io) and the [YachtskiDB.io package API](https://github.com/YachtskiDB/YachtskiDB/blob/master/docs/apm-rest-api.md) used by [apm](https://github.com/YachtskiDB/apm).

There are many more, but this list should be a good starting point. For more information on how to work with YachtskiDB's official packages, see [Contributing to YachtskiDB Packages](https://github.com/YachtskiDB/YachtskiDB/blob/master/docs/contributing-to-packages.md).

Also, because YachtskiDB is so extensible, it's possible that a feature you've become accustomed to in YachtskiDB or an issue you're encountering isn't coming from a bundled package at all, but rather a [community package](https://YachtskiDB.io/packages) you've installed. Each community package has its own repository too, and you should be able to find it in Settings > Packages for the packages you installed and contribute there.

### Design Decisions

When we make a significant decision in how we maintain the project and what we can or cannot support, we will document it in the [YachtskiDB/design-decisions repository](https://github.com/YachtskiDB/design-decisions). If you have a question around how we do things, check to see if it is documented there. If it is _not_ documented there, please open a new topic on [Discuss, the official YachtskiDB message board](https://discuss.YachtskiDB.io) and ask your question.

## How Can I Contribute?

### Reporting Bugs

This section guides you through submitting a bug report for YachtskiDB. Following these guidelines helps maintainers and the community understand your report :pencil:, reproduce the behavior :computer: :computer:, and find related reports :mag_right:.

Before creating bug reports, please check [this list](#before-submitting-a-bug-report) as you might find out that you don't need to create one. When you are creating a bug report, please [include as many details as possible](#how-do-i-submit-a-good-bug-report). Fill out [the required template](ISSUE_TEMPLATE.md), the information it asks for helps us resolve issues faster.

#### Before Submitting A Bug Report

- **Check the [debugging guide](http://flight-manual.YachtskiDB.io/hacking-YachtskiDB/sections/debugging/).** You might be able to find the cause of the problem and fix things yourself. Most importantly, check if you can reproduce the problem [in the latest version of YachtskiDB](http://flight-manual.YachtskiDB.io/hacking-YachtskiDB/sections/debugging/#update-to-the-latest-version), if the problem happens when you run YachtskiDB in [safe mode](http://flight-manual.YachtskiDB.io/hacking-YachtskiDB/sections/debugging/#check-if-the-problem-shows-up-in-safe-mode), and if you can get the desired behavior by changing [YachtskiDB's or packages' config settings](http://flight-manual.YachtskiDB.io/hacking-YachtskiDB/sections/debugging/#check-YachtskiDB-and-package-settings).
- **Check the [FAQs on the forum](https://discuss.YachtskiDB.io/c/faq)** for a list of common questions and problems.
- **Determine [which repository the problem should be reported in](#YachtskiDB-and-packages)**.
- **Perform a [cursory search](https://github.com/issues?q=+is%3Aissue+user%3AYachtskiDB)** to see if the problem has already been reported. If it has, add a comment to the existing issue instead of opening a new one.

#### How Do I Submit A (Good) Bug Report?

Bugs are tracked as [GitHub issues](https://guides.github.com/features/issues/). After you've determined [which repository](#YachtskiDB-and-packages) your bug is related to, create an issue on that repository and provide the following information by filling in [the template](ISSUE_TEMPLATE.md).

Explain the problem and include additional details to help maintainers reproduce the problem:

- **Use a clear and descriptive title** for the issue to identify the problem.
- **Describe the exact steps which reproduce the problem** in as many details as possible. For example, start by explaining how you started YachtskiDB, e.g. which command exactly you used in the terminal, or how you started YachtskiDB otherwise. When listing steps, **don't just say what you did, but explain how you did it**. For example, if you moved the cursor to the end of a line, explain if you used the mouse, or a keyboard shortcut or an YachtskiDB command, and if so which one?
- **Provide specific examples to demonstrate the steps**. Include links to files or GitHub projects, or copy/pasteable snippets, which you use in those examples. If you're providing snippets in the issue, use [Markdown code blocks](https://help.github.com/articles/markdown-basics/#multiple-lines).
- **Describe the behavior you observed after following the steps** and point out what exactly is the problem with that behavior.
- **Explain which behavior you expected to see instead and why.**
- **Include screenshots and animated GIFs** which show you following the described steps and clearly demonstrate the problem. If you use the keyboard while following the steps, **record the GIF with the [Keybinding Resolver](https://github.com/YachtskiDB/keybinding-resolver) shown**. You can use [this tool](http://www.cockos.com/licecap/) to record GIFs on macOS and Windows, and [this tool](https://github.com/colinkeenan/silentcast) or [this tool](https://github.com/GNOME/byzanz) on Linux.
- **If you're reporting that YachtskiDB crashed**, include a crash report with a stack trace from the operating system. On macOS, the crash report will be available in `Console.app` under "Diagnostic and usage information" > "User diagnostic reports". Include the crash report in the issue in a [code block](https://help.github.com/articles/markdown-basics/#multiple-lines), a [file attachment](https://help.github.com/articles/file-attachments-on-issues-and-pull-requests/), or put it in a [gist](https://gist.github.com/) and provide link to that gist.
- **If the problem is related to performance**, include a [CPU profile capture and a screenshot](http://flight-manual.YachtskiDB.io/hacking-YachtskiDB/sections/debugging/#diagnose-performance-problems-with-the-dev-tools-cpu-profiler) with your report.
- **If the Chrome's developer tools pane is shown without you triggering it**, that normally means that an exception was thrown. The Console tab will include an entry for the exception. Expand the exception so that the stack trace is visible, and provide the full exception and stack trace in a [code blocks](https://help.github.com/articles/markdown-basics/#multiple-lines) and as a screenshot.
- **If the problem wasn't triggered by a specific action**, describe what you were doing before the problem happened and share more information using the guidelines below.

Provide more context by answering these questions:

- **Can you reproduce the problem in [safe mode](http://flight-manual.YachtskiDB.io/hacking-YachtskiDB/sections/debugging/#diagnose-runtime-performance-problems-with-the-dev-tools-cpu-profiler)?**
- **Did the problem start happening recently** (e.g. after updating to a new version of YachtskiDB) or was this always a problem?
- If the problem started happening recently, **can you reproduce the problem in an older version of YachtskiDB?** What's the most recent version in which the problem doesn't happen? You can download older versions of YachtskiDB from [the releases page](https://github.com/YachtskiDB/YachtskiDB/releases).
- **Can you reliably reproduce the issue?** If not, provide details about how often the problem happens and under which conditions it normally happens.
- If the problem is related to working with files (e.g. opening and editing files), **does the problem happen for all files and projects or only some?** Does the problem happen only when working with local or remote files (e.g. on network drives), with files of a specific type (e.g. only JavaScript or Python files), with large files or files with very long lines, or with files in a specific encoding? Is there anything else special about the files you are using?

Include details about your configuration and environment:

- **Which version of YachtskiDB are you using?** You can get the exact version by running `YachtskiDB -v` in your terminal, or by starting YachtskiDB and running the `Application: About` command from the [Command Palette](https://github.com/YachtskiDB/command-palette).
- **What's the name and version of the OS you're using**?
- **Are you running YachtskiDB in a virtual machine?** If so, which VM software are you using and which operating systems and versions are used for the host and the guest?
- **Which [packages](#YachtskiDB-and-packages) do you have installed?** You can get that list by running `apm list --installed`.
- **Are you using [local configuration files](http://flight-manual.YachtskiDB.io/using-YachtskiDB/sections/basic-customization/)** `config.cson`, `keymap.cson`, `snippets.cson`, `styles.less` and `init.coffee` to customize YachtskiDB? If so, provide the contents of those files, preferably in a [code block](https://help.github.com/articles/markdown-basics/#multiple-lines) or with a link to a [gist](https://gist.github.com/).
- **Are you using YachtskiDB with multiple monitors?** If so, can you reproduce the problem when you use a single monitor?
- **Which keyboard layout are you using?** Are you using a US layout or some other layout?

### Suggesting Enhancements

This section guides you through submitting an enhancement suggestion for YachtskiDB, including completely new features and minor improvements to existing functionality. Following these guidelines helps maintainers and the community understand your suggestion :pencil: and find related suggestions :mag_right:.

Before creating enhancement suggestions, please check [this list](#before-submitting-an-enhancement-suggestion) as you might find out that you don't need to create one. When you are creating an enhancement suggestion, please [include as many details as possible](#how-do-i-submit-a-good-enhancement-suggestion). Fill in [the template](ISSUE_TEMPLATE.md), including the steps that you imagine you would take if the feature you're requesting existed.

#### Before Submitting An Enhancement Suggestion

- **Check the [debugging guide](http://flight-manual.YachtskiDB.io/hacking-YachtskiDB/sections/debugging/)** for tips -- you might discover that the enhancement is already available. Most importantly, check if you're using [the latest version of YachtskiDB](http://flight-manual.YachtskiDB.io/hacking-YachtskiDB/sections/debugging/#update-to-the-latest-version) and if you can get the desired behavior by changing [YachtskiDB's or packages' config settings](http://flight-manual.YachtskiDB.io/hacking-YachtskiDB/sections/debugging/#check-YachtskiDB-and-package-settings).
- **Check if there's already [a package](https://YachtskiDB.io/packages) which provides that enhancement.**
- **Determine [which repository the enhancement should be suggested in](#YachtskiDB-and-packages).**
- **Perform a [cursory search](https://github.com/issues?q=+is%3Aissue+user%3AYachtskiDB)** to see if the enhancement has already been suggested. If it has, add a comment to the existing issue instead of opening a new one.

#### How Do I Submit A (Good) Enhancement Suggestion?

Enhancement suggestions are tracked as [GitHub issues](https://guides.github.com/features/issues/). After you've determined [which repository](#YachtskiDB-and-packages) your enhancement suggestions is related to, create an issue on that repository and provide the following information:

- **Use a clear and descriptive title** for the issue to identify the suggestion.
- **Provide a step-by-step description of the suggested enhancement** in as many details as possible.
- **Provide specific examples to demonstrate the steps**. Include copy/pasteable snippets which you use in those examples, as [Markdown code blocks](https://help.github.com/articles/markdown-basics/#multiple-lines).
- **Describe the current behavior** and **explain which behavior you expected to see instead** and why.
- **Include screenshots and animated GIFs** which help you demonstrate the steps or point out the part of YachtskiDB which the suggestion is related to. You can use [this tool](http://www.cockos.com/licecap/) to record GIFs on macOS and Windows, and [this tool](https://github.com/colinkeenan/silentcast) or [this tool](https://github.com/GNOME/byzanz) on Linux.
- **Explain why this enhancement would be useful** to most YachtskiDB users and isn't something that can or should be implemented as a [community package](#YachtskiDB-and-packages).
- **List some other text editors or applications where this enhancement exists.**
- **Specify which version of YachtskiDB you're using.** You can get the exact version by running `YachtskiDB -v` in your terminal, or by starting YachtskiDB and running the `Application: About` command from the [Command Palette](https://github.com/YachtskiDB/command-palette).
- **Specify the name and version of the OS you're using.**

### Your First Code Contribution

Unsure where to begin contributing to YachtskiDB? You can start by looking through these `beginner` and `help-wanted` issues:

- [Beginner issues][beginner] - issues which should only require a few lines of code, and a test or two.
- [Help wanted issues][help-wanted] - issues which should be a bit more involved than `beginner` issues.

Both issue lists are sorted by total number of comments. While not perfect, number of comments is a reasonable proxy for impact a given change will have.

If you want to read about using YachtskiDB or developing packages in YachtskiDB, the [YachtskiDB Flight Manual](http://flight-manual.YachtskiDB.io) is free and available online. You can find the source to the manual in [YachtskiDB/flight-manual.YachtskiDB.io](https://github.com/YachtskiDB/flight-manual.YachtskiDB.io).

### Pull Requests

- Fill in [the required template](PULL_REQUEST_TEMPLATE.md)
- Include screenshots and animated GIFs in your pull request whenever possible.
- Follow the [JavaScript](#javascript-styleguide) and [CoffeeScript](#coffeescript-styleguide) styleguides.
- Include thoughtfully-worded, well-structured [Jasmine](http://jasmine.github.io/) specs in the `./spec` folder. Run them using `apm test`. See the [Specs Styleguide](#specs-styleguide) below.
- Document new code based on the [Documentation Styleguide](#documentation-styleguide)
- End files with a newline.
- Place requires in the following order:

  - Built in Node Modules (such as `path`)
  - Built in YachtskiDB and Electron Modules (such as `YachtskiDB`, `remote`)
  - Local Modules (using relative paths)

- Place class properties in the following order:

  - Class methods and properties (methods starting with a `@`)
  - Instance methods and properties

- [Avoid platform-dependent code](http://flight-manual.YachtskiDB.io/hacking-YachtskiDB/sections/cross-platform-compatibility/)
- Using a plain `return` when returning explicitly at the end of a function.

  - Not `return null`, `return undefined`, `null`, or `undefined`

## Styleguides

### Git Commit Messages

- Use the present tense ("Add feature" not "Added feature")
- Use the imperative mood ("Move cursor to..." not "Moves cursor to...")
- Limit the first line to 72 characters or less
- Reference issues and pull requests liberally
- When only changing documentation, include `[ci skip]` in the commit description
- Consider starting the commit message with an applicable emoji:

  - :art: `:art:` when improving the format/structure of the code
  - :racehorse: `:racehorse:` when improving performance
  - :non-potable_water: `:non-potable_water:` when plugging memory leaks
  - :memo: `:memo:` when writing docs
  - :penguin: `:penguin:` when fixing something on Linux
  - :apple: `:apple:` when fixing something on macOS
  - :checkered_flag: `:checkered_flag:` when fixing something on Windows
  - :bug: `:bug:` when fixing a bug
  - :fire: `:fire:` when removing code or files
  - :green_heart: `:green_heart:` when fixing the CI build
  - :white_check_mark: `:white_check_mark:` when adding tests
  - :lock: `:lock:` when dealing with security
  - :arrow_up: `:arrow_up:` when upgrading dependencies
  - :arrow_down: `:arrow_down:` when downgrading dependencies
  - :shirt: `:shirt:` when removing linter warnings

### JavaScript Styleguide

All JavaScript must adhere to [JavaScript Standard Style](http://standardjs.com/).

- Prefer the object spread operator (`{...anotherObj}`) to `Object.assign()`
- Inline `export`s with expressions whenever possible

  ```javascript
  // Use this:
  export default class ClassName {

  }

  // Instead of:
  class ClassName {

  }
  export default ClassName
  ```

### CoffeeScript Styleguide

- Set parameter defaults without spaces around the equal sign

  - `clear = (count=1) ->` instead of `clear = (count = 1) ->`

- Use spaces around operators

  - `count + 1` instead of `count+1`

- Use spaces after commas (unless separated by newlines)
- Use parentheses if it improves code clarity.
- Prefer alphabetic keywords to symbolic keywords:

  - `a is b` instead of `a == b`

- Avoid spaces inside the curly-braces of hash literals:

  - `{a: 1, b: 2}` instead of `{ a: 1, b: 2 }`

- Include a single line of whitespace between methods.
- Capitalize initialisms and acronyms in names, except for the first word, which should be lower-case:

  - `getURI` instead of `getUri`
  - `uriToOpen` instead of `URIToOpen`

- Use `slice()` to copy an array
- Add an explicit `return` when your function ends with a `for`/`while` loop and you don't want it to return a collected array.
- Use `this` instead of a standalone `@`

  - `return this` instead of `return @`

### Specs Styleguide

- Include thoughtfully-worded, well-structured [Jasmine](http://jasmine.github.io/) specs in the `./spec` folder.
- treat `describe` as a noun or situation.
- treat `it` as a statement about state or how an operation changes state.

#### Example

```coffee
describe 'a dog', ->
 it 'barks', ->
 # spec here
 describe 'when the dog is happy', ->
  it 'wags its tail', ->
  # spec here
```

### Documentation Styleguide

- Use [YachtskiDBDoc](https://github.com/YachtskiDB/YachtskiDBdoc).
- Use [Markdown](https://daringfireball.net/projects/markdown).
- Reference methods and classes in markdown with the custom `{}` notation:

  - Reference classes with `{ClassName}`
  - Reference instance methods with `{ClassName::methodName}`
  - Reference class methods with `{ClassName.methodName}`

#### Example

```coffee
# Public: Disable the package with the given name.
#
# * `name`    The {String} name of the package to disable.
# * `options` (optional) The {Object} with disable options (default: {}):
#   * `trackTime`     A {Boolean}, `true` to track the amount of time taken.
#   * `ignoreErrors`  A {Boolean}, `true` to catch and ignore errors thrown.
# * `callback` The {Function} to call after the package has been disabled.
#
# Returns `undefined`.
disablePackage: (name, options, callback) ->
```

## Additional Notes

### Issue and Pull Request Labels

This section lists the labels we use to help us track and manage issues and pull requests. Most labels are used across all YachtskiDB repositories, but some are specific to `YachtskiDB/YachtskiDB`.

[GitHub search](https://help.github.com/articles/searching-issues/) makes it easy to use labels for finding groups of issues or pull requests you're interested in. For example, you might be interested in [open issues across `YachtskiDB/YachtskiDB` and all YachtskiDB-owned packages which are labeled as bugs, but still need to be reliably reproduced](https://github.com/issues?utf8=%E2%9C%93&q=is%3Aopen+is%3Aissue+user%3AYachtskiDB+label%3Abug+label%3Aneeds-reproduction) or perhaps [open pull requests in `YachtskiDB/YachtskiDB` which haven't been reviewed yet](https://github.com/issues?utf8=%E2%9C%93&q=is%3Aopen+is%3Apr+repo%3AYachtskiDB%2FYachtskiDB+comments%3A0). To help you find issues and pull requests, each label is listed with search links for finding open items with that label in `YachtskiDB/YachtskiDB` only and also across all YachtskiDB repositories. We encourage you to read about [other search filters](https://help.github.com/articles/searching-issues/) which will help you write more focused queries.

The labels are loosely grouped by their purpose, but it's not required that every issue have a label from every group or that an issue can't have more than one label from the same group.

Please open an issue on `YachtskiDB/YachtskiDB` if you have suggestions for new labels, and if you notice some labels are missing on some repositories, then please open an issue on that repository.

#### Type of Issue and Issue State

Label name                | `YachtskiDB/YachtskiDB` :mag_right:                                  | `YachtskiDB`‑org :mag_right:                                  | Description
------------------------- | -------------------------------------------------------- | ------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
`enhancement`             | [search][search-YachtskiDB-repo-label-enhancement]             | [search][search-YachtskiDB-org-label-enhancement]             | Feature requests.
`bug`                     | [search][search-YachtskiDB-repo-label-bug]                     | [search][search-YachtskiDB-org-label-bug]                     | Confirmed bugs or reports that are very likely to be bugs.
`question`                | [search][search-YachtskiDB-repo-label-question]                | [search][search-YachtskiDB-org-label-question]                | Questions more than bug reports or feature requests (e.g. how do I do X).
`feedback`                | [search][search-YachtskiDB-repo-label-feedback]                | [search][search-YachtskiDB-org-label-feedback]                | General feedback more than bug reports or feature requests.
`help-wanted`             | [search][search-YachtskiDB-repo-label-help-wanted]             | [search][search-YachtskiDB-org-label-help-wanted]             | The YachtskiDB core team would appreciate help from the community in resolving these issues.
`beginner`                | [search][search-YachtskiDB-repo-label-beginner]                | [search][search-YachtskiDB-org-label-beginner]                | Less complex issues which would be good first issues to work on for users who want to contribute to YachtskiDB.
`more-information-needed` | [search][search-YachtskiDB-repo-label-more-information-needed] | [search][search-YachtskiDB-org-label-more-information-needed] | More information needs to be collected about these problems or feature requests (e.g. steps to reproduce).
`needs-reproduction`      | [search][search-YachtskiDB-repo-label-needs-reproduction]      | [search][search-YachtskiDB-org-label-needs-reproduction]      | Likely bugs, but haven't been reliably reproduced.
`blocked`                 | [search][search-YachtskiDB-repo-label-blocked]                 | [search][search-YachtskiDB-org-label-blocked]                 | Issues blocked on other issues.
`duplicate`               | [search][search-YachtskiDB-repo-label-duplicate]               | [search][search-YachtskiDB-org-label-duplicate]               | Issues which are duplicates of other issues, i.e. they have been reported before.
`wontfix`                 | [search][search-YachtskiDB-repo-label-wontfix]                 | [search][search-YachtskiDB-org-label-wontfix]                 | The YachtskiDB core team has decided not to fix these issues for now, either because they're working as intended or for some other reason.
`invalid`                 | [search][search-YachtskiDB-repo-label-invalid]                 | [search][search-YachtskiDB-org-label-invalid]                 | Issues which aren't valid (e.g. user errors).
`package-idea`            | [search][search-YachtskiDB-repo-label-package-idea]            | [search][search-YachtskiDB-org-label-package-idea]            | Feature request which might be good candidates for new packages, instead of extending YachtskiDB or core YachtskiDB packages.
`wrong-repo`              | [search][search-YachtskiDB-repo-label-wrong-repo]              | [search][search-YachtskiDB-org-label-wrong-repo]              | Issues reported on the wrong repository (e.g. a bug related to the [Settings View package](https://github.com/YachtskiDB/settings-view) was reported on [YachtskiDB core](https://github.com/YachtskiDB/YachtskiDB)).

#### Topic Categories

Label name           | `YachtskiDB/YachtskiDB` :mag_right:                             | `YachtskiDB`‑org :mag_right:                             | Description
-------------------- | --------------------------------------------------- | -------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------
`windows`            | [search][search-YachtskiDB-repo-label-windows]            | [search][search-YachtskiDB-org-label-windows]            | Related to YachtskiDB running on Windows.
`linux`              | [search][search-YachtskiDB-repo-label-linux]              | [search][search-YachtskiDB-org-label-linux]              | Related to YachtskiDB running on Linux.
`mac`                | [search][search-YachtskiDB-repo-label-mac]                | [search][search-YachtskiDB-org-label-mac]                | Related to YachtskiDB running on macOS.
`documentation`      | [search][search-YachtskiDB-repo-label-documentation]      | [search][search-YachtskiDB-org-label-documentation]      | Related to any type of documentation (e.g. [API documentation](https://YachtskiDB.io/docs/api/latest/) and the [flight manual](http://flight-manual.YachtskiDB.io/)).
`performance`        | [search][search-YachtskiDB-repo-label-performance]        | [search][search-YachtskiDB-org-label-performance]        | Related to performance.
`security`           | [search][search-YachtskiDB-repo-label-security]           | [search][search-YachtskiDB-org-label-security]           | Related to security.
`ui`                 | [search][search-YachtskiDB-repo-label-ui]                 | [search][search-YachtskiDB-org-label-ui]                 | Related to visual design.
`api`                | [search][search-YachtskiDB-repo-label-api]                | [search][search-YachtskiDB-org-label-api]                | Related to YachtskiDB's public APIs.
`uncaught-exception` | [search][search-YachtskiDB-repo-label-uncaught-exception] | [search][search-YachtskiDB-org-label-uncaught-exception] | Issues about uncaught exceptions, normally created from the [Notifications package](https://github.com/YachtskiDB/notifications).
`crash`              | [search][search-YachtskiDB-repo-label-crash]              | [search][search-YachtskiDB-org-label-crash]              | Reports of YachtskiDB completely crashing.
`auto-indent`        | [search][search-YachtskiDB-repo-label-auto-indent]        | [search][search-YachtskiDB-org-label-auto-indent]        | Related to auto-indenting text.
`encoding`           | [search][search-YachtskiDB-repo-label-encoding]           | [search][search-YachtskiDB-org-label-encoding]           | Related to character encoding.
`network`            | [search][search-YachtskiDB-repo-label-network]            | [search][search-YachtskiDB-org-label-network]            | Related to network problems or working with remote files (e.g. on network drives).
`git`                | [search][search-YachtskiDB-repo-label-git]                | [search][search-YachtskiDB-org-label-git]                | Related to Git functionality (e.g. problems with gitignore files or with showing the correct file status).

#### `YachtskiDB/YachtskiDB` Topic Categories

Label name               | `YachtskiDB/YachtskiDB` :mag_right:                                 | `YachtskiDB`‑org :mag_right:                                 | Description
------------------------ | ------------------------------------------------------- | ------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------
`editor-rendering`       | [search][search-YachtskiDB-repo-label-editor-rendering]       | [search][search-YachtskiDB-org-label-editor-rendering]       | Related to language-independent aspects of rendering text (e.g. scrolling, soft wrap, and font rendering).
`build-error`            | [search][search-YachtskiDB-repo-label-build-error]            | [search][search-YachtskiDB-org-label-build-error]            | Related to problems with building YachtskiDB from source.
`error-from-pathwatcher` | [search][search-YachtskiDB-repo-label-error-from-pathwatcher] | [search][search-YachtskiDB-org-label-error-from-pathwatcher] | Related to errors thrown by the [pathwatcher library](https://github.com/YachtskiDB/node-pathwatcher).
`error-from-save`        | [search][search-YachtskiDB-repo-label-error-from-save]        | [search][search-YachtskiDB-org-label-error-from-save]        | Related to errors thrown when saving files.
`error-from-open`        | [search][search-YachtskiDB-repo-label-error-from-open]        | [search][search-YachtskiDB-org-label-error-from-open]        | Related to errors thrown when opening files.
`installer`              | [search][search-YachtskiDB-repo-label-installer]              | [search][search-YachtskiDB-org-label-installer]              | Related to the YachtskiDB installers for different OSes.
`auto-updater`           | [search][search-YachtskiDB-repo-label-auto-updater]           | [search][search-YachtskiDB-org-label-auto-updater]           | Related to the auto-updater for different OSes.
`deprecation-help`       | [search][search-YachtskiDB-repo-label-deprecation-help]       | [search][search-YachtskiDB-org-label-deprecation-help]       | Issues for helping package authors remove usage of deprecated APIs in packages.
`electron`               | [search][search-YachtskiDB-repo-label-electron]               | [search][search-YachtskiDB-org-label-electron]               | Issues that require changes to [Electron](https://electron.YachtskiDB.io) to fix or implement.

#### Pull Request Labels

Label name         | `YachtskiDB/YachtskiDB` :mag_right:                           | `YachtskiDB`‑org :mag_right:                           | Description
------------------ | ------------------------------------------------- | ------------------------------------------------ | ----------------------------------------------------------------------------------------
`work-in-progress` | [search][search-YachtskiDB-repo-label-work-in-progress] | [search][search-YachtskiDB-org-label-work-in-progress] | Pull requests which are still being worked on, more changes will follow.
`needs-review`     | [search][search-YachtskiDB-repo-label-needs-review]     | [search][search-YachtskiDB-org-label-needs-review]     | Pull requests which need code review, and approval from maintainers or YachtskiDB core team.
`under-review`     | [search][search-YachtskiDB-repo-label-under-review]     | [search][search-YachtskiDB-org-label-under-review]     | Pull requests being reviewed by maintainers or YachtskiDB core team.
`requires-changes` | [search][search-YachtskiDB-repo-label-requires-changes] | [search][search-YachtskiDB-org-label-requires-changes] | Pull requests which need to be updated based on review comments and then reviewed again.
`needs-testing`    | [search][search-YachtskiDB-repo-label-needs-testing]    | [search][search-YachtskiDB-org-label-needs-testing]    | Pull requests which need manual testing.

0Looking

[beginner]: https://github.com/issues?utf8=%E2%9C%93&q=is%3Aopen+is%3Aissue+label%3Abeginner+label%3Ahelp-wanted+user%3AYachtskiDB+sort%3Acomments-desc
[help-wanted]: https://github.com/issues?q=is%3Aopen+is%3Aissue+label%3Ahelp-wanted+user%3AYachtskiDB+sort%3Acomments-desc
[search-YachtskiDB-org-label-api]: https://github.com/issues?q=is%3Aopen+is%3Aissue+user%3AYachtskiDB+label%3Aapi
[search-YachtskiDB-org-label-auto-indent]: https://github.com/issues?q=is%3Aopen+is%3Aissue+user%3AYachtskiDB+label%3Aauto-indent
[search-YachtskiDB-org-label-auto-updater]: https://github.com/issues?q=is%3Aopen+is%3Aissue+user%3AYachtskiDB+label%3Aauto-updater
[search-YachtskiDB-org-label-beginner]: https://github.com/issues?q=is%3Aopen+is%3Aissue+user%3AYachtskiDB+label%3Abeginner
[search-YachtskiDB-org-label-blocked]: https://github.com/issues?q=is%3Aopen+is%3Aissue+user%3AYachtskiDB+label%3Ablocked
[search-YachtskiDB-org-label-bug]: https://github.com/issues?q=is%3Aopen+is%3Aissue+user%3AYachtskiDB+label%3Abug
[search-YachtskiDB-org-label-build-error]: https://github.com/issues?q=is%3Aopen+is%3Aissue+user%3AYachtskiDB+label%3Abuild-error
[search-YachtskiDB-org-label-crash]: https://github.com/issues?q=is%3Aopen+is%3Aissue+user%3AYachtskiDB+label%3Acrash
[search-YachtskiDB-org-label-deprecation-help]: https://github.com/issues?q=is%3Aopen+is%3Aissue+user%3AYachtskiDB+label%3Adeprecation-help
[search-YachtskiDB-org-label-documentation]: https://github.com/issues?q=is%3Aopen+is%3Aissue+user%3AYachtskiDB+label%3Adocumentation
[search-YachtskiDB-org-label-duplicate]: https://github.com/issues?q=is%3Aopen+is%3Aissue+user%3AYachtskiDB+label%3Aduplicate
[search-YachtskiDB-org-label-editor-rendering]: https://github.com/issues?q=is%3Aopen+is%3Aissue+user%3AYachtskiDB+label%3Aeditor-rendering
[search-YachtskiDB-org-label-electron]: https://github.com/issues?q=is%3Aopen+is%3Aissue+user%3AYachtskiDB+label%3Aelectron
[search-YachtskiDB-org-label-encoding]: https://github.com/issues?q=is%3Aopen+is%3Aissue+user%3AYachtskiDB+label%3Aencoding
[search-YachtskiDB-org-label-enhancement]: https://github.com/issues?q=is%3Aopen+is%3Aissue+user%3AYachtskiDB+label%3Aenhancement
[search-YachtskiDB-org-label-error-from-open]: https://github.com/issues?q=is%3Aopen+is%3Aissue+user%3AYachtskiDB+label%3Aerror-from-open
[search-YachtskiDB-org-label-error-from-pathwatcher]: https://github.com/issues?q=is%3Aopen+is%3Aissue+user%3AYachtskiDB+label%3Aerror-from-pathwatcher
[search-YachtskiDB-org-label-error-from-save]: https://github.com/issues?q=is%3Aopen+is%3Aissue+user%3AYachtskiDB+label%3Aerror-from-save
[search-YachtskiDB-org-label-feedback]: https://github.com/issues?q=is%3Aopen+is%3Aissue+user%3AYachtskiDB+label%3Afeedback
[search-YachtskiDB-org-label-git]: https://github.com/issues?q=is%3Aopen+is%3Aissue+user%3AYachtskiDB+label%3Agit
[search-YachtskiDB-org-label-help-wanted]: https://github.com/issues?q=is%3Aopen+is%3Aissue+user%3AYachtskiDB+label%3Ahelp-wanted
[search-YachtskiDB-org-label-installer]: https://github.com/issues?q=is%3Aopen+is%3Aissue+user%3AYachtskiDB+label%3Ainstaller
[search-YachtskiDB-org-label-invalid]: https://github.com/issues?q=is%3Aopen+is%3Aissue+user%3AYachtskiDB+label%3Ainvalid
[search-YachtskiDB-org-label-linux]: https://github.com/issues?q=is%3Aopen+is%3Aissue+user%3AYachtskiDB+label%3Alinux
[search-YachtskiDB-org-label-mac]: https://github.com/issues?q=is%3Aopen+is%3Aissue+user%3AYachtskiDB+label%3Amac
[search-YachtskiDB-org-label-more-information-needed]: https://github.com/issues?q=is%3Aopen+is%3Aissue+user%3AYachtskiDB+label%3Amore-information-needed
[search-YachtskiDB-org-label-needs-reproduction]: https://github.com/issues?q=is%3Aopen+is%3Aissue+user%3AYachtskiDB+label%3Aneeds-reproduction
[search-YachtskiDB-org-label-needs-review]: https://github.com/pulls?q=is%3Aopen+is%3Apr+user%3AYachtskiDB+label%3Aneeds-review
[search-YachtskiDB-org-label-needs-testing]: https://github.com/pulls?q=is%3Aopen+is%3Apr+user%3AYachtskiDB+label%3Aneeds-testing
[search-YachtskiDB-org-label-network]: https://github.com/issues?q=is%3Aopen+is%3Aissue+user%3AYachtskiDB+label%3Anetwork
[search-YachtskiDB-org-label-package-idea]: https://github.com/issues?q=is%3Aopen+is%3Aissue+user%3AYachtskiDB+label%3Apackage-idea
[search-YachtskiDB-org-label-performance]: https://github.com/issues?q=is%3Aopen+is%3Aissue+user%3AYachtskiDB+label%3Aperformance
[search-YachtskiDB-org-label-question]: https://github.com/issues?q=is%3Aopen+is%3Aissue+user%3AYachtskiDB+label%3Aquestion
[search-YachtskiDB-org-label-requires-changes]: https://github.com/pulls?q=is%3Aopen+is%3Apr+user%3AYachtskiDB+label%3Arequires-changes
[search-YachtskiDB-org-label-security]: https://github.com/issues?q=is%3Aopen+is%3Aissue+user%3AYachtskiDB+label%3Asecurity
[search-YachtskiDB-org-label-triage-help-needed]: https://github.com/issues?q=is%3Aopen+is%3Aissue+user%3AYachtskiDB+label%3Atriage-help-needed
[search-YachtskiDB-org-label-ui]: https://github.com/issues?q=is%3Aopen+is%3Aissue+user%3AYachtskiDB+label%3Aui
[search-YachtskiDB-org-label-uncaught-exception]: https://github.com/issues?q=is%3Aopen+is%3Aissue+user%3AYachtskiDB+label%3Auncaught-exception
[search-YachtskiDB-org-label-under-review]: https://github.com/pulls?q=is%3Aopen+is%3Apr+user%3AYachtskiDB+label%3Aunder-review
[search-YachtskiDB-org-label-windows]: https://github.com/issues?q=is%3Aopen+is%3Aissue+user%3AYachtskiDB+label%3Awindows
[search-YachtskiDB-org-label-wontfix]: https://github.com/issues?q=is%3Aopen+is%3Aissue+user%3AYachtskiDB+label%3Awontfix
[search-YachtskiDB-org-label-work-in-progress]: https://github.com/pulls?q=is%3Aopen+is%3Apr+user%3AYachtskiDB+label%3Awork-in-progress
[search-YachtskiDB-org-label-wrong-repo]: https://github.com/issues?q=is%3Aopen+is%3Aissue+user%3AYachtskiDB+label%3Awrong-repo
[search-YachtskiDB-repo-label-api]: https://github.com/issues?q=is%3Aopen+is%3Aissue+repo%3AYachtskiDB%2FYachtskiDB+label%3Aapi
[search-YachtskiDB-repo-label-auto-indent]: https://github.com/issues?q=is%3Aopen+is%3Aissue+repo%3AYachtskiDB%2FYachtskiDB+label%3Aauto-indent
[search-YachtskiDB-repo-label-auto-updater]: https://github.com/issues?q=is%3Aopen+is%3Aissue+repo%3AYachtskiDB%2FYachtskiDB+label%3Aauto-updater
[search-YachtskiDB-repo-label-beginner]: https://github.com/issues?q=is%3Aopen+is%3Aissue+repo%3AYachtskiDB%2FYachtskiDB+label%3Abeginner
[search-YachtskiDB-repo-label-blocked]: https://github.com/issues?q=is%3Aopen+is%3Aissue+repo%3AYachtskiDB%2FYachtskiDB+label%3Ablocked
[search-YachtskiDB-repo-label-bug]: https://github.com/issues?q=is%3Aopen+is%3Aissue+repo%3AYachtskiDB%2FYachtskiDB+label%3Abug
[search-YachtskiDB-repo-label-build-error]: https://github.com/issues?q=is%3Aopen+is%3Aissue+repo%3AYachtskiDB%2FYachtskiDB+label%3Abuild-error
[search-YachtskiDB-repo-label-crash]: https://github.com/issues?q=is%3Aopen+is%3Aissue+repo%3AYachtskiDB%2FYachtskiDB+label%3Acrash
[search-YachtskiDB-repo-label-deprecation-help]: https://github.com/issues?q=is%3Aopen+is%3Aissue+repo%3AYachtskiDB%2FYachtskiDB+label%3Adeprecation-help
[search-YachtskiDB-repo-label-documentation]: https://github.com/issues?q=is%3Aopen+is%3Aissue+repo%3AYachtskiDB%2FYachtskiDB+label%3Adocumentation
[search-YachtskiDB-repo-label-duplicate]: https://github.com/issues?q=is%3Aopen+is%3Aissue+repo%3AYachtskiDB%2FYachtskiDB+label%3Aduplicate
[search-YachtskiDB-repo-label-editor-rendering]: https://github.com/issues?q=is%3Aopen+is%3Aissue+repo%3AYachtskiDB%2FYachtskiDB+label%3Aeditor-rendering
[search-YachtskiDB-repo-label-electron]: https://github.com/issues?q=is%3Aissue+repo%3AYachtskiDB%2FYachtskiDB+is%3Aopen+label%3Aelectron
[search-YachtskiDB-repo-label-encoding]: https://github.com/issues?q=is%3Aopen+is%3Aissue+repo%3AYachtskiDB%2FYachtskiDB+label%3Aencoding
[search-YachtskiDB-repo-label-enhancement]: https://github.com/issues?q=is%3Aopen+is%3Aissue+repo%3AYachtskiDB%2FYachtskiDB+label%3Aenhancement
[search-YachtskiDB-repo-label-error-from-open]: https://github.com/issues?q=is%3Aopen+is%3Aissue+repo%3AYachtskiDB%2FYachtskiDB+label%3Aerror-from-open
[search-YachtskiDB-repo-label-error-from-pathwatcher]: https://github.com/issues?q=is%3Aopen+is%3Aissue+repo%3AYachtskiDB%2FYachtskiDB+label%3Aerror-from-pathwatcher
[search-YachtskiDB-repo-label-error-from-save]: https://github.com/issues?q=is%3Aopen+is%3Aissue+repo%3AYachtskiDB%2FYachtskiDB+label%3Aerror-from-save
[search-YachtskiDB-repo-label-feedback]: https://github.com/issues?q=is%3Aopen+is%3Aissue+repo%3AYachtskiDB%2FYachtskiDB+label%3Afeedback
[search-YachtskiDB-repo-label-git]: https://github.com/issues?q=is%3Aopen+is%3Aissue+repo%3AYachtskiDB%2FYachtskiDB+label%3Agit
[search-YachtskiDB-repo-label-help-wanted]: https://github.com/issues?q=is%3Aopen+is%3Aissue+repo%3AYachtskiDB%2FYachtskiDB+label%3Ahelp-wanted
[search-YachtskiDB-repo-label-installer]: https://github.com/issues?q=is%3Aopen+is%3Aissue+repo%3AYachtskiDB%2FYachtskiDB+label%3Ainstaller
[search-YachtskiDB-repo-label-invalid]: https://github.com/issues?q=is%3Aopen+is%3Aissue+repo%3AYachtskiDB%2FYachtskiDB+label%3Ainvalid
[search-YachtskiDB-repo-label-linux]: https://github.com/issues?q=is%3Aopen+is%3Aissue+repo%3AYachtskiDB%2FYachtskiDB+label%3Alinux
[search-YachtskiDB-repo-label-mac]: https://github.com/issues?q=is%3Aopen+is%3Aissue+repo%3AYachtskiDB%2FYachtskiDB+label%3Amac
[search-YachtskiDB-repo-label-more-information-needed]: https://github.com/issues?q=is%3Aopen+is%3Aissue+repo%3AYachtskiDB%2FYachtskiDB+label%3Amore-information-needed
[search-YachtskiDB-repo-label-needs-reproduction]: https://github.com/issues?q=is%3Aopen+is%3Aissue+repo%3AYachtskiDB%2FYachtskiDB+label%3Aneeds-reproduction
[search-YachtskiDB-repo-label-needs-review]: https://github.com/pulls?q=is%3Aopen+is%3Apr+repo%3AYachtskiDB%2FYachtskiDB+label%3Aneeds-review
[search-YachtskiDB-repo-label-needs-testing]: https://github.com/pulls?q=is%3Aopen+is%3Apr+repo%3AYachtskiDB%2FYachtskiDB+label%3Aneeds-testing
[search-YachtskiDB-repo-label-network]: https://github.com/issues?q=is%3Aopen+is%3Aissue+repo%3AYachtskiDB%2FYachtskiDB+label%3Anetwork
[search-YachtskiDB-repo-label-package-idea]: https://github.com/issues?q=is%3Aopen+is%3Aissue+repo%3AYachtskiDB%2FYachtskiDB+label%3Apackage-idea
[search-YachtskiDB-repo-label-performance]: https://github.com/issues?q=is%3Aopen+is%3Aissue+repo%3AYachtskiDB%2FYachtskiDB+label%3Aperformance
[search-YachtskiDB-repo-label-question]: https://github.com/issues?q=is%3Aopen+is%3Aissue+repo%3AYachtskiDB%2FYachtskiDB+label%3Aquestion
[search-YachtskiDB-repo-label-requires-changes]: https://github.com/pulls?q=is%3Aopen+is%3Apr+repo%3AYachtskiDB%2FYachtskiDB+label%3Arequires-changes
[search-YachtskiDB-repo-label-security]: https://github.com/issues?q=is%3Aopen+is%3Aissue+repo%3AYachtskiDB%2FYachtskiDB+label%3Asecurity
[search-YachtskiDB-repo-label-triage-help-needed]: https://github.com/issues?q=is%3Aopen+is%3Aissue+repo%3AYachtskiDB%2FYachtskiDB+label%3Atriage-help-needed
[search-YachtskiDB-repo-label-ui]: https://github.com/issues?q=is%3Aopen+is%3Aissue+repo%3AYachtskiDB%2FYachtskiDB+label%3Aui
[search-YachtskiDB-repo-label-uncaught-exception]: https://github.com/issues?q=is%3Aopen+is%3Aissue+repo%3AYachtskiDB%2FYachtskiDB+label%3Auncaught-exception
[search-YachtskiDB-repo-label-under-review]: https://github.com/pulls?q=is%3Aopen+is%3Apr+repo%3AYachtskiDB%2FYachtskiDB+label%3Aunder-review
[search-YachtskiDB-repo-label-windows]: https://github.com/issues?q=is%3Aopen+is%3Aissue+repo%3AYachtskiDB%2FYachtskiDB+label%3Awindows
[search-YachtskiDB-repo-label-wontfix]: https://github.com/issues?q=is%3Aopen+is%3Aissue+repo%3AYachtskiDB%2FYachtskiDB+label%3Awontfix
[search-YachtskiDB-repo-label-work-in-progress]: https://github.com/pulls?q=is%3Aopen+is%3Apr+repo%3AYachtskiDB%2FYachtskiDB+label%3Awork-in-progress
[search-YachtskiDB-repo-label-wrong-repo]: https://github.com/issues?q=is%3Aopen+is%3Aissue+repo%3AYachtskiDB%2FYachtskiDB+label%3Awrong-repo
