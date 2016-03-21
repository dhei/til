# Whitespace in MSBuild Exec command task

MSBuild [Exec Task](https://msdn.microsoft.com/en-us/library/x8zx72cd.aspx) can run specified program or command with specified arguemnts.

Note that whitespaces are **allowed** in `WorkingDirectory` but not `Command`.

```XML
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="VisualStudioDeveloperCommandPrompt">
        <Exec Command="VsDevCmd.bat" WorkingDirectory="C:\Program Files (x86)\Microsoft Visual Studio 12.0\Common7\Tools" />
    </Target>
</Project>
```

---
Reference:
- MSBuild [Exec Task](https://msdn.microsoft.com/en-us/library/x8zx72cd.aspx)