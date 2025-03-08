# dotnet-toolset

A Docker image containing .NET and a small set of tools:

* git
* [docfx](https://www.nuget.org/packages/docfx)
* [trx2junit](https://www.nuget.org/packages/trx2junit)
* [dotnet-sonarscanner](https://www.nuget.org/packages/dotnet-sonarscanner)
* [dotCover](https://www.nuget.org/packages/JetBrains.dotCover.GlobalTool)

To run the image, call Docker as follows:

```
docker run -v <local-project-dir>:<project-dir> -w <project-dir> robtimus/dotnet-toolset
```

This will open a shell at `<project-dir>`, that allows you to execute your standard set of commands like `dotnet build` and `dotnet test`.

## SonarQube integration

See [.NET test coverage - dotCover](https://docs.sonarsource.com/sonarqube-server/latest/analyzing-source-code/test-coverage/dotnet-test-coverage/#dotcover) for an example. See [Using the SonarScanner for .NET](https://docs.sonarsource.com/sonarqube-server/latest/analyzing-source-code/scanners/dotnet/using/) for available options.
