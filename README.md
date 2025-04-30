# Data C104 Course Website

[![pages-build-deployment](https://github.com/ds-104/datac104-website/actions/workflows/pages/pages-build-deployment/badge.svg)](https://github.com/ds-104/datac104-website/actions/workflows/pages/pages-build-deployment)
[![Run all page tests](https://github.com/ds-104/datac104-website/actions/workflows/rspec.yml/badge.svg)](https://github.com/ds-104/datac104-website/actions/workflows/rspec.yml)

Dates are for Fall 2024.

Website is using the [CS 161 Template Website](https://github.com/cs161-staff/course-site-template) developed by Peyrin 

## Installation

Prerequisites:

- You have everything that [Jekyll requires](https://jekyllrb.com/docs/installation/)
- You have installed [Bundler](https://bundler.io/): `gem install jekyll bundler`

After cloning this repository and navigating into the directory, run the following command to install dependencies
```
cd YOUR_REPO
bundle install
```

## Usage

To run the site locally, run:

```
bundle exec jekyll serve
```

Note that if you alter `_config.yml`, you will need to rerun the above command to see the changes reflected.

## Deployment

This site is deployed via a [GitHub Action Workflow](.github/workflows/jekyll.yml). For more information see [GitHub Pages](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/about-github-pages-and-jekyll).

