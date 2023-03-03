# PSScriptAnalyzer Action
Github action for running PSScriptAnalyzer and use ConvertToSARIF to generate a SARIF file.

# Getting Started
To run this action add the step below in your GitHub Action:
```yaml
 - name: Run PSScriptAnalyzer
   uses: microsoft/psscriptanalyzer-action@v1.0
   with:
    path: .\
    recurse: true 
    output: results.sarif
```
The above yaml code scans all the code in your repository and outputs the results to `result.sarif` at the CWD.

# YAML
See the [input section](#Inputs) for more info about the inputs.
```yaml
 - name: Run PSScriptAnalyzer
   uses: psscriptanalyzer-action
   with:
    path:
    customRulePath: 
    recurseCustomRulePath: 
    excludeRule: 
    includeDefaultRules:
    includeRule:
    severity:
    recurse:
    suppressedOnly:
    fix:
    enableExit:
    settings:
    output:
    ignorePattern:
```

# Inputs
The inputs for the action. The inputs `output` and `ignorePattern` are action specific. The rest are mapped to the parameters of PSScriptAnalyzer.
Every input is of type string. 

To provide an array follow the format `'"value.fake", "value1.fake", ....'`
## path
Specifies the path to the scripts or module to be analyzed. Wildcard characters are supported. Default value is: `.\`. More info [here](https://github.com/PowerShell/PSScriptAnalyzer/blob/master/docs/Cmdlets/Invoke-ScriptAnalyzer.md#-path).
```yaml
with:
  path: .\
```
```yaml
with:
  path: .\src
```
## customRulePath
Specifies the path to the scripts or module to be analyzed. Wildcard characters are supported. More info [here](https://github.com/PowerShell/PSScriptAnalyzer/blob/master/docs/Cmdlets/Invoke-ScriptAnalyzer.md#-customrulepath).
```yaml
with:
  customRulePath: '".\customRule.ps1"'
```
```yaml
with:
  customRulePath: '".\customRule.ps1", "customRule2.ps1"'
```

## recurseCustomRulePath
Uses only the custom rules defined in the specified paths to the analysis. To still use the built-in rules, add the -IncludeDefaultRules switch. More info [here](https://github.com/PowerShell/PSScriptAnalyzer/blob/master/docs/Cmdlets/Invoke-ScriptAnalyzer.md#-recursecustomrulepath).
```yaml
with:
  recurseCustomRulePath: true
```
```yaml
with:
  recurseCustomRulePath: false
```

## excludeRule
Omits the specified rules from the Script Analyzer test. Wildcard characters are supported. More info [here](https://github.com/PowerShell/PSScriptAnalyzer/blob/master/docs/Cmdlets/Invoke-ScriptAnalyzer.md#-excluderule).
```yaml
with:
  # exclude one rule 
  excludeRule: '"PSAvoidLongLines"'
```
```yaml
with:
  # exclude multiple rules
  excludeRule: '"PSAvoidLongLines", "PSAlignAssignmentStatement"'
```

## includeDefaultRules
Uses only the custom rules defined in the specified paths to the analysis. To still use the built-in rules, add the -IncludeDefaultRules switch. More info [here](https://github.com/PowerShell/PSScriptAnalyzer/blob/master/docs/Cmdlets/Invoke-ScriptAnalyzer.md#-includedefaultrules).
```yaml
with:
  includeDefaultRules: true 
```
```yaml
with:
  includeDefaultRules: false
```

## includeRule
Runs only the specified rules in the Script Analyzer test. More info [here](https://github.com/PowerShell/PSScriptAnalyzer/blob/master/docs/Cmdlets/Invoke-ScriptAnalyzer.md#-includerule).
```yaml
with:
  # Include one rule
  includeRule: '"PSAvoidUsingInvokeExpression"'
```
```yaml
with:
  # Include multiple rules
  includeRule: '"PSAvoidUsingInvokeExpression", "PSAvoidUsingConvertToSecureStringWithPlainText"' 
```

## severity
After running Script Analyzer with all rules, this parameter selects rule violations with the specified severity. More info [here](https://github.com/PowerShell/PSScriptAnalyzer/blob/master/docs/Cmdlets/Invoke-ScriptAnalyzer.md#-severity).
```yaml
with:
  # Report only rule violations with error severity
  severity: '"Error"'
```
```yaml
with:
  # Report only rule violations with error and warning severity
  severity: '"Error", "Warning"'
```
## recurse
Script Analyzer on the files in the Path directory and all subdirectories recursively. More info [here](https://github.com/PowerShell/PSScriptAnalyzer/blob/master/docs/Cmdlets/Invoke-ScriptAnalyzer.md#-recurse).
```yaml
with:
  recurse: true
```
```yaml
with:
  recurse: false
```

## suppressedOnly
Returns rules that are suppressed, instead of analyzing the files in the path. More info [here](https://github.com/PowerShell/PSScriptAnalyzer/blob/master/docs/Cmdlets/Invoke-ScriptAnalyzer.md#-suppressedonly).
```yaml
with:
  suppressedOnly: true
```
```yaml
with:
  suppressedOnly: false
```

## fix
Fixes certain warnings which contain a fix in their DiagnosticRecord. More info [here](https://github.com/PowerShell/PSScriptAnalyzer/blob/master/docs/Cmdlets/Invoke-ScriptAnalyzer.md#-fix).
```yaml
with:
  fix: true
```
```yaml
with:
  fix: false
```

## enableExit
Exits PowerShell and returns an exit code equal to the number of error records. More info [here](https://github.com/PowerShell/PSScriptAnalyzer/blob/master/docs/Cmdlets/Invoke-ScriptAnalyzer.md#-enableexit).
```yaml
with:
  enableExit: true
```

```yaml
with:
  enableExit: false
```

## settings
File path that contains user profile or hash table for ScriptAnalyzer. Does not support passing a hashtable as an argument. More info [here](https://github.com/PowerShell/PSScriptAnalyzer/blob/master/docs/Cmdlets/Invoke-ScriptAnalyzer.md#-settings).
```yaml
with:
  settings: .\settings.psd1
```

## output
File path that defines where the SARIF output will be stored.
```yaml
with:
  output: results.sarif
```

## consoleLog
Log output directly to the console.
```yaml
consoleLog: true
```

## ignorePattern
Exclude specific files from the SARIF results. Uses regex pattern.
```yaml
with:
  # Any file or folder that have the name test will not be present in the SARIF file.
  ignorePattern: 'tests'
```

# Project

> This repo has been populated by an initial template to help get you started. Please
> make sure to update the content to build a great experience for community-building.

As the maintainer of this project, please make a few updates:

- Improving this README.MD file to provide a great experience
- Updating SUPPORT.MD with content about this project's support experience
- Understanding the security reporting process in SECURITY.MD
- Remove this section from the README

## Contributing

This project welcomes contributions and suggestions.  Most contributions require you to agree to a
Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us
the rights to use your contribution. For details, visit https://cla.opensource.microsoft.com.

When you submit a pull request, a CLA bot will automatically determine whether you need to provide
a CLA and decorate the PR appropriately (e.g., status check, comment). Simply follow the instructions
provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.

## Trademarks

This project may contain trademarks or logos for projects, products, or services. Authorized use of Microsoft 
trademarks or logos is subject to and must follow 
[Microsoft's Trademark & Brand Guidelines](https://www.microsoft.com/en-us/legal/intellectualproperty/trademarks/usage/general).
Use of Microsoft trademarks or logos in modified versions of this project must not cause confusion or imply Microsoft sponsorship.
Any use of third-party trademarks or logos are subject to those third-party's policies.
