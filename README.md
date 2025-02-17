# [casbin.org](https://casbin.org/) [![Build Status](https://img.shields.io/github/workflow/status/casbin/casbin-website/Node.js%20CI)](https://github.com/casbin/casbin-website/actions) 
The site configuration and documentation powering Casbin's website: https://casbin.org

## Getting started

### Prerequisites

1.  Git
1.  Node: install version 6.2.2 or greater. Node v8 would be ideal.
1.  Yarn: See [Yarn Installation](https://yarnpkg.com/lang/en/docs/install/)
1.  Docusaurus: Run `yarn global add docusaurus-init` or `npm install --global docusaurus-init`

### Installation

1.  `git clone https://github.com/casbin/casbin-website` to download source code.
1.  `cd casbin-website` to go into the project root.
1.  `cd website` to go into the website portion of the project.
1.  `yarn` to install the website's npm dependencies (or `npm install`, if not using Yarn).

### Running locally

1.  `yarn start` to start the development server (powered by Docusaurus) (or `npm start`, if not using Yarn).
1.  open `http://localhost:3000/` to open the site in your favorite browser.

### Publish manually (optional)

Whenever a new commit lands in `master`, the change will be automatically
published to: https://casbin.org. However, if you want to deploy the site manually,
make sure you have `write` access to: https://github.com/casbin/casbin.github.io,
and use the following instruction:

1. `yarn run publish-gh-pages` to publish the site to GitHub pages: https://github.com/casbin/casbin.github.io (aka https://casbin.org).

# Overview

If you're here because you would like to contribute an edit or addition to the
docs, you'll probably want to take a look at the `docs/` directory.

To edit the internals of how the site is built, you may want to get familiarized
with how the site is built. The Casbin website is a static site generated
using [Docusaurus](https://docusaurus.io). The website configuration can be
found in the `website/` directory. Visit the Docusaurus website to learn more
about all the available configuration options.

## Directory structure

The following is a high-level overview of relevant files and folders.

```
casbin-website/
├── docs/
│   ├── assets/
│   ├── accessibility.md
│   └── ...
└── website/
    ├── blog/
    │   ├── assets/
    │   ├── 2015-03-26-casbin-bringing-modern-web-techniques-to-mobile.md
    │   └── ...
    ├── core/
    ├── pages/
    │   └── en/
    │       ├── ...
    │       ├── index.js
    │       └── ...
    ├── static/
    │   ├── css/
    │   ├── img/
    │   └── js/
    ├── versioned_docs/
    │   ├── version-0.5/
    │   └── ...
    ├── versioned_sidebars/
    │   ├── version-0.5-sidebars.json
    │   └── ...
    ├── showcase.json
    ├── sidebars.json
    ├── siteConfig.js
    └── versions.json
```

## Documentation sources

As mentioned above, the `docs/` folder contains the source files for all of the
docs in the Casbin website. In most cases, you will want to edit the files
within this directory. If you're adding a new doc or you need to alter the order
the docs appear in the sidebar, take a look at the `sidebars.json` file in the
`website/` directory. The sidebars file contains a list of document ids that
should match those defined in the header metadata (aka frontmatter) of the docs
markdown files.

### Versioned docs

The Casbin website is versioned as to allow users to go back and see the
API reference docs for any given release. A new version of the website is
generally made whenever there is a new Casbin release. When this happens,
any changes made to the `docs/` and `website/sidebars.json` files will be copied
over to the corresponding location within `website/versioned_docs/` and
`website/versioned_sidebars/`.

> Do not edit the auto-generated files within `versioned_docs/` or
> `versioned_sidebars/` unless you are sure it is necessary. Edits made to older
> versions will not be propagated to newer versions of the docs.

Docusaurus keeps track of the list of versions for the site in the
`website/versions.json` file. The ordering of the versions in this file should
be in reverse chronological order.

#### Cutting a new version

1.  `cd casbin-website` to go into the project root
1.  `cd website` to go into the website portion of the project
1.  Run `yarn version <version>` where `<version>` is the new version being
    released.

## Website configuration

The main config file for the website can be found at `website/siteConfig.js`.
This file tells Docusaurus [how to build the website](http://docusaurus.io/docs/en/site-config.html).
Edits to this file are rarely necessary.

The `pages/` subdirectory contains the Casbin components that make up the
non-documentation pages of the site, such as the homepage.

The `showcase.json` file contains the list of users that are highlighted in the
Casbin showcase.

## Contributing

### Create a branch

1.  `git checkout master` from any folder in your local `casbin-website` repository.
1.  `git pull origin master` to ensure you have the latest main code.
1.  `git checkout -b the-name-of-my-branch` (replacing `the-name-of-my-branch`
    with a suitable name) to create a branch.

### Make the change

1.  Follow the [Running locally](#running-locally) instructions.
1.  Save the files and check in the browser. Some changes may require a server restart.
1.  Changes to `/docs` will only be visible in the latest version of the documentation (master).

open `http://localhost:3000/casbin/versions.html` to see other versions.

### Test the change

1.  If possible, test any visual changes in all latest versions of common
    browsers, on both desktop and mobile.

### Push it

1.  Run `yarn prettier` to ensure your changes are consistent with other files in
    the repo
1.  `git add -A && git commit -m "My message"` (replacing `My message` with a
    commit message, such as `Fixed header logo on Android`) to stage and commit
    your changes
1.  `git push my-fork-name the-name-of-my-branch`
1.  Go to the
    [casbin-website repo](https://casbin.org)
    and you should see recently pushed branches.
1.  Follow GitHub's instructions.
1.  If possible, include screenshots of visual changes.

---

## Translation

[Crowdin](https://crowdin.com/project/casbin) is used for Casbin website's translation. You can contribute to the translation of your proficient languages on that.

### Build the translation project locally
Please contact the Casbin team for manager access on Crowdin.

### Manually trigger Crowdin [DEPRECATED]

- Install Crowdin CLI:

https://support.crowdin.com/cli-tool/

- Setup environment variable:

```
CROWDIN_DOCUSAURUS_API_KEY = XXX
```

- Upload:

```
crowdin --config ../crowdin.yaml upload sources --auto-update -b master
```

- Download:

```
crowdin --config ../crowdin.yaml download -b master
```

> Noting that the translation of the official website will update after a Pull Request is merged

## License

Casbin is [Apache licensed](./LICENSE).

Casbin documentation is [Creative Commons licensed](./LICENSE-docs).
