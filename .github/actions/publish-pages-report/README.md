Publish pages report
=====================

Publish an HTML report directory into a `gh-pages` branch and prune old reports by age.

Usage
-----

- Add this action to a workflow step (example in this repo):

```yaml
- name: Publish report to gh-pages
  id: publish
  uses: ./.github/actions/publish-pages-report
  with:
    report_path: test-report
    retention_days: 14
    reports_dir: reports
    pages_branch: gh-pages
```

Inputs
------

- `report_path` (required): Path in the caller workspace to the generated HTML report directory.
- `retention_days` (default: `30`): Delete reports older than this many days.
- `reports_dir` (default: `reports`): Directory inside the pages branch where reports are stored.
- `pages_branch` (default: `gh-pages`): Target branch in the repository to publish pages to.
- `artifact_name` (optional): If set, the action downloads this artifact into `report_path` instead of using local files.

Outputs
-------

- `report_url`: URL to the published report on the pages site.

Permissions
-----------

The workflow using this action must grant the runner a token with `contents: write` permission so the action can push to the pages branch (see the `permissions` block in the example workflow).
