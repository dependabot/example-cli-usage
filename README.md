<div align="center">
    <picture>
        <source media="(prefers-color-scheme: light)" srcset="https://user-images.githubusercontent.com/7659/174594540-5e29e523-396a-465b-9a6e-6cab5b15a568.svg">
        <source media="(prefers-color-scheme: dark)" srcset="https://user-images.githubusercontent.com/7659/174594559-0b3ddaa7-e75b-4f10-9dee-b51431a9fd4c.svg">
        <img src="https://user-images.githubusercontent.com/7659/174594540-5e29e523-396a-465b-9a6e-6cab5b15a568.svg" alt="Dependabot" width="336">
    </picture>
</div>

# Example Dependabot CLI Usage

This repo serves as an example of how to use Dependabot CLI for updates. It is intended as a starting point for advanced users to run a self-hosted version of Dependabot within their own projects.

If you're looking for a hassle-free Dependabot experience, check out the hosted [Dependabot Service](https://docs.github.com/en/github/administering-a-repository/about-dependabot-version-updates).

This repo uses an Action which downloads and runs Dependabot CLI. To run the Action you would go to [the Action in the Actions tab](https://github.com/dependabot/example-cli-usage/actions/workflows/example.yml), and run it.

To see what the results look like, go check out the Pull Requests.

## Implementation details

The Action is defined at [.github/workflows/example.yml](.github/workflows/example.yml).

It contains two jobs, the first downloads and runs Dependabot CLI. The inputs for the CLI runs are in [.github/dependabot](.github/dependabot). See the [Dependabot CLI repo](https://github.com/dependabot/cli) for more info on inputs such as credentials and groupings. 

The results are redirected to a file and uploaded as artifacts.

The second job downloads the artifact and creates PRs from it using the script [create.sh](create.sh).

The reason there are two jobs is Dependabot CLI should only run with read-only tokens as some ecosystem may execute arbitrary code. To achieve that in Actions we must use two jobs with `permissions` defined differently.

Also take a look at the [Dependabot Smoke Tests repo](https://github.com/dependabot/smoke-tests/tree/main/tests) for example inputs and expected outputs.

## Where can I go for help?

If you are having issues with the updates to a specific ecosystem, head over to [dependabot-core](https://github.com/dependabot/dependabot-core).

If there is a problem with running the Dependabot CLI, report that in the [CLI repo](https://github.com/dependabot/cli).

We do not provide direct support for the scripts and workflows in this repo, this is only to serve as an example.

