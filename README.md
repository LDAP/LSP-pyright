# LSP-pyright

Python support for Sublime's LSP plugin provided through [microsoft/pyright](https://github.com/microsoft/pyright).

## Installation

1. Make sure you have [Node.js](https://nodejs.org) installed and `node` is in your `$PATH`. The language server subprocess is a Node.js app. The minimum required Node.js version is 12.
2. Install [LSP](https://packagecontrol.io/packages/LSP) and
   [LSP-pyright](https://packagecontrol.io/packages/LSP-pyright) via Package Control.
3. Restart Sublime.
4. (Optional) Configure pyright for your `virtualenv`.

## Configuration

> **TIP**: It's recommended to additionally install the `LSP-json` package which provides validation and auto-complete for
`LSP-pyright` settings and the `pyrightconfig.json` configuration file.

Here are some ways to configure the package and the language server.

- From `Preferences > Package Settings > LSP > Servers > LSP-pyright`
- From the command palette `Preferences: LSP-pyright Settings`
- Project-specific configuration
  From the command palette run `Project: Edit Project` and add your settings in:

  ```js
  {
     "settings": {
        "LSP": {
           "LSP-pyright": {
              "settings": {
                 // Put your settings here
              }
           }
        }
     }
  }
  ```

- Through a `pyrightconfig.json` configuration file (check [settings documentation](https://github.com/microsoft/pyright/blob/master/docs/configuration.md))

### Virtual environments

If your project needs to run and be validated within a virtual environment, the `pyrightconfig.json` file must be present at the root of your project.

This configuration file, at a minimum, should define where your Python virtualenvs are located, as well as the name of the one to use for your project:

```json
{
    "venvPath": "/path/to/virtualenvs/",
    "venv": "myenv"
}
```

For example, if you have created a virtual environment inside the directory `.venv` within the project directory then you would use:

```json
{
    "venvPath": ".",
    "venv": ".venv"
}
```

Note that the `venv` option is only supported in the `pyrightconfig.json` file. The `venvPath` option can also be specified in your .sublime-project, in case you don't want to hard-code a system-specific path in a shared project.

Please see [Pyright Documentation](https://github.com/microsoft/pyright/blob/master/docs/configuration.md) for more options.
