# e-Rum2020 Workshop

This repository collects the information and material related to the e-Rum2020 workshop from Mirai Solutions.

## Bring your R Application Safely to Production. Collaborate, Deploy, Automate.

If you are looking for a hands-on introduction to CI/CD pipelines with a structured approach to collaborative development, this is the workshop you are looking for. To get your head around pull requests and branches, travis.yml or GitHub Actions jobs, workflows and processes for controlled development and deployments using free open source tools, all you need is your laptop (with R >= 3.6.x, ideally 4.0.x, RStudio and Git installed), a GitHub account and joining us.

In this hands-on 3-hours session we will:

- highlight the benefits of versioning your R code with Git and GitHub;
- show how to set up automated controls of your development on Travis CI, leveraging unit tests and R’s built-in package checks for Continuous Integration (CI);
- discuss effective branching models, pull requests and branch protection on GitHub, an approach especially important in a collaborative environment;
- demonstrate how to set up Continuous Deployment (CD) of packaged applications via Travis CI / GitHub Actions.

A simple R package with a Shiny app will be used as a running example to lay out a full workflow for stable, secure, reproducible deployments and releases.

This workshop is the natural continuation of "Is R ready for Production? Let’s develop a Professional Shiny Application!", however, attendance to the previous workshop is not a mandatory prerequisite.

**Keywords**: CI/CD, Git, GitHub, Travis CI, Actions

**When**: Saturday June 20th, 14.00-17.00 CEST

### Prerequisites

- A GitHub account is necessary for the workshop, also make sure you have its password ad hand.
- A local installation of R >= 3.6.x, ideally R 4.0.x
- A recent version of RStudio (>= 1.2) is recommended
- Package pre-installation via renv (**not yet available**):
    - Create a new RStudio project from https://github.com/miraisolutions/eRum2020Workshop-setup
      ```
      File > New Project... > Version Control > Git
      ```
    - Once in the new project, run at the R console
      ```r
      renv::restore()
      ```
- To make working with Git easier, you can optionally install additional tools we will mention in the workshop
    - [compareWith](https://github.com/miraisolutions/compareWith#readme) R package
    - [Sublime Merge](https://www.sublimemerge.com)
