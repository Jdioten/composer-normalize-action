# composer-normalize-action

[![Build Status](https://travis-ci.com/localheinz/composer-normalize-action.svg?branch=master)](https://travis-ci.com/localheinz/composer-normalize-action)

## What does this action do?

This action runs [`localheinz/composer-normalize`](https://github.com/localheinz/composer-normalize) with the `--dry-run` option.

That is, when you enable this action, the action will fail when a `composer.json` is pushed that is not valid or not already normalized.

## Usage

Define a workflow in `.github/workflows/ci.yml` (or add a job if you alread have defined workflows) like this:

```yaml
name: CI

on: push

jobs:
  composer-normalize:
    name: composer-normalize
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@master
      - name: Run localheinz/composer-normalize
        uses: docker://localheinz/composer-normalize-action
```

You can also use a specific tag, for example, `x.y.z` (otherwise, `latest` will be used).

```yaml
name: CI

on: push

jobs:
  composer-normalize:
    name: composer-normalize
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@master
      - name: Run localheinz/composer-normalize
        uses: docker://localheinz/composer-normalize-action:x.y.z
```

### Inputs

If you wish to specify the version of [`localheinz/composer-normalize`](https://github.com/localheinz/composer-normalize)  that should be used by the action, you can use the `composer-normalize-version` input parameter:

```yaml
name: CI

on: push

jobs:
  composer-normalize:
    name: composer-normalize
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@master
      - name: Run localheinz/composer-normalize
        uses: docker://localheinz/composer-normalize-action
        with:
          composer-normalize-version: '^1.3.0'
```

The value can be a range (for example, `^1.3.0`) or an exact version (for example, `1.2.0`).

:bulb: Also see [Automating your workflow with GitHub Actions](https://help.github.com/en/categories/automating-your-workflow-with-github-actions)

## Examples

To see this action in action, take a look at the following checks:

* https://github.com/localheinz/composer-normalize-action-example/pull/1/checks
* https://github.com/localheinz/composer-normalize-action-example/pull/2/checks
* https://github.com/localheinz/composer-normalize-action-example/pull/3/checks

## Docker

A docker image is automatically built and pushed to Docker Hub, see [`localheinz/composer-normalize-action`](https://cloud.docker.com/repository/docker/localheinz/composer-normalize-action).

You can execute the image by running

```
$ docker run --interactive --rm --tty --workdir=/app --volume ${PWD}:/app localheinz/composer-normalize-action
```

:bulb: Also see [Docker Docs: Docker run reference](https://docs.docker.com/engine/reference/run/).

## Changelog

Please have a look at [`CHANGELOG.md`](CHANGELOG.md).

## Contributing

Please have a look at [`CONTRIBUTING.md`](.github/CONTRIBUTING.md).

## Code of Conduct

Please have a look at [`CODE_OF_CONDUCT.md`](.github/CODE_OF_CONDUCT.md).

## License

This package is licensed using the MIT License.

## Credits

The implementation of this GitHub action is largely inspired by the work of [Oskar Stark](https://github.com/OskarStark) on the GitHub actions [`OskarStark/php-cs-fixer-ga`](https://github.com/OskarStark/php-cs-fixer-ga) and [`OskarStark/phpstan-ga`](https://github.com/OskarStark/phpstan-ga).
