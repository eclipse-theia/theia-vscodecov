# theia-vscodecov

Test VS Code API coverage against Theia for any VS Code extension

[![Open in Gitpod](https://gitpod.io/button/open-in-gitpod.svg)](https://gitpod.io/#https://github.com/theia-ide/theia-vscodecov)

## Install on your machine

Run in order to build and install locally:

    git clone https://github.com/theia-ide/theia-vscodecov.git
    cd theia-vscodecov
    npm install
    npm install -g .

## Use `theia-vscodecov`

Run in any extracted VS Code extension folder:

    npx theia-vscodecov

Run to learn more about the options:

    npx theia-vscodecov --help

## Install and use in devcontainer

You may want to avoid `theia-vscodecov` on your local machine.
In this case, you can use a devcontainer instead and avoid impacting your local machine.

### Installation

* Ensure you have the [requirements to run devcontainers](https://code.visualstudio.com/docs/remote/containers#_system-requirements)
  * Ensure you have [docker installed](https://code.visualstudio.com/docs/remote/containers#_installation)
  * Install [VS Code](https://code.visualstudio.com/)
  * Install the [Remote Development extension pack](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack)
* Open this repository in VS Code
* Run task `Remote-Containers: Reopen in Container` or click the notification the button in the notification to open the folder in the container

VS Code will open the repostory in a devcontainer and install `theia-vscodecov` in it.

### Running `theia-vscodecov`

`theia-vscodecov` is already installed in the devcontainer after its initialization, so you can just ...

* Copy and extract an extension into the workspace folder, e.g. into `<this-repo-folder>/vsx/gitlab-vscode-extension-main`
* Change into the extension folder, e.g. `cd vsx/gitlab-vscode-extension-main`
* Run `npx theia-vscodecov`

## Output

`theia-vscodecov` will output the manifest commands, used symbols, and used commands.
It compares those to the symbols and commands supported by Theia.
The Theia version to compare against is by default `latest` but can be configured in the `package.json` (see dependency `@theia/plugin`).
The missing symbols and commands are printed by `theia-vscodecov` as follows, e.g.:

```json
{
  ...,
  "missingSymbols": [
    "\"vscode\".Comment.thread",
    "\"vscode\".QuickPick.busy",
    "\"vscode\".QuickPick.hide",
    "\"vscode\".QuickPick.onDidHide",
    "\"vscode\".QuickPick.show",
    "\"vscode\".Selection.start",
    "\"vscode\".ThemeIcon.Folder",
    "\"vscode\".WorkspaceConfiguration.customQueries",
    "\"vscode\".WorkspaceConfiguration.featureFlags",
    "\"vscode\".WorkspaceConfiguration.instanceUrl",
    "\"vscode\".WorkspaceConfiguration.pipelineGitRemoteName",
    "\"vscode\".WorkspaceConfiguration.remoteName",
    "\"vscode\".WorkspaceConfiguration.repositories"
  ],
  "missingCommands": [
    "markdown.showPreview",
    "vscode.git",
    "vscode.openFolder"
  ]
}
```
