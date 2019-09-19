# Contributing

If you're reading this, you're awesome! Thank you for helping us make this project great and being a part of the Material-UI community. Here are a few guidelines that will help you along the way.


## Getting started

1. Fork the Material-UI repository on GitHub

2. Clone the fork to your local machine and add upstream remote
```
git clone git@github.com:<yourname>/material-ui.git
cd material-ui
git remote add upstream git@github.com:mui-org/material-ui.git
```

NOTE: If you already have a cloned Material-UI repository make sure to synchronize it with the upstream one:
```
git checkout master
git pull upstream master
```
3. Create a branch `git checkout -b my-topic-branch`. Branching is usually done from `master`. ([check branches](#branch-structure))

4. Install `yarn` on your OS and start the development server with (in root folder of the project) `yarn && yarn start`. The sandbox application (with live reload) is available on `localhost:3000`.

5. Make changes to the code, [format](#code-formatting) it properly, add [tests](#testing) and [update API documentation](#updating-api-documentation). If new feature was added, considered [adding a demo to the documentation](#adding-a-demo-in-the-documentation).

NOTE: If you are submitting a new component, add it to the [`material-ui-lab`](https://github.com/mui-org/material-ui/tree/master/packages/material-ui-lab) package instead of `material-ui` core package.

6. Commit and push to your fork: `git push --set-upstream origin my-topic-branch`

7. On [github.com](https://github.com) go to your fork and make a PR back to `mui-org/material-ui`. Please name the PR as `[ComponentName] subject_line_format`. (Check [subject line format](https://chris.beams.io/posts/git-commit/#imperative))


## Branch Structure

`master` branch represents development as well as release branch for the latest version of Material-UI (v4.x).

The two other branches (`v0.x` and `v3.x`) are for legacy versions of Material-UI.


## Code formatting

Material-UI uses [eslint](https://eslint.org/) for code linting. It is recommended to use eslint plugin for your editor. The linting can also be run manually with `yarn lint`.

You can also run `yarn prettier` to reformat the code.

Code formatting is also doublechecked by [Circle CI](https://circleci.com/) when you submit a PR.

## Testing

Although test coverage is limited at present, please include tests along the new code. Tests can be run with `yarn test`. You can read more about our test setup in our test [README](https://github.com/mui-org/material-ui/blob/master/test/README.md). 


## Updating API documentation

If you change the API of some component, you should update its PropTypes (including PropTypes' comments). The updated API documentation (shown on [Material-UI](https://material-ui.com/) webpage) can then be generated using:
```sh
yarn docs:api
```


## Adding a demo in the documentation

### Let's get started.

It's simple. You just need to **create** a new file and **modify** two files.
For example, let say you want to add new demos for buttons component, then you have to go through the following steps:

#### 1. Add a new React component file under the related directory.

In this case, I'm going to add the new file to the following directory:
```
docs/src/pages/components/buttons/
```
And let's give it a name: `SuperButtons.js`.

We try to also document how to use this library with TypeScript. If you are familiar with
that language try writing that demo in TypeScript in a *.tsx file. When you're done
run `yarn docs:typescript:formatted` to automatically add a JavaScript version.

Apart from the inherent pros and cons of TypeScript the demos are also used to test our
type declarations. This helps a lot in catching regressions when updating our type
declarations.

#### 2. Edit the page Markdown file.

The Markdown file is the source for the website documentation. So, whatever you wrote there will be reflected on the website.
In this case, the file you need to edit is `docs/src/pages/components/buttons/buttons.md`, and I'm going to add a description about SuperButtons.

Changes should only be applied to the english version e.g. only `app-bar.md` and
not `app-bar-de.md`. For contributions concerning translations please read the [section
about translations](#Translations).

```diff
+ ### Super buttons
+
+ Sometimes, you need a super button to make your app looks **superb**. Yea ...
+
+ {{"demo": "pages/components/buttons/SuperButtons.js"}}
```

#### 3. You are done 🎉!

In case you missed something, [we have a real example that can be used as a summary report]((https://github.com/mui-org/material-ui/pull/8922/files)).

### About TypeScript demos

To help people use this library with TypeScript we try to provide equivalent demos
in TypeScript.

Changing demos in JavaScript requires a manual update of the TypeScript
version. If you are not familiar with this language you can add the filepath
of the TS demo to `docs/scripts/formattedTSDemos.js`. Otherwise our CI will fail the
`test_build` job. A contributor can later update the TypeScript version of that demo.

If you are already familiar with TypeScript you can simply write the demo in TypeScript.
`yarn docs:typescript:formatted` will transpile it down to JavaScript.


## Build Material-UI package locally

To use the provided build scripts with yarn you have to install `yarn@^1.9.0`.
Depending on the package you want to build just run `yarn workspace @material-ui/PACKAGE build`.

## Using local build of Material-UI in your application (`yarn link` mechanism)

Not possible at the moment!

## Translations

Translations are handled via [Crowdin](https://translate.material-ui.com).
You don't need to apply any changes to localized versions of our markdown files
i.e. files having a `-someLocale` suffix. Crowdin automatically takes care of syncing
these changes across the localized versions.

## Roadmap

To get a sense of where Material-UI is heading, or for ideas on where you could contribute, take a look at the [ROADMAP](https://github.com/mui-org/material-ui/blob/master/ROADMAP.md).

## License

By contributing your code to the mui-org/material-ui GitHub repository, you agree to license your contribution under the MIT license.
