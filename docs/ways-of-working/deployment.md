# Deployment

- GitHub Actions SHOULD be used as the preferred deployment tool
- External automation service such as Jenkins and CodeDeploy MUST NOT be used

<!--
Deployment pipelines SHOULD be in a separate repo that is set to private
Non-deployment pipelines MAY be kept with code or in a separate repo and made public
Reuse workflows where possible
Use checkpoints requiring a human to approve when appropriate.  Inform humans they need to do something via Slack.
-->
