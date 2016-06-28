# Nuget Restore Custom Source

How to restore nuget packages from a custom source?

    nuget.exe restore C:\MyProject\MyProject.csproj -OutputDirectory C:\MyProject\packages -Source C:\MyProject\customNugetFeedPath

    NuGet Config files used:
    C:\Users\<User>\AppData\Roaming\NuGet\NuGet.Config

    Feeds used:
    C:\Users\<User>\AppData\Local\NuGet\Cache
    C:\Users\<User>\.nuget\packages\
    C:\MyProject\customNugetFeedPath

    Installed:
    1 package(s) to packages.config projects

How to force nuget to restore packages from a custom source, not the local cache?

    nuget.exe restore C:\MyProject\MyProject.csproj -OutputDirectory C:\MyProject\packages -Source C:\MyProject\customNugetFeedPath -NoCache

    NuGet Config files used:
    C:\Users\<User>\AppData\Roaming\NuGet\NuGet.Config

    Feeds used:
    C:\MyProject\customNugetFeedPath

    Installed:
    1 package(s) to packages.config projects

---
References:
- Nuget Documentation: [Command-line reference](https://docs.nuget.org/consume/command-line-reference#restore-command)