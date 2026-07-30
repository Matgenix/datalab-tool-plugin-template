# datalab tool plugin template

Copier template for independently maintained
[datalab](https://github.com/Matgenix/datalab) tool plugins.

> [!WARNING]
> The datalab tool API is under active development. Generated projects
> currently pin the compatible Matgenix datalab commit.

The template generates either:

- a standalone tool that opens outside the datalab application and uses a
  temporary tool access token; or
- an in-app tool that renders below the datalab navigation and uses the
  browser-session frontend SDK.

Both variants include packaging, documentation, continuous integration,
pre-commit, tests, an MIT license, and Copier update metadata. In-app projects
also include the minimal Vue/Vite frontend and may declare a selected-item
table action.

## Generate a project

Install [Copier](https://copier.readthedocs.io/) and generate a repository:

```shell
uvx copier copy --trust \
  https://github.com/Matgenix/datalab-tool-plugin-template \
  ../my-datalab-tool
```

Then initialize and publish the generated repository:

```shell
cd ../my-datalab-tool
git init
git add .
git commit -m "Initial tool plugin"
git branch -M main
git remote add origin git@github.com:YOUR-NAMESPACE/YOUR-REPOSITORY.git
git push -u origin main
```

## Update a generated project

After the template has a new release:

```shell
uvx copier update
```

Review the resulting changes, resolve conflicts, rebuild any in-app frontend
bundle, and run the generated checks before committing.

See the
[standalone example](https://github.com/Matgenix/datalab-standalone-tool-plugin-example)
and
[in-app example](https://github.com/Matgenix/datalab-in-app-tool-plugin-example).

Tool plugins are trusted extensions. A datalab deployment administrator must
review their Python code, dependencies, release provenance, and—for in-app
tools—the frontend source and compiled bundle before installation or upgrade.
