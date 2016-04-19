# Swift Education Web Site

This is the source code for generating the static content for the [Swift Education web site](http://swifteducation.github.io) hosted via GitHub Pages.

## Organization

Everything in the [master](https://github.com/SwiftEducation/SwiftEducation.github.io/tree/master) branch is publicly accessible via [http://swifteducation.github.io](http://swifteducation.github.io). However, do not manually add html files and other assets to this branch! Everything on [master](https://github.com/SwiftEducation/SwiftEducation.github.io/tree/master) should be a result of site generation via the [develop](https://github.com/SwiftEducation/SwiftEducation.github.io/tree/develop) branch.

The [develop](https://github.com/SwiftEducation/SwiftEducation.github.io/tree/develop) branch contains the actual source code for the web site. It is within the [develop](https://github.com/SwiftEducation/SwiftEducation.github.io/tree/develop) branch that you should make any changes, and generate the results in the _build_ directory, which then gets committed and pushed to [master](https://github.com/SwiftEducation/SwiftEducation.github.io/tree/master). To learn more about this workflow, first **set up your development environment**, and then try making a change following the **workflow tutorial**.

## Set Up Your Development Environment

This web site uses the Ruby [Middleman](https://middlemanapp.com/) gem for static site generation. Doing so allows you, the developer, to think in terms of templates and other features usually found in dynamic server-side frameworks. You should know, or be prepared to know, a little about Ruby, HAML, Compass/SASS, and the typical client-side web stack (HTML5, CSS, JavaScript). Due to its influence on [Middleman](https://middlemanapp.com/), having experience with [Rails](http://rubyonrails.org) is a plus, but is not required. Learning how to use [Middleman](https://middlemanapp.com/) itself is fairly easy.

### Steps

1. You should have Ruby 2.2.2+ and [Bundler](http://bundler.io/) installed (`gem install bundler`).
2. Clone the repository: `git clone git@github.com:SwiftEducation/SwiftEducation.github.io.git`.
3. Check out the _develop_ branch (`git checkout develop`). The rule of thumb is "always be working in _develop_ or a branch off of _develop_."
4. Install the dependencies: `bundle install`.
5. Note that the _develop_ branch _.gitignore_ is set to ignore the _build_ directory. This is correct.
6. From within the repository root, clone the repository again, placing it within a _build_ directory. Yes, really: `git clone git@github.com:SwiftEducation/SwiftEducation.github.io.git build`. The rule of thumb here is "_build_ should always be on the _master_ branch."

What you have done here is created a local repository for the web site, where you will be working in the _develop_ branch. Once you have finished your changes, you will run `middleman build`. This will translate the code in _source_ into static files that reside in _build_. The _build_ directory is bound to the [master](https://github.com/SwiftEducation/SwiftEducation.github.io/tree/master) branch. After running `middleman build` to generate a new static site in the _build_ directory, you should `cd` into the _build_ directory, `commit` and `push`. This will push the new static site to the [master](https://github.com/SwiftEducation/SwiftEducation.github.io/tree/master) branch on the remote (GitHub), which will then be visible at [http://swifteducation.github.io](http://swifteducation.github.io).

## Workflow Tutorial

This development environment configuration may seem a little strange, but is actually a simple method for using [Middleman](https://middlemanapp.com/) with GitHub Pages for organizations. To help reify this, let's walk through a simple change.

1. In one console, checkout the _develop_ branch and run `middleman server` from the repo root. Keep this running, and use another console for everything else.
2. Visit [http://localhost:4567](http://localhost:4567) in your browser, and observe the web site. (If something doesn't look right, then do not continue. Either your environment isn't right, you didn't run `middleman server` from the repo root, or [this documentation is wrong](https://github.com/SwiftEducation/SwiftEducation.github.io/issues).
3. Verify that you are on the [develop](https://github.com/SwiftEducation/SwiftEducation.github.io/tree/develop) branch, and make a change. For example, add an innocuous HTML comment to the bottom of _source/layouts/layout.html.haml_.
4. Visit [http://localhost:4567](http://localhost:4567) in your browser, view the source of the page, and observe the change you made.
5. Once you are done, commit your change. You have just committed a source change to the [develop](https://github.com/SwiftEducation/SwiftEducation.github.io/tree/develop) branch.
6. Push your local _develop_ branch to the [develop](https://github.com/SwiftEducation/SwiftEducation.github.io/tree/develop) remote on GitHub: `git push origin develop`.
7. Visit [http://swifteducation.github.io](http://swifteducation.github.io) and notice that your changes _do not appear_ on the web site. Why is this? Because you made a change to the [develop](https://github.com/SwiftEducation/SwiftEducation.github.io/tree/develop) branch, which is right, but GitHub Pages for organizations reflects the [master](https://github.com/SwiftEducation/SwiftEducation.github.io/tree/master) branch. The next step is to get your changes into [master](https://github.com/SwiftEducation/SwiftEducation.github.io/tree/master).
8. Run `middleman build`. This will generate a new static site in the _build_ directory.
9. `cd` into the _build_ directory and run a `git diff`. If things seem as expected, `commit` and `push`.
10. Visit [http://swifteducation.github.io](http://swifteducation.github.io) and notice that your changes appear on the web site.

## Issues and Conventions

Try to create a well-described [issue](https://github.com/SwiftEducation/SwiftEducation.github.io/issues) for a feature before implementing the change in the [develop](https://github.com/SwiftEducation/SwiftEducation.github.io/tree/develop) branch. Commits related to the issue should use a commit message prefixed with `Issue #N`. Commits that resolve an issue should use `Fixes #N` in the message, typically as the prefix. See the [log](https://github.com/SwiftEducation/SwiftEducation.github.io/commits/develop) for examples.

Commit messages should use present tense. For example, "Correct missing giraffe and add new gerbil," rather than "Corrected missing giraffe..." or "Correcting missing giraffe."

## Contributing

Improvements and corrections are welcome! Simply fork this repository, make your changes on the `develop` branch, and create a pull request for the upstream `develop` branch (not `master`). If your PR is merged into the `develop` branch, you can expect that the site generation will be run, and that your changes will be reflected on `master` (and, therefore, the web site).

---

Copyright &copy; 2015 Apple, Inc. All rights reserved.