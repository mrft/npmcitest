# NPM CI TEST

## About

We were having trouble with npm ci when run from a bitbucket pipeline, and in order to investigate what exactly was going on we created this tiny repo, just to check whether the prepare script from inside package.json would run properly.

Turns out it was related to a bug in npm 6 that would not execute the prepare script when run as root (which is what happens by default on most docker containers (and thus when running things from a bitbucket pipeline).

Here's some info that got us on the right track, so we could build a workaround in the bitbucket pipeline:
 * https://github.com/npm/npm/issues/17346
 * https://stackoverflow.com/questions/52766731/npm-v6-4-1-not-running-prepare-inside-docker
