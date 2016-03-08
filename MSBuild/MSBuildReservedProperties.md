# MSBuild Reserved Properties

MSBuild provides a set of predefined properties that store information about the project file and the MSBuild binaries. These properties are evaluated in the same manner as other MSBuild properties.

MSBuild uses the values in the following table to predefine reserved and well-known properties. Reserved properties cannot be overridden, but well-known properties can be overridden by using identically named environment properties, global properties, or properties that are declared in the project file.

| Property                | Example                                 | Description                                                                                          |
|-------------------------|-----------------------------------------|------------------------------------------------------------------------------------------------------|
| MSBuildBinPath          | C:\Windows\Microsoft.Net\Framework\v4.0.30319  | The absolute path of the folder where the MSBuild binaries that are currently being used are located |
| MSBuildToolsVersion     | 12.0                                    | The version of the MSBuild Toolset that is used to build the project.                                |
| MSBuildProgramFiles32   | C:\Program Files (x86)                  | The location of the 32-bit program folder                                                            |
| MSBuildProjectFullPath  | C:\MyRepository\MyProject\sample.csproj | The absolute path and complete file name of the project file, including the file name extension      |
| MSBuildProjectDirectory | C:\MyRepository\MyProject               | The absolute path of the directory where the project file is located                                 |
| MSBuildProjectFile      | sample.csproj                           | The complete file name of the project file, including the file name extension                        |


- MSDN link: [MSBuild Reserved and Well-Known Properties](https://msdn.microsoft.com/en-us/library/ms164309.aspx)
- MSBuild Engine on [GitHub](https://github.com/Microsoft/msbuild)