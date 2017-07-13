# POS docs

## Setting up your environment

To get your mkdocs environment configured; install the following:
* chocolatey
* python:

        cinst python -y
* mkdocs:

        pip install mkdocs

Note: you might need to ensure cinst, python, & pip are all in your path.

## Updating the documentation

The posdocs repository has all the documentation in markdown format. Commits to the posdocs repo will automatically publish (via appveyor) the static site content to AWS S3
http://posdocs.oxipay.com.au.s3-website-ap-southeast-2.amazonaws.com

To update the documentation the following steps need to be done.

* clone the repository and cd into it:

        git clone git@github.com:oxipay/posdocs.git
        cd oxidocs

* You'll need to create a branch for your changes as master is protected.

        git checkout -b new-thing
* Make your changes to the documentation.
* Run the web-application locally:

        mkdocs serve
* Commit your changes and push your branch back up to GitHub.
* Submit a PR.
* When the PR is merged into the master branch, the Appveyor build will automatically push the generated content up to AWS S3

test
test
