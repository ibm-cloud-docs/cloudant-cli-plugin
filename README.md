# cloudant-cli-plugin

Documentation repository for cloudant-cli-plugin

## Staging links:

* content of the `draft` branch is on https://test.cloud.ibm.com/docs-draft/Cloudant-cli-plugin
* content of the `review` branch is on https://test.cloud.ibm.com/docs/Cloudant-cli-plugin

## Production links:

* content of the `publish` branch is on https://cloud.ibm.com/docs/Cloudant-cli-plugin

## Slack channels

To follow the doc build status on Slack channel: #docs-cloudant-cli-plugin

To check Acrolinx and output branch notifications: #cloudant-integrations-doc-notification

## Quality Dashboard

To check the Content Quality Dashboard filter for `cloudant-cli-plugin`:

* production: https://cqd.console.test.cloud.ibm.com/docs/production
* staging: https://cqd.console.test.cloud.ibm.com/docs/staging

## Merge info

The default branch is `review`.
PRs should use `review` as base.

You can add content via a custom branch or the `draft` branch
and then opening the PR to `review`.

Changes merge to review via "rebase" or "squash".
Merge commits are not permitted to make it easier to track
the delta as changes flow between the branches.

To preview changes before staging use the `draft` branch.

Be aware that new tags of the CLI plugin automatically
update the `draft` branch and open a PR from `draft` to `review`.

After changes in `review` are verified as OK in staging then
a tag is created on the `review` branch to push the commits
automatically to `publish` and make the docs live in production.
