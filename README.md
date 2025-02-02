dxutils
=======

Additional utilities to support vscode utilities

[![Version](https://img.shields.io/npm/v/dxutils.svg)](https://npmjs.org/package/dxutils)
[![CircleCI](https://circleci.com/gh/siddharatha/dxutils/tree/master.svg?style=shield)](https://circleci.com/gh/siddharatha/dxutils/tree/master)
[![Appveyor CI](https://ci.appveyor.com/api/projects/status/github/siddharatha/dxutils?branch=master&svg=true)](https://ci.appveyor.com/project/heroku/dxutils/branch/master)
[![Codecov](https://codecov.io/gh/siddharatha/dxutils/branch/master/graph/badge.svg)](https://codecov.io/gh/siddharatha/dxutils)
[![Greenkeeper](https://badges.greenkeeper.io/siddharatha/dxutils.svg)](https://greenkeeper.io/)
[![Known Vulnerabilities](https://snyk.io/test/github/siddharatha/dxutils/badge.svg)](https://snyk.io/test/github/siddharatha/dxutils)
[![Downloads/week](https://img.shields.io/npm/dw/dxutils.svg)](https://npmjs.org/package/dxutils)
[![License](https://img.shields.io/npm/l/dxutils.svg)](https://github.com/siddharatha/dxutils/blob/master/package.json)

<!-- toc -->
* [Debugging your plugin](#debugging-your-plugin)
<!-- tocstop -->
<!-- install -->
<!-- usage -->
```sh-session
$ npm install -g @siddharatha/dxutils
$ @siddharatha/dxutils COMMAND
running command...
$ @siddharatha/dxutils (-v|--version|version)
@siddharatha/dxutils/0.0.10 win32-x64 node-v10.15.3
$ @siddharatha/dxutils --help [COMMAND]
USAGE
  $ @siddharatha/dxutils COMMAND
...
```
<!-- usagestop -->
<!-- commands -->
* [`@siddharatha/dxutils <%= command.id %> [-d <integer>] [-a] [-c] [-u <string>] [--apiversion <string>] [--json] [--loglevel trace|debug|info|warn|error|fatal]`](#siddharathadxutils--commandid---d-integer--a--c--u-string---apiversion-string---json---loglevel-tracedebuginfowarnerrorfatal)
* [`@siddharatha/dxutils <%= command.id %> [-n <string>] [-a] [--json] [--loglevel trace|debug|info|warn|error|fatal]`](#siddharathadxutils--commandid---n-string--a---json---loglevel-tracedebuginfowarnerrorfatal)

## `@siddharatha/dxutils <%= command.id %> [-d <integer>] [-a] [-c] [-u <string>] [--apiversion <string>] [--json] [--loglevel trace|debug|info|warn|error|fatal]`

Pull changes from your connected org and generate an xml or autodownload metadata based on last modified date

```
USAGE
  $ @siddharatha/dxutils dxutils:pull [-d <integer>] [-a] [-c] [-u <string>] [--apiversion <string>] [--json] 
  [--loglevel trace|debug|info|warn|error|fatal]

OPTIONS
  -a, --autodownload                              AutoDownload the files using sfdx force:source:retrieve

  -c, --autoclean                                 Automatically clean the files that are downloaded with sfdx
                                                  dxutils:pull

  -d, --days=days                                 Please select the number of days we need to specify for getting org
                                                  details

  -u, --targetusername=targetusername             username or alias for the target org; overrides default target org

  --apiversion=apiversion                         override the api version used for api requests made by this command

  --json                                          format output as json

  --loglevel=(trace|debug|info|warn|error|fatal)  [default: warn] logging level for this command invocation

EXAMPLES
  $ sfdx dxutils:pull --targetusername myOrg@example.com
           Hello myname
           Calculating packages
  $ sfdx dxutils:pull -u myOrg@example.com -a
           Hello myname
           Calculating packages ...
           You have 130 metadata types in your org I can scan
```

_See code: [src\commands\dxutils\pull.ts](https://github.com/siddharatha/dxutils/blob/v0.0.10/src\commands\dxutils\pull.ts)_

## `@siddharatha/dxutils <%= command.id %> [-n <string>] [-a] [--json] [--loglevel trace|debug|info|warn|error|fatal]`

Pull changes from your connected org and generate an xml or autodownload metadata based on last modified date

```
USAGE
  $ @siddharatha/dxutils dxutils:starter [-n <string>] [-a] [--json] [--loglevel trace|debug|info|warn|error|fatal]

OPTIONS
  -a, --autodownload                              AutoDownload the files using sfdx force:source:retrieve
  -n, --projectname=projectname                   Please select the project name
  --json                                          format output as json
  --loglevel=(trace|debug|info|warn|error|fatal)  [default: warn] logging level for this command invocation

EXAMPLES
  $ sfdx dxutils:pull --targetusername myOrg@example.com
     Hello myname
     Calculating packages
  $ sfdx dxutils:pull -u myOrg@example.com -a
     Hello myname
     Calculating packages ...
     You have 130 metadata types in your org I can scan
```

_See code: [src\commands\dxutils\starter.ts](https://github.com/siddharatha/dxutils/blob/v0.0.10/src\commands\dxutils\starter.ts)_
<!-- commandsstop -->
<!-- debugging-your-plugin -->
# Debugging your plugin
We recommend using the Visual Studio Code (VS Code) IDE for your plugin development. Included in the `.vscode` directory of this plugin is a `launch.json` config file, which allows you to attach a debugger to the node process when running your commands.

To debug the `hello:org` command: 
1. Start the inspector
  
If you linked your plugin to the sfdx cli, call your command with the `dev-suspend` switch: 
```sh-session
$ sfdx hello:org -u myOrg@example.com --dev-suspend
```
  
Alternatively, to call your command using the `bin/run` script, set the `NODE_OPTIONS` environment variable to `--inspect-brk` when starting the debugger:
```sh-session
$ NODE_OPTIONS=--inspect-brk bin/run hello:org -u myOrg@example.com
```

2. Set some breakpoints in your command code
3. Click on the Debug icon in the Activity Bar on the side of VS Code to open up the Debug view.
4. In the upper left hand corner of VS Code, verify that the "Attach to Remote" launch configuration has been chosen.
5. Hit the green play button to the left of the "Attach to Remote" launch configuration window. The debugger should now be suspended on the first line of the program. 
6. Hit the green play button at the top middle of VS Code (this play button will be to the right of the play button that you clicked in step #5).
<br><img src=".images/vscodeScreenshot.png" width="480" height="278"><br>
Congrats, you are debugging!
