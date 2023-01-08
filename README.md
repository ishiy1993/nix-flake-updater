# nix-flake-updater
A reusable workflow for updating flake.lock

## Note
If you need a custom action, use [DeterminateSystems/update-flake-lock](https://github.com/DeterminateSystems/update-flake-lock).

## Usage
Minimum example:

```yaml
jobs:
  call-nix-flake-updater:
    uses: ishiy1993/nix-flake-updater/.github/workflows/nix-flake-updater.yml@v0
    with:
      base_branch: main
```

Other options:

```yaml
jobs:
  call-nix-flake-updater:
    uses: ishiy1993/nix-flake-updater/.github/workflows/nix-flake-updater.yml@v0
    with:
      base_branch: main
      pr_branch_prefix: 'bot/'
      pr_title: 'Update flake.lock by nix-flake-updater'
      reviewer: <your github id>
      timezone: JST-9
```

## What nix-flake-updater does

1. checkout by [actions/checkout](https://github.com/actions/checkout).
2. install nix by [cachix/install-nix-action](https://github.com/cachix/install-nix-action).
3. `nix flake update --commit-lock-file`.
4. create a PR by [gh pr create](https://cli.github.com/manual/gh_pr_create).

**If there are no updates, no PR will be created.**
The commit and PR author is `github-actions[bot]`.
