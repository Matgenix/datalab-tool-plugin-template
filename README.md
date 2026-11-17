# datalab tool plugin template

Use this Copier template to create an independently maintained
[datalab](https://github.com/datalab-org/datalab) tool plugin. Generated
projects include packaging, tests, documentation, continuous integration,
pre-commit checks, an MIT license, and Copier update metadata.

> [!WARNING]
> The tool API is still being developed on the Matgenix
> `dw/tools_plugins_nojupyter` branch. Generated development dependencies point
> to that branch until the feature is merged upstream.

## Choose a tool type

- **In-app** renders below datalab's navigation and uses the browser-session
  frontend SDK. The template includes a minimal Vue/Vite frontend.
- **Standalone** opens a separate page or service and uses a temporary tool
  access token.

Either type can add a selected-items table action. Read
[Developing tool plugins](https://docs.datalab-org.io/en/latest/plugin-development/tool-plugin/)
before choosing; it explains the UI trade-offs, provider contract, permissions,
testing, packaging, and release workflow.

## Generate a project

```shell
uvx copier copy --trust \
  https://github.com/Matgenix/datalab-tool-plugin-template \
  ../my-datalab-tool
cd ../my-datalab-tool
```

Copier runs `uv lock`. Review the generated `README.md` and `INSTALL.md`, then
replace the generic description and user instructions with the tool's actual
workflow and configuration before publishing it.

Two generated repositories show the intended result:

- [in-app Hello World example](https://github.com/Matgenix/datalab-in-app-tool-plugin-example)
- [standalone Hello World example](https://github.com/Matgenix/datalab-standalone-tool-plugin-example)

## Update a generated project

From the generated repository, run:

```shell
uvx copier update
```

Review and resolve the changes, rebuild an in-app frontend bundle if present,
and run the generated tests and pre-commit checks before committing.

Tool plugins are trusted extensions. Deployment administrators must review
Python code, dependencies, built artifacts, and release provenance before
installation or upgrade. Standalone services must also follow datalab's
[deployment boundary](https://docs.datalab-org.io/en/latest/deployment/#plugin-provided-standalone-services).
