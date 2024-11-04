# CS 161 Staff Website

New course website for SU23 developed by Peyrin (ping on Slack in the `#website` channel if there are any problems).


## Updating assignments

- Instructions for uploading discussion worksheets are in `_data/discussions.yml`.
- Instructions for releasing homeworks are in `_data/homeworks.yml`.
- Instructions for releasing projects are in `_data/projects.yml`.


## Building website

To update the website, just push to this repo, and the website will automatically build and update in around a minute. To keep the repo clean, **please tag your commit messages** by adding an assignment tag at the beginning. Examples:
- `[disc02] release`
- `[hw02] add electronic hw`
- `[proj1] fix typo in spec`

To build the website locally, [install Jekyll](https://jekyllrb.com/docs/installation/) and run `bundle exec jekyll serve`.

## [NEW] SU24: Beginning of semester setup
Refer to this [GitHub gist](https://gist.github.com/ashmchiu/797f80d9d4c1d674b9868c0a01b633c0) for information on setting up the website to deploy on inst.eecs.