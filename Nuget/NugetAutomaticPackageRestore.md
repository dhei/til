# MSBuild-Integrated package restore vs. Automatic package restore in Nuget

### What is Automatic package restore in Visual Studio?
Beginning with NuGet 2.7, the NuGet Visual Studio extension integrates into Visual Studio's build events and restores missing packages when a build begins.

### How does it work?
1. On project or solution build, Visual Studio raises an event that a build is beginning within the solution.
2. NuGet responds to this event and checks for packages.config files included in the solution.
3. For each packages.config file found, its packages are enumerated and checked for existence in the solution's packages folder.
4. Any missing packages are downloaded from the user's configured (and enabled) package sources, respecting the order of the package sources.
5. As packages are downloaded, they are unzipped into the solution's packages folder.

---
### What is MSBuild-Integrated package restore?
Projects that use MSBuild-Integrated package restore typically contain a .nuget folder with three files and project references:

1. NuGet.Config
2. NuGet.exe
3. NuGet.targets

By default, the NuGet.Config file instructs NuGet to bypass adding package binaries to source control. Automatic Package Restore will honor this as long as you leave this file in place. When migrating to Automatic Package Restore, **all three Nuget files must be removed.** 

---
### How to migrate from MSBuild-Integrated to Automatic package restore (Git repository)
1. Delete .nuget folder from repository
2. Remove any references to Nuget.targets file in each .csproj in the solution such as the following:

```XML
<RestorePackages>true</RestorePackages>  
```

```XML
<Import Project="$(SolutionDir)\.nuget\nuget.targets" />  
```

```XML
<Target Name="EnsureNuGetPackageBuildImports" BeforeTargets="PrepareForBuild">  
    <PropertyGroup>
        <ErrorText>This project references NuGet package(s) that are missing on this computer. Enable NuGet Package Restore to download them.  For more information, see http://go.microsoft.com/fwlink/?LinkID=322105. The missing file is {0}.</ErrorText>
    </PropertyGroup>
    <Error Condition="!Exists('$(SolutionDir)\.nuget\NuGet.targets')" Text="$([System.String]::Format('$(ErrorText)', '$(SolutionDir)\.nuget\NuGet.targets'))" />
</Target>
``` 

---
References:
- Nuget Documentation: [Nuget Package Restore](https://docs.nuget.org/consume/package-restore)
- Nuget Documentation: [Migrating MSBuild-Integrated solutions to use Automatic Package Restore](https://docs.nuget.org/consume/package-restore/migrating-to-automatic-package-restore)