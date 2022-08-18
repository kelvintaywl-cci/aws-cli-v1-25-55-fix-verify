# aws-cli-v1-25-55-fix-verify
Confirming the fix on AWS CLI as of v1.25.55

## Brief

As of AWS CLI v1.25.54, there was a bug introduced.
Specifically, users are not able to configure a profile.

The error seen would be something like:

```
The config profile (a_new_profile) could not be found
```

For more info, you can refer to this report: https://github.com/aws/aws-cli/issues/7199

Some CircleCI users are impacted because they are likely using [CircleCI's AWS CLI orb](https://circleci.com/developer/orbs/orb/circleci/aws-cli) to install and setup their AWS CLI config.
In particular, the `aws-cli/setup` command relies on the `aws-cli/install` command to install AWS CLI.
Right now, the `aws-cli/install` command will simply install the latest CLI version.

See https://github.com/CircleCI-Public/aws-cli-orb/blob/master/src/scripts/install.sh


## Resolution

It appears AWS has fixed this issue, as per v1.25.55:
https://github.com/aws/aws-cli/blob/develop/CHANGELOG.rst#12555

This repo thus runs a CircleCI build to verify AWS CLI version, and check that a AWS profile is set up correctly.
