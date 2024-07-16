# CI/CD GitLab 

## Creating a Pipeline using gitlab

![Alt text](m1_ci_cd_gitlab/images/creating-pipeline.png)

## Adding a yaml file 

![Alt text](m1_ci_cd_gitlab/images/yaml-file.png)

## Writing a bash script

![Alt text](m1_ci_cd_gitlab/images/creating-file.png)

## Executing a pipeline

![Alt text](m1_ci_cd_gitlab/images/pipe-line-job.png)

![Alt text](m1_ci_cd_gitlab/images/gitlab-execution.png)

## Creating jobs and stages

![Alt text](m1_ci_cd_gitlab/images/pipeline-stages.png)

## Adding Artifacts

![Alt text](m1_ci_cd_gitlab/images/artifacts.png)

## Running Pipeline

![Alt text](m1_ci_cd_gitlab/images/finish-results.png)

## Pipeline execution result

![Alt text](m1_ci_cd_gitlab/images/test-results.png)

![Alt text](m1_ci_cd_gitlab/images/test-result2.png)


# M2 CI/CD WORKFLOW

## Part-1 Creating Static Website

    `node --version`
    `npm --version`
    `npm i -g gatsby-cli`
    `gatsby --version`
    `npm init gatsby`
    `cd website-folder/`
    `npm run develop`

![Alt text](m2_ci_cd_workflow/images/static-website.png)

### Building the project locally (build step)

![Alt text](m2_ci_cd_workflow/images/build-step.png)


### Creating yaml file

![Alt text](m2_ci_cd_workflow/images/creating-yaml.png)

### Executing pipeline and adding artifacts

![Alt text](m2_ci_cd_workflow/images/uploading-artifacts.png)

![Alt text](m2_ci_cd_workflow/images/browse-artifacts.png)

## Part-2 Adding a Test Stage 

### Creating Two test (Success and Fail Test)

![Alt text](m2_ci_cd_workflow/images/test-stage.png)


![Alt text](m2_ci_cd_workflow/images/test-stage-pipeline.png)

![Alt text](m2_ci_cd_workflow/images/failed-status.png)

### Creating Two jobs for test / Running jobs in parallel

![Alt text](m2_ci_cd_workflow/images/second-job-test.png)

![Alt text](m2_ci_cd_workflow/images/running-tests-parallel.png)

#### gatsby serve issue running without release

![Alt text](m2_ci_cd_workflow/images/gatsby-serve.png)

#### gatsby serve issue running and release task

![Alt text](m2_ci_cd_workflow/images/gatsby-serve-release.png)

![Alt text](m2_ci_cd_workflow/images/pipelines-after-release.png)

### Deployment using `surge.sh`

    `npm install --global surge`
    `surge`


![Alt text](m2_ci_cd_workflow/images/surge-website.png)


### Environment Variables for Managing secrets

    `surge token`
    
- step-1: Go to setting side bar

- step-2: CI/CD

- step-3: Expand variable

- step-4: Click Add Variable

- step-5: Type SURGE_LOGIN name at the key field , email at the value field, uncheck box Protect variable and click Add variable button

- step-6: Click Add Variable again to add the surge token

- step-7: Type SURGE_TOKEN name at the key field , token at the value field, uncheck box Protect variable, check box Mask Variable and click Add variable button

## Part-3 Deploying Project using Gitlab CI


![Alt text](m2_ci_cd_workflow/images/stages-three.png)

![Alt text](m2_ci_cd_workflow/images/deploy-stage.png)

![Alt text](m2_ci_cd_workflow/images/deploy-pipeline.png)

### Published website using surge.sh Automatically through Gitlab CI

![Alt text](m2_ci_cd_workflow/images/surge-published.png)


## Task extend the pipeline and add a new stage

1 - add a new stage called "deployment tests".

![Alt text](m2_ci_cd_workflow/images/deployment-test-new-stage.png)

2 - create a new job called "test deployment"

3 - download the first page of the website and search for a specific string (you can use the curl command)

![Alt text](m2_ci_cd_workflow/images/deployment-tests-stage.png)

![Alt text](m2_ci_cd_workflow/images/deployment-tests-pipeline.png)


![Alt text](m2_ci_cd_workflow/images/deployment-tests-log.png)

### Let's find a way to improve the execution time.

4 - Use the Docker alpine image for this job.

![Alt text](m2_ci_cd_workflow/images/alpine-image.png)

![Alt text](m2_ci_cd_workflow/images/update-alpine-log.png)