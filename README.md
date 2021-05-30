# FAV-BAR USEFUL PANEL

Adds a panel for accessing frequently used files, Internet addresses, programs, commands, snippets.

![Favorites Side Bar](preview/fav_bar__useful_panel.gif)

#### The integrated AutoFormat automatically formats a document as you save it:

|||
|-: | :- |
|||
[![](https://img.shields.io/static/v1?label=Auto%20Format&message=Prettier%20&color=ff69b4)](https://prettier.io/playground/ "playground")|[![](https://img.shields.io/static/v1?label=Prettier&message=Options%20&color=rgba(255,229,100,.8))](https://prettier.io/docs/en/options.html "options") |
|||


## Features

- Quick access to your favorite files
- Quick access to favorite URLs
- Fast launch of applications
- Quick access to your favorite files
- Quick access to favorite commands
- Setting icons for commands

## Extend features
- Added global Scope(sandbox) :
```json
{
    _, // lodash
    vscode,
    env.сontext,  // extension сontext
    env.prettier // options for integrated formatter
}
```
- Extend functional (runCommand):
- commands:
- - cmd
- - node
- - terminal
- - sel

## Extension Settings

The extension will initial demo configuration if none in .vscode/.favoritesSideBar.js.

```js
"favoritesSideBar":{ 
       commands": [
        {
            "label": "README",
            "description": "- read me",
            "icon": "zap",
            "command": "openFile",
            "arguments": ["README.MD"]
        }
    ]
}
```
List of available [icons](https://code.visualstudio.com/api/references/icons-in-labels#icon-listing "icons")

## Examples of using the plugin

### Editing code
```json
{
    "label": "lowercase ➜ UPPER CASE",
    "description": "",
    "icon": "debug-step-out",
    "command": "runCommand",
    "arguments": [
        "editor.action.transformToUppercase"
    ]
}
```

### Opening file

#### File in project

Settings for opening file in project

```json
{
    "label": "README",
    "description": "- read me",
    "command": "openFile",
    "arguments": ["README.MD"]
}
```
#### File is out project 

Settings for opening file in project

```json
{
    "label": "Hosts",
    "description": "Windows hosts file",
    "command": "openFile",
    "arguments": ["C:\\Windows\\System32\\drivers\\etc\\hosts", "external"]
}
```
### Run program

Settings for run program

#### Run CMD in OS Windows

```js

{
    label: "use | CMD1",

    description: "",
    icon: "link-external",
    command: "runCommand",
    arguments: [
    "cmd",
        `
            "C:\\Program Files (x86)\\Google\\Chrome\\Application\\chrome.exe"
            --user-data-dir="D:\\sets\\Chrome\\plnx.acc"
            https://observablehq.com/@observablehq/a-taste-of-observable?collection=@observablehq/overview
        `,
    ],
},

{
    label: "use | CMD2",

    description: "",
    icon: "link-external",
    command: "runCommand",
    arguments: [
    "cmd",
        '"C:\\Program Files (x86)\\Google\\Chrome\\Application\\chrome.exe"',
        '--user-data-dir="D:\\sets\\Chrome\\plnx.acc"',
        "https://observablehq.com/@observablehq/a-taste-of-observable?collection=@observablehq/overview",
    ],
}
```

#### Run Node javascript

```json
// eval:
{
    "label": "mm | bubbl.us",
    "description": "",
    "icon": "link-external",
    "command": "runCommand",
    "arguments": [
        "node",
        "-e",
        "require('./.scripts/clg')('hello','nodeJs')",
        "with",
        "evaluate"
    ]
}
// or for cmdFn:
{
    "label": "mm | bubbl.us",
    "description": "",
    "icon": "link-external",
    "command": "runCommand",
    "arguments": [
        "node",
        "./.scripts/cmdFn",
        "\"C:\\Program Files (x86)\\Google\\Chrome\\Application\\chrome.exe\"",
        "--user-data-dir=\"D:\\sets\\Chrome\\plnx.acc\"",
        "https://bubbl.us/12228588"
    ]
}
```

#### Run in Terminal
```js
// npm:

{
    label: "dev:spa",
    description: "",
    icon: "chevron-right",
    command: "runCommand",
    arguments: [
    "terminal",
    "quasar dev -m spa",
    ],
},
{
    label: "use | terminal1",
    description: "",
    icon: "link-external",
    command: "runCommand",
    arguments: [
    "terminal",
    `
        "C:\\Program Files (x86)\\Google\\Chrome\\Application\\chrome.exe"
        --user-data-dir="D:\\sets\\Chrome\\plnx.acc"
        https://observablehq.com/@observablehq/a-taste-of-observable?collection=@observablehq/overview
    `,
    ],
},
{
    label: "use | terminal2",
    description: "",
    icon: "link-external",
    command: "runCommand",
    arguments: [
    "terminal",
    'echo "Hello terminal world"',
    `node -e "console.log('%chello %s','color:yellow', 'node worldvscode');"`,
    'echo "Hello vscode world" && code -v',
    ],
},
{
    label: "deploy",
    description: "",
    icon: "chevron-right",
    command: "runCommand",
    arguments: [
    "terminal",
    "eslint src/**/*.{js,vue} --fix || exit 0",
    "node ./.scripts/zip",
    "node node_modules/vercel/dist --prod",
    ],
}
```

#### Run Chrome in OS Windows

```json
{
    "label": "Chrome",
    "description": "Run Chrome",
    "command": "run",
    "arguments": ["start chrome"]
}
```

#### Open folder in OS Windows

```json
{
    "label": "Windows",
    "description": "",
    "command": "run",
    "arguments": ["start explorer /n, C:\\Windows"]
}
```

### Open URL

Settings for open URL

```json
    {
      "label": "github.com",
      "description": "",
      "command": "runCommand",
      "arguments": ["vscode.open", "https://github.com"],
    }
```

### Run Command
Settings for running arbitrary commands

```json
{
  "label": "Zoom In",
  "description": "",
  "command": "runCommand",
  "arguments": ["editor.action.fontZoomIn"],
}
```
#### Open Search panel
command: workbench.action.findInFiles
arguments:
- query?: string;
-	isRegex?: boolean;
-	triggerSearch?: boolean;
-	filesToInclude?: string;
-	filesToExclude?: string;
-	isCaseSensitive?: boolean;

```json
{
  "label": "Find in files",
  "description": "",
  "command": "runCommand",
  "arguments": ["workbench.action.findInFiles", {"query": "SearchPattern", "triggerSearch": true}],
},
```

#### Insert text
Search and insert text by regexp pattern. Searches until the first match.

```json
{
  "label": "Replace",
  "description": "",
  "icon": "find-replace",
  "command": "insertNewCode",
  "arguments": ["ui/components/tableItem.ts", "<td className=\"col-date-time\">", "<div className=\"new\">NewText</div>", "before"],
}
```

#### Replace text
Search and replace text by regexp pattern. Searches until the first match.

```json
{
  "label": "Replace",
  "description": "",
  "icon": "find-replace",
  "command": "insertNewCode",
  "arguments": ["ui/components/tableItem.ts", "<td className=\"col-date-time\">", "<div className=\"WOW\"></div>", "replace"]
}
```

#### Replace All text
Search and replace text by regexp pattern. Searches all match.

```json
{
  "label": "ReplaceAll",
  "description": "",
  "icon": "find-replace",
  "command": "insertNewCode",
  "arguments": ["ui/components/tableItem.ts", "<td className=\"col-date-time\">", "<div className=\"WOW\"></div>", "replaceALL"]
}
```

### Settings for example:

Copy this snippet of settings to see the extension in action.

> EDIT

```js
{
    is: true,
    label: "EDIT",

    commands: [
      {
        label:
          "Toggle Line Comment",

        description: "",
        icon: "quote",
        command: "runCommand",
        arguments: [
          "editor.action.commentLine",
        ],
      },
      {
        label:
          "Toggle Block Comment",
        description: "",
        icon: "quote",
        command: "runCommand",
        arguments: [
          "editor.action.blockComment",
        ],
      },
      {
        label:
          "lowercase ➜ UPPER CASE",
        description: "",
        icon: "debug-step-out",
        command: "runCommand",
        arguments: [
          "editor.action.transformToUppercase",
        ],
      },
      {
        label:
          "UPPER CASE ➜ lowercase",
        description: "",
        icon: "debug-step-into",
        command: "runCommand",
        arguments: [
          "editor.action.transformToLowercase",
        ],
      },
      {
        label: "camelCase",
        description: "",
        icon: "ellipsis",
        command: "runCommand",
        arguments: [
          "sel",
          (_sel) =>
            _.camelCase(_sel),
        ],
      },
      {
        label: "snake_case",
        description: "",
        icon: "ellipsis",
        command: "runCommand",
        arguments: [
          "sel",
          (_sel) =>
            _.snakeCase(_sel),
        ],
      },
      {
        label: "kebab-case",
        description: "",
        icon: "ellipsis",
        command: "runCommand",
        arguments: [
          "sel",
          (_sel) =>
            _.kebabCase(_sel),
        ],
      },
      {
        label: "PascalCase",
        description: "",
        icon: "ellipsis",
        command: "runCommand",
        arguments: [
          "sel",
          (_sel) =>
            _.camelCase(_sel),
          (_sel) =>
            _.upperFirst(_sel),
        ],
      },
      {
        label:
          "UPPER_CASE_SNAKE_CASE",
        description: "",
        icon: "ellipsis",
        command: "runCommand",
        arguments: [
          "sel",
          (_sel) =>
            _.snakeCase(_sel),
          (_sel) =>
            _.toUpper(_sel),
        ],
      },
      {
        label: "path: \\ ➜ /",
        description: "",
        icon: "milestone",
        command: "runCommand",
        arguments: [
          "editor.action.insertSnippet",
          {
            snippet:
              "${TM_SELECTED_TEXT/([\\\\]{1,})/${1:+/}/g}",
          },
        ],
      },
      {
        label: "path: \\ ➜ \\\\",
        description: "",
        icon: "italic",
        command: "runCommand",
        arguments: [
          "editor.action.insertSnippet",
          {
            snippet:
              "${TM_SELECTED_TEXT/([\\\\]{1,})/${1:+\\\\\\\\}/g}",
          },
        ],
      },
      {
        label:
          "var ➜ prop={prop}",
        description: "",
        icon: "symbol-namespace",
        command: "runCommand",
        arguments: [
          "editor.action.insertSnippet",
          {
            snippet:
              "$TM_SELECTED_TEXT={$TM_SELECTED_TEXT}",
          },
        ],
      },
    ],
  }
```

> HOW TO

```js
{
    if: 1,
    label: "HOW TO ",
    commands: [
      {
        label: "CMD",
        description: "1",
        icon: "play",
        command: "runCommand",
        arguments: [
          "cmd",
          `
                  "C:\\Program Files (x86)\\Google\\Chrome\\Application\\chrome.exe"
                  --user-data-dir="D:\\sets\\Chrome\\plnx.acc"
                  https://observablehq.com/@observablehq/a-taste-of-observable?collection=@observablehq/overview
                `,
        ],
      },
      {
        id: "ID is needed only for [label,description] identify collision issues!",
        
        label: "CMD",
        description: "2",

        icon: "play",
        command: "runCommand",
        arguments: [
          "cmd",
          '"C:\\Program Files (x86)\\Google\\Chrome\\Application\\chrome.exe"',
          '--user-data-dir="D:\\sets\\Chrome\\plnx.acc"',
          "https://observablehq.com/@observablehq/a-taste-of-observable?collection=@observablehq/overview",
        ],
      },
      {
        label: "node 1",
        description:
          "error no module",

        icon: "beaker",
        command: "runCommand",
        arguments: [
          "node",
          "./node_modules/prettier/bin-prettier",
          "./<your>.js",
          "--write",
        ],
      },
      {
        label: "node 2",
        description: "server",

        icon: "beaker",
        command: "runCommand",
        arguments: [
          "node",
          "-e",
          `
            var http = require('http'),
               // open = require('open'),
                server;
            server = http.createServer(function (req, res) {
                      res.writeHead(200, {'Content-Type': 'text/plain'});
                      res.end('Hello World\\n');
                    });
            server.listen(1337, '127.0.0.1',function(){
                // console.log('Launching the browser on http://127.0.0.1:1337!');
                // open('http://127.0.0.1:1337');
            });
          `,
        ],
      },
      {
        label: "TERMINAL 1",

        description: "block",
        icon: "terminal",
        command: "runCommand",
        arguments: [
          "terminal",
          `
                  "C:\\Program Files (x86)\\Google\\Chrome\\Application\\chrome.exe"
                  --user-data-dir="D:\\sets\\Chrome\\plnx.acc"
                  https://observablehq.com/@observablehq/a-taste-of-observable?collection=@observablehq/overview
              `,
        ],
      },
      {
        label: "TERMINAL 2",

        description:
          "lines params",
        icon: "terminal",
        command: "runCommand",
        arguments: [
          "terminal",
          "cls",
          'echo "Hello terminal world"',
          `node -e "console.log('%chello %s','color:yellow', 'node','prettier : ${howTo.prettier()}');"`,
          `echo "Hello extension сontext" && echo "${howTo.сontext()}"`,
          `echo "Hello code.exe" && code -v`,
          `echo "Hello vscode" && echo "${howTo.vscode.version}"`,
        ],
      },
    ],
  }
```

## Release Notes

### 0.0.1 | 2021/06/22

- Added support for vscode.openFolder.
- Added the ability to move plugin settings into custom files.

More information in the [changelog](CHANGELOG.md "Changelog")
