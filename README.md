# aseprite-auto

Automatically builds the latest [Aseprite](https://github.com/aseprite/aseprite) release using GitHub Actions.

[![Build and deploy Aseprite](https://github.com/the0cp/aseprite-auto/actions/workflows/build.yml/badge.svg?branch=main)](https://github.com/the0cp/aseprite-auto/actions/workflows/build.yml)

## Downloads

Prebuilt packages are available on the [Releases](https://github.com/the0cp/aseprite-auto/releases) page.

### Supported platforms

- [x] Windows
- [x] Linux
- [x] macOS

The workflow builds Aseprite from the upstream source and creates platform-specific release archives.

## How it works

The workflow runs automatically once a week and can also be started manually.

You can fork this repository and use GitHub Actions to build Aseprite in your own repository.

1. Click **Fork** at the top of this repository and create a fork under your GitHub account.

2. Open the **Actions** tab and enable the workflows if GitHub asks. Workflows and scheduled workflows in forked repositories may be disabled initially and need to be enabled manually.

The workflow will build Aseprite for all supported platforms.

## Change the build schedule

The schedule is configured in:

```text
.github/workflows/build.yml
```

The default schedule is:

```yaml
on:
  schedule:
    - cron: '17 9 * * 1'
      timezone: 'America/Los_Angeles'
```

This runs every Monday at **09:17 America/Los_Angeles time**.

You can change both the cron expression and timezone.

For example, to run every Friday at 18:30:

```yaml
on:
  schedule:
    - cron: '30 18 * * 5'
      timezone: 'America/Los_Angeles'
```

GitHub Actions uses standard POSIX cron syntax.

## Run a build manually

If you only want to run builds manually, remove the `schedule` section and keep:

```yaml
on:
  workflow_dispatch:
```

Then builds will only run when you manually select **Run workflow** from the Actions page.

## macOS

The macOS build is packaged as a native `Aseprite.app`.

Because the application is not code-signed or notarized, macOS may report that the downloaded application cannot be opened.

The macOS release archive includes a README with instructions for removing the quarantine attribute if necessary.

## Source

Aseprite source code: [https://github.com/aseprite/aseprite](https://github.com/aseprite/aseprite)

This repository only provides the automated GitHub Actions build workflow.
