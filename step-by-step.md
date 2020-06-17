# Bring your R Application Safely to Production. Collaborate, Deploy, Automate.

## Detailed workshop steps

### Initial setup

#### Fork from GitHub

Fork the starting-point repository https://github.com/miraisolutions/ShinyCICD-workshop/fork to your 
GitHub user account.


#### RStudio project setup

Clone the forked repo (https://github.com/&lt;user&gt;/ShinyCICD-workshop) as a new RStudio project
```
File > New Project... > Version Control > Git
```

#### Restore renv package dependencies

```r
renv::status()
renv::restore()
```

If you see a warning about
```
Project requested R version '4.0.z' but '3.6.x' is currently being used
```
this is not a big deal: align the R version in the lockfile via
```r
renv::snapshot()
```

#### Adapt the README to your forked repo

Diff: RStudio, compareWith, Sublime Merge

```r
renv::install("miraisolutions/comparewith")
```

Stage > Commit > Push

#### Package check suite

Build Pane: Check

Everything should be fine. If the check get stuck, it might be due to issues with renv on Windows. Possible to fall-back on renv-free setup and still follow the rest of the workshop: `renv::deactivate()`, then delete `renv.lock` and the `renv` folder.


#### Trigger a failure

TBD

### Automated checks on Travis

Setup Travis CI to automate package-level checks for continuous integration, triggered upon any push event (and pull requests) on the GitHub repo.

- Login at https://travis-ci.com/ (using your GitHub account)
- Activate authorization via GitHub Apps integration (see [Travis CI Tutorial](https://docs.travis-ci.com/user/tutorial)).
- Setup Travis for your project 
  ```r
  usethis::use_travis() # ext = "com" for usethis < 1.6.0
  ```
- This will bring you to https://travis-ci.com/account/repositories, from where you can "Manage repositories on GitHub" to make sure Travis CI has access to your repo
- Setup package dependencies `cache` and `install` for `renv`, and fix the R _major_._minor_ version
- Commit & push the generated `.travis.yaml` along with the `.Rbuildignore` file, as well as the updated README with the Travis badge.

This will trigger the first run on Travis, which can take ~10 minutes (future runs will be much faster thanks to caching caching). The run should be successful.


### New functionality

Change. Should sound innocuous.

Commit.

Push.

Failing Checks.

``` r
#' @param varaible The name of the [Old Faithful geyser][faithful] variable to
#'   use.
```

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
