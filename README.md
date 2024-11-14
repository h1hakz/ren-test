# 32537

## Current behavior

Renovate is configured to monitor both all the files in a GitHub repository to identify and create pull requests (PRs) for dependency vulnerabilities. When Renovate identifies a vulnerability in both files for a specific dependency (e.g., Jinja2 < 3.1.4 with a known CVE), only the requirements.txt file is included in the generated PR. The poetry.lock file, though flagged as vulnerable in the logs, is not included in the PR upgrades section.

The logs confirm that poetry.lock has been identified as containing the vulnerable dependency, but no updates are applied to this file in the resulting PR. This issue persists even though enabledManagers includes both poetry and pip_requirements.

## Expected behavior

When vulnerabilities are detected in dependencies across both requirements.txt and poetry.lock, Renovate should create a PR that includes updates for both files, ensuring that all vulnerable dependencies are addressed in a single PR. This behavior would ensure that vulnerabilities in poetry.lock are patched alongside requirements.txt in each PR, as defined in the configuration.

## Link to the Renovate issue or Discussion

(https://github.com/renovatebot/renovate/discussions/32537)
