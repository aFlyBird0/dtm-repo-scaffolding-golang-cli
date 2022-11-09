# dtm-scaffolding-golang

This repo contains templates used by DevStream plugin "repo-scaffolding" (thereafter: the plugin).

This repo isn't intended to be used directly without DevStream. It should only be consumed by the plugin automatically.

The plugin (together with this repo of templates) can create a repo in GitHub and set up the project layout and initialize the reop with necessary files that are typical for a Go cli app. The followings can be created automatically:

- a Go cli app example (generated by [`cobra-cli init`](https://github.com/spf13/cobra-cli/blob/main/README.md))
- [GoReleaser-Actions workflow](https://github.com/goreleaser/goreleaser-action)(Once you push a tag, it will build and release your app automatically)
- `.gitignore`, generated by [Toptal | gitignore.io](https://www.toptal.com/developers/gitignore/api/go,vim,macos,visualstudiocode) with minimum changes
- Makefile, with install/dev/build/clean

## Usage

- Render all files using go template whose name end with `.tpl` suffix.
- Files whose name don't end with `.tpl` extension don't need to be rendered.
- subdirectory "helm/**_app_name_**" (the **_app_name_** part) should be rendered with `AppName`
- subdicrectory "cmd/**_app_name_**" (the **_app_name_** part) should be rendered with `AppName`

Example of required parameters to render these templates:

```yaml
AppName: my-hello-world
Repo:
  Owner: ironcore864
  Name: my-hello-world
ImageRepo: ironcore864/my-hello-world # dockerhub
```
