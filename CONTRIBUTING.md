# Contributing

Thanks for helping improve a Tey Labs package. Contributions are welcome through pull requests on the package's GitHub repository.

## Before you start

- **Questions and ideas:** start a discussion in the package's GitHub Discussions.
- **Bugs:** open an issue with the steps to reproduce it, the package version, and your PHP and Laravel versions.
- **Larger changes:** open a discussion or issue first, so we can agree on the approach before you spend time on it.
- **Security issues:** don't open a public issue. Follow the [security policy](https://github.com/teylabs/.github/blob/main/SECURITY.md).

## Pull requests

- Keep each pull request to one change, with tests that cover it.
- Match the existing code style: run `composer format` before committing.
- Make sure `composer test` and `composer analyse` pass.
- Update the README and `CHANGELOG.md` when behaviour changes for users.
- Write commit messages and the pull request description for public readers: say what changed and why.

## Development setup

```bash
git clone https://github.com/teylabs/<package>.git
cd <package>
composer install
composer test
```

See the package's README for anything specific to it. These packages follow the [Tey Labs package conventions](https://github.com/teylabs/.github/blob/main/CONVENTIONS.md).
