# SAFE Ionide Bug Reproduction


This repository was created by installing and using the SAFE template.

1) `dotnet new -i SAFE.Template`
2) `dotnet new SAFE`
3) `dotnet run`
4) `git add -A`
5) `git commit -m "..."`

To get the errors:
Have vscode with ionide and open the project `code .`

The Ionide errors I get in the F# output are:
```
[10:06:07.383 ERR] [LSP Server] HandleClientMessage - Error {"Code": -32601, "Message": "Method not found", "Data": null, "$type": "Error"} when handling notification {"Version": "2.0", "Method": "$/cancelRequest", "Params": {"Value": [[[]]], "$type": "Some"}, "$type": "Notification"}
[Error - 10:06:10] Request textDocument/hover failed.
  Message: Cached typecheck results not yet available
  Code: -32603
[10:06:11.917 ERR] [LSP Server] HandleClientMessage - Error {"Code": -32601, "Message": "Method not found", "Data": null, "$type": "Error"} when handling notification {"Version": "2.0", "Method": "$/cancelRequest", "Params": {"Value": [[[]]], "$type": "Some"}, "$type": "Notification"}
[10:06:11.934 WRN] [LSP] Errors while processing code action request for file:///c%3A/Projects/safeIonideBugRepro/src/Shared/Shared.fs with {"Diagnostics": [], "$type": "CodeActionContext"} at {"Start": {"Line": 0, "Character": 0, "DebuggerDisplay": "(0,0)", "$type": "Position"}, "End": {"Line": 0, "Character": 0, "DebuggerDisplay": "(0,0)", "$type": "Position"}, "DebuggerDisplay": "(0,0)-(0,0)", "$type": "Range"}: ["No deref found at that pos", "no typeof expr found", "Couldn't find symbolUse at (1, 9) in file c:/Projects/safeIonideBugRepro/src/Shared/Shared.fs"]
[10:06:13.314 WRN] [LSP] Errors while processing code action request for file:///c%3A/Projects/safeIonideBugRepro/src/Shared/Shared.fs with {"Diagnostics": [{"Range": {"Start": {"Line": 19, "Character": 6, "DebuggerDisplay": "(19,6)", "$type": "Position"}, "End": {"Line": 19, "Character": 14, "DebuggerDisplay": "(19,14)", "$type": "Position"}, "DebuggerDisplay": "(19,6)-(19,14)", "$type": "Range"}, "Severity": {"Value": "Information", "$type": "Some"}, "Code": {"Value": "FL0039", "$type": "Some"}, "CodeDescription": {"Value": {"Href": {"Value": "http://fsprojects.github.io/FSharpLint/how-tos/rules/FL0039.html", "$type": "Some"}, "$type": "CodeDescription"}, "$type": "Some"}, "Source": "F# Linter", "Message": "Consider changing `getTodos` to PascalCase.", "RelatedInformation": null, "Tags": null, "Data": {"Value": [[[[[[null, null, null]], [[null, null, null]], [[]]]], [[]]]], "$type": "Some"}, "DebuggerDisplay": "[Information] ((19,6)-(19,14)) Consider changing `getTodos` to PascalCase. (FL0039)", "$type": "Diagnostic"}], "$type": "CodeActionContext"} at {"Start": {"Line": 19, "Character": 6, "DebuggerDisplay": "(19,6)", "$type": "Position"}, "End": {"Line": 19, "Character": 14, "DebuggerDisplay": "(19,14)", "$type": "Position"}, "DebuggerDisplay": "(19,6)-(19,14)", "$type": "Range"}: ["No deref found at that pos", "no typeof expr found"]
```

If someone else manages to not get these errors it is likely that my vscode/ionide/paket installation is broken somehow.


## Environment

### My environment

```powershell
[environment]::OSVersion.Version

Major  Minor  Build  Revision
-----  -----  -----  --------
10     0      18363  0
```
sdk: 5.0.401
code: 1.60.2
7f6ab5485bbc008386c4386d08766667e155244e
x64
ionide: 5.7.3

# SAFE Template

This template can be used to generate a full-stack web application using the [SAFE Stack](https://safe-stack.github.io/). It was created using the dotnet [SAFE Template](https://safe-stack.github.io/docs/template-overview/). If you want to learn more about the template why not start with the [quick start](https://safe-stack.github.io/docs/quickstart/) guide?

## Install pre-requisites

You'll need to install the following pre-requisites in order to build SAFE applications

* [.NET Core SDK](https://www.microsoft.com/net/download) 5.0 or higher
* [Node LTS](https://nodejs.org/en/download/)

## Starting the application

Before you run the project **for the first time only** you must install dotnet "local tools" with this command:

```bash
dotnet tool restore
```

To concurrently run the server and the client components in watch mode use the following command:

```bash
dotnet run
```

Then open `http://localhost:8080` in your browser.

The build project in root directory contains a couple of different build targets. You can specify them after `--` (target name is case-insensitive).

To run concurrently server and client tests in watch mode (you can run this command in parallel to the previous one in new terminal):

```bash
dotnet run -- RunTests
```

Client tests are available under `http://localhost:8081` in your browser and server tests are running in watch mode in console.

Finally, there are `Bundle` and `Azure` targets that you can use to package your app and deploy to Azure, respectively:

```bash
dotnet run -- Bundle
dotnet run -- Azure
```

## SAFE Stack Documentation

If you want to know more about the full Azure Stack and all of it's components (including Azure) visit the official [SAFE documentation](https://safe-stack.github.io/docs/).

You will find more documentation about the used F# components at the following places:

* [Saturn](https://saturnframework.org/)
* [Fable](https://fable.io/docs/)
* [Elmish](https://elmish.github.io/elmish/)
