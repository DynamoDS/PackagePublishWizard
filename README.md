# Package Publish Wizard

[![NPM Version](https://img.shields.io/npm/v/%40dynamods%2Fdynamo-pm-wizard)](https://www.npmjs.com/package/@dynamods/dynamo-pm-wizard)
[![Publish](https://github.com/DynamoDS/PackagePublishWizard/actions/workflows/npm-publish.yml/badge.svg)](https://github.com/DynamoDS/PackagePublishWizard/actions/workflows/npm-publish.yml)

This repository publishes [`@dynamods/dynamo-pm-wizard`](https://www.npmjs.com/package/@dynamods/dynamo-pm-wizard),
the package publishing wizard hosted in [Dynamo](https://github.com/DynamoDS/Dynamo)'s Package Manager.

**The source code is not here.** The wizard is developed in an internal Autodesk repository, because
it depends on internal Autodesk UI libraries. This repository exists only to publish the built
package to npmjs.org.

## How releases work

1. The internal CI builds a release of the wizard and packs it with `npm pack`.
2. The CI creates a GitHub release here (`v<version>`) and attaches the tarball.
3. The [Publish release](.github/workflows/npm-publish.yml) workflow downloads the tarball, checks
   that its name and version match the release, and publishes it to npmjs.org.

Nothing is built here, and the workflow publishes only what the internal CI attached.

### Dry run

When the `PUBLISH_DRY_RUN` repository variable is `true`, the workflow runs
`npm publish --dry-run` and nothing is published. It's used to check a release before publishing it.

### Re-running a publish

If publishing fails (for example, an expired `NPM_TOKEN`), fix the cause and run the workflow
manually (**Actions → Publish release → Run workflow**) with the release tag. Don't create a new
release for the same version.

## Using the package

```sh
npm install @dynamods/dynamo-pm-wizard
```

Dynamo consumes a pinned version at build time.

## License

The contents of this repository are licensed under the [MIT License](LICENSE).
