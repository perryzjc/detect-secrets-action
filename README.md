# detect-secrets Action

detect-secrets Action is a powerful GitHub Action designed to scan your repository for any secrets that may have been accidentally committed, helping to protect your codebase and minimize the risk of sensitive information leakage. It is built upon the experimental version of [NASA-AMMOS/slim-detect-secrets](https://github.com/NASA-AMMOS/slim-detect-secrets/tree/exp) and will be updated to use the official [Yelp/detect-secrets](https://github.com/Yelp/detect-secrets) version once the customized plugins are merged.

For more information about `NASA-AMMOS/slim-detect-secrets`, please refer to the following links:
1. [NASA-AMMOS SLIM's documentation for detect-secrets usage](https://github.com/NASA-AMMOS/slim/blob/d20ee6134a0dc0e0dab11d2d2570e358ef7e4550/continuous-testing/starter-kits/README.md#detect-secrets)

## Usage

To integrate the Detect Secrets Action into your workflow, include the following configuration in your GitHub Actions workflow file:

[View the action.yml configuration](https://github.com/perryzjc/slim-detect-secrets-action/blob/main/action.yaml)

## Workflow Steps

The Detect Secrets Action follows these steps to ensure the security of your code:

1. **Checkout Code**: Utilizes GitHub's checkout action to access the repository. This is the code that will be scanned for secrets.
2. **Install Necessary Packages**: Deploys the required Python packages, including the experimental version of `slim-detect-secrets` and `jq`. These packages enable the primary functionality of the Action.
3. **Check Existence of .secrets.baseline**: Ensures the Action remains operational even if no baseline file exists yet. If the `.secrets.baseline` file is not found, the action creates an initial baseline file by scanning an empty directory.
4. **Scan Repository for Secrets**: In this step, the Action backs up the list of known secrets and scans the repository for any new secrets. The scan excludes files starting with '.secrets.' and '.git'. The 'compare_secrets' function is used to identify any differences between the known secrets and newly detected ones. If new secrets are detected, the build fails, and the user is guided to clean up the secrets using the `detect-secrets` tool.

## Support

Should you encounter any issues or require further assistance, feel free to create an issue in this repository. We value your feedback and will strive to provide timely support.

## Contributing

We warmly welcome contributions to the Detect Secrets Action. If you have an idea for an improvement or have discovered a bug, please fork this repository, make your changes, and submit a pull request. We appreciate your efforts in helping us make this action better!
