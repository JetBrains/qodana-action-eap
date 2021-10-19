# Qodana - EAP Linters

![Qodana EAP version alert](resources/eap-alert.png)

**Qodana** is a code quality monitoring platform that allows you to evaluate the integrity of code you own, contract, or purchase. It brings into your CI/CD pipelines all the smart features you love in the JetBrains IDEs plus continues adding project-level checks like clone detection and license audit.

**Table of Contents**

<!-- toc -->

- [Qodana - EAP Linters](#qodana---eap-linters)
  - [Usage](#usage)
  - [Output Results](#output-results)
  - [License](#license)

<!-- tocstop -->


## Usage
* `linter` - Qodana Linter. Possible values: `qodana-jvm`, `qodana-php` and `qodana-python`
* `project-dir` - Project folder to inspect (default `${{ github.workspace }}`)
* `results-dir` - Save results to folder (default `${{ github.workspace }}/qodana`)
* `cache-dir` - Save cache to folder (default `/home/runner/work/_temp/_github_home/qodana-cache`)
* `inspected-dir` - Directory to be inspected. If not specified, the whole project is inspected by default
* `baseline` - Run in baseline mode. Provide the path to an exisitng SARIF report to be used in the baseline state calculation
* `baseline-include-absent` - Include in the output report the results from the baseline run that are absent in the current run (default `false`)
* `fail-threshold` - Set the number of problems that will serve as a quality gate. If this number is reached, the inspection run is terminated
* `save-html-report` - Generate HTML report (default `false`)
* `profile-name` - Name of a profile defined in project
* `profile-path` - Absolute path to the profile file
* `gradle-settings-path` - Provide path to gradle.properties file (for example: `/your/custom/path/gradle.properties`)
* `additional-volumes` - Additional volumes to mount to qodana docker image
* `additional-env-variables` - Additional environment variables to pass to qodana docker image

```yaml
- name: Qodana - JVM
  uses: JetBrains/qodana-jvm-action@v1.1.1-eap
  with:
    linter: qodana-jvm-android
```
 
```yaml
- name: Qodana - JVM
  uses: JetBrains/qodana-jvm-action@v1.1.1-eap
  with:
    linter: qodana-jvm
    fail-threshold: 10
    additional-env-variables: |
        IDEA_PROPERTIES='/data/project/idea.properties'
```

## Output Results

An example of the Qodana command-line summary output:
```
---- Qodana ----

2 problem(s) with Critical severity
 - Category(ies): General

1 problem(s) with Moderate severity
 - Category(ies): Code style

---- Problems reported: 3 ----
```

## License

Using Qodana docker image you agree to [JetBrains EAP user agreement](https://www.jetbrains.com/legal/docs/toolbox/user_eap/) and [JetBrains privacy policy](https://www.jetbrains.com/legal/docs/privacy/privacy/). The docker image includes an evaluation license which will expire in 30-day. Please ensure you pull a new image on time. 