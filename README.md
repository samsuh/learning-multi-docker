# Learning CI/CD Workflows.

The purpose of this project is to learn and sett up an automated cicd workflow.

## Description

It's a toy react frontend that takes in a fibonacci index, and returns the value at that index after refreshing (no hot reload).

The back end is a simple express server that does a trivial task that holds previously looked up indexes/values on a redis cache and stores the values long term in a postgres managed instance.

## CI/CD Workflow

### To the developer

- write code > push to github, and everything triggers on its own.

### Under the hood

github actions will rebuild everything, run tests, and update images on docker hub > store the built project on aws s3 > itll also redeploy to aws elasticache (aws redis) and aws postgres separately > deploy through IAM to an elastic beanstalk/EC2 instance.

### Notes

This rebuild/redeployment process takes about 4 minutes every time.
