# Bring your R Application Safely to Production. Collaborate, Deploy, Automate.

## Detailed workshop steps

### Fork from GitHub

### Version Control

Changes on README

Commit

Push

### Check package

```r
R CMD check
```

Fix documentation, rerun checks, see that passes

### Automated checks on Travis

Setup Travis CI to automate testing (and package-level checks in general) for continuous integration, triggered upon any push event on the GitHub repo. You need to first login at https://travis-ci.com/ (using your GitHub account)

- Setup Travis via `usethis::use_travis(ext = "com")`
- This will open your browser to allow you enabling access to the repo
- Commit & push the generated `.travis.yaml` file.

This will trigger the first run on Travis, which might take > 5 minutes (future runs will be much faster for caching). The run should be successful.


### New functionality

Change. Should sound innocuous.

Commit.

Push.

Failing Checks.

### GitFlow setup

After creating a `develop` branch (on GitHub)

- Pull the branch and switch to it locally (e.g. on the Git pane of RStudio)
- _Bump_ the package revision to include .9000: `usethis::use_dev_version()`
- Commit & push

Setup branch restrictions and agile setup as GitHub project (check slides).

### New feature 

From `develop`, create on GitHub a novel branch for the new feature `feature/1-xxxx`. Implement the feature in the local checkout of `feature/1-xxxxx`.

- Run tests and examples to see the outcome.
- Add a bullet about the new feature in the development section of `NEWS.md`.
- Commit & push.
- Create a pull request to `develop` on GitHub, get it approved and  merged.

### Deployment

### GitHub Actions Checks

### Continuous Deployment on Github Actions

#### Exercise: Continuous Deploymnet on Travis CI

### First release

We want to start using semantic versioning for the XXX package to track future updates and corresponding changes.

- Setup a changelog as `NEWS.md` file via `usethis::use_news_md()`, adding relevant information about this first version of the package.
- Define a new major version (1.0.0) via `usethis::use_version("major")`.
- Commit & push.
- Create release on GitHub as "v1.0.0", with title "XXX 1.0.0" and as content the corresponding `NEWS.md` section.

### New release 

We want to release the new feature(s) as a minor release with version 1.1.0

- Create release branch `release/v1.1.0` from `develop`.
- Update the package version via `usethis::use_version("minor")` locally on branch `release/v1.1.0`.
- Commit & push.
- Create a pull request to `master` on GitHub, get it approved and merged.
- Create release on GitHub as "v1.1.0", with title "xxxx 1.1.0" and content of the corresponding `NEWS.md` section.
- Go back to a development version `usethis::use_dev_version()` locally, still on branch `release/v1.1.0`.
- Commit & push.
- Create a pull request to `develop` on GitHub, get it approved and merged.
- Delete the release branch.
