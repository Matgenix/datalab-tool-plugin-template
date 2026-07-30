# datalab tool plugin template

This is the Copier template for datalab tool plugins. It can
generate either:

- a standalone application that uses a short-lived *tool access token*; or
- a trusted *in-app tool* that renders inside datalab and uses the current
  *browser session* through the frontend SDK.

Generate a new plugin repository:

```shell
uvx copier copy https://github.com/Matgenix/datalab-tool-plugin-template \
  ../my-datalab-tool
```

The generated project includes the provider, Flask blueprint, package entry
point, and an example of the selected UI contract. In-app projects also include
a small Vite build that emits one classic JavaScript bundle and externalizes Vue
to datalab's host runtime. Either UI kind may open in the current tab or a new
tab.

For an in-app project, the template optionally declares one
*table-selection tool action*. The action can appear in the selected-items
dropdown of Samples, Inventory, Equipment, or items within a collection. When
this option is disabled, the generated provider and Vue component contain no
selection-specific code.

datalab automatically authenticates every route in the provider's declared
blueprint. Browser-session *authentication* is the default; service integrations
must declare service *authentication* and validate their machine client. The
starter UIs access user data through the normal datalab API, where existing
*item* and collection permission filters apply.

Both variants are trusted extensions. Deployment administrators must review the
generated Python package and its dependencies. For *in-app tools*, they must also
review the frontend source, dependency lockfile, and compiled JavaScript before
installing or upgrading the plugin. For separately hosted *standalone tools*,
they must additionally trust the remote operator, backend, *tool access token*
destination, and data retention and deletion policies.
