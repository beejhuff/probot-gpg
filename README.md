# Probot GPG

> A GitHub App built with [probot](https://github.com/probot/probot) that enforces GPG signatures on Pull Requests

[![Build Status](https://travis-ci.org/jarrodldavis/probot-gpg.svg?branch=develop)](https://travis-ci.org/jarrodldavis/probot-gpg)
[![Coverage Status](https://coveralls.io/repos/github/jarrodldavis/probot-gpg/badge.svg)](https://coveralls.io/github/jarrodldavis/probot-gpg)
[![NSP Status](https://nodesecurity.io/orgs/jarrodldavis/projects/d841ad74-0b11-47f3-9216-bc6e48414bac/badge)](https://nodesecurity.io/orgs/jarrodldavis/projects/d841ad74-0b11-47f3-9216-bc6e48414bac)
[![Greenkeeper Status](https://badges.greenkeeper.io/jarrodldavis/probot-gpg.svg)](https://greenkeeper.io/)
[![npm](https://img.shields.io/npm/v/@jarrodldavis/probot-gpg.svg)](https://www.npmjs.com/package/@jarrodldavis/probot-gpg)

## Setup

```
# Install dependencies
npm install

# Run the bot
npm start
```

## Usage

[Configure this app](https://github.com/apps/probot-gpg) on your organizations and repositories. Be sure to enable [required status checks](https://help.github.com/articles/about-required-status-checks/) if you want to enforce GPG signatures on all pull requests.

See [docs/deploy.md](docs/deploy.md) if you would like to run your own instance of this plugin.


## How it works

Git supports [signing commits with GPG keys](https://git-scm.com/book/en/v2/Git-Tools-Signing-Your-Work) to verify commit authorship beyond the easy-to-forge [author](https://git-scm.com/docs/git-commit#git-commit---authorltauthorgt) field.

GitHub supports [verifying GPG signatures on commits](https://github.com/blog/2144-gpg-signature-verification) and has an excellent [series of help articles](https://help.github.com/articles/signing-commits-with-gpg/) for creating a GPG key, using it with `git` locally, and linking it to your GitHub account.

After installation, this app [checks all commits](https://developer.github.com/v3/repos/commits/#compare-two-commits) of new (or newly updated) pull requests for valid GPG signatures [according to the GitHub API](https://developer.github.com/changes/2016-04-04-git-signing-api-preview/). Note that for the status check to pass, _every_ contributor of a pull request must:
- set up a GPG key on their local machine
- sign _all_ of their commits in the pull request with that key
- link that key with their GitHub account

![GPG Status Check Success](https://user-images.githubusercontent.com/235875/30776187-bed103a8-a067-11e7-9ecc-5540c03114e1.png "GPG Status Check Success")

Otherwise, the app will set the status to `failed`.

![GPG Status Check Failed](https://user-images.githubusercontent.com/235875/30776885-3ab13158-a074-11e7-95df-8b6eb7d6b795.png "GPG Status Check Failed")

## Further reading

- [Git Tools - Signing Your Work](https://git-scm.com/book/en/v2/Git-Tools-Signing-Your-Work)
- [GitHub Help: Signing commits with GPG](https://help.github.com/articles/signing-commits-with-gpg/)
- [GitHub Help: Troubleshooting GPG](https://help.github.com/articles/troubleshooting-gpg/)
- [GitHub Blog: GPG signature verification](https://github.com/blog/2144-gpg-signature-verification)
- [GitHub Developer: Preview support for Git signing](https://developer.github.com/changes/2016-04-04-git-signing-api-preview/)
- [The GNU Privacy Guard](https://gnupg.org)
