# Code-Analysis
Repository for holding code analysis rules and configuration for StyleCop & other Roslyn Analyzers.

## How to add to new Cedita Projects
1. Right click the Solution and add Cedita.ruleset and stylecop.json as Solution-level items for global inclusion.
2. Edit the .csproj of each project file. For .NET Core, simply Right Click -> Edit X.csproj. For other libraries, Right Click -> Unload Project and then Right Click -> Edit X.csproj.
3. Add the Code Analysis Ruleset under the initial `<PropertyGroup>`:
    ```
    <CodeAnalysisRuleSet>..\Cedita.ruleset</CodeAnalysisRuleSet>
    ```
4. Add the additional file link under either an existing `<ItemGroup>` or create a new one:
    ```
    <ItemGroup>
        <AdditionalFiles Include="..\stylecop.json" Link="stylecop.json" />
    </ItemGroup>
    ```
5. (for non .NET Core) Right Click -> Reload Solution
6. Add `StyleCop.Analyzers` from NuGet to each project in Solution:
    ```
    Install-Package StyleCop.Analyzers -pre
    ```
7. (Optional) Add `AsyncUsageAnalyzers` from NuGet to each project in Solution:
    ```
    Install-Package AsyncUsageAnalyzers -Pre
    ```
