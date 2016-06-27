# MSBuild Copy Command Recursive Copy

1. You are not copying a *source folder* to a *destination folder*, but you are copying all the subdirectory and files contained in the source folder to destination folder.
2. You must use **%(RecursiveDir)** in destination to preserve folder structure

Example:

```XML
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <MySourceFiles Include="c:\MySourceTree\**\*.*"/>
    </ItemGroup>
    <Target Name="CopyFiles">
        <Copy
            SourceFiles="@(MySourceFiles)"
            DestinationFiles="c:\MyDestinationTree\%(RecursiveDir)%"/>
    </Target>
</Project>
```

# MSBuild Copy Command Skip Unchanged Files

Set `SkipUnchangedFiles` to `true` in `Copy` command

```XML
<Copy SourceFiles="@(Packages)" DestinationFolder="\\server\nuget\packages\" SkipUnchangedFiles="true" />  
```

References:
- MSDN Documentation: [Copy Task](https://msdn.microsoft.com/en-us/library/3e54c37h.aspx)
- Stackoverflow [question](http://stackoverflow.com/a/11449407/873234)
