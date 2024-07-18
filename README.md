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

    npm install --global surge
    surge


![Alt text](m2_ci_cd_workflow/images/surge-website.png)


### Environment Variables for Managing secrets

    surge token
    
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

# M3 Gitlab CI Fundamentals

## [Predefined environment variables](https://docs.gitlab.com/ee/ci/variables/predefined_variables.html)


- To create a variable that give the first eight characters of CI_COMMIT_SHA

![Alt text](m3_gitlab_ci_fundamentals/images/environment-variable.png)

- In index.js file add environment variable

![Alt text](m3_gitlab_ci_fundamentals/images/version-variable.png)

- version number at the build stage log info

![Alt text](m3_gitlab_ci_fundamentals/images/version-number.png)

- test deployment of the version on the website

![Alt text](m3_gitlab_ci_fundamentals/images/test-version.png)

## Optimize the build speed using Cache

![Alt text](m3_gitlab_ci_fundamentals/images/cache.png)


### Disabling the cache for the jobs that do not need it

    `cache:{}`


![Alt text](m3_gitlab_ci_fundamentals/images/disable-cache.png)

### Configuring the global cache by specifying the pull policy

![Alt text](m3_gitlab_ci_fundamentals/images/cache-policy.png)

#### Task: create a job that runs only once per day and updates the cache. The job will not need to download the caches (pull). It only needs to create new caches (push).

#### 1 - create a stage called "cache"

![Alt text](m3_gitlab_ci_fundamentals/images/stage-cache.png)

#### 2 - create a job called "update cache"
#### 3 - make sure the job does runs the command npm install (to install all dependencies)
#### 4 - add the following cache policy to the job: policy: push. Note that you will need to define the entire cache configuration (as you have done globally). You can not  override only the policy.
#### 5 - make sure the "update cache" job only runs when the pipeline is triggered by a schedule

![Alt text](m3_gitlab_ci_fundamentals/images/update-cache.png)

#### 6 - make sure that all other jobs DO NOT RUN when the pipeline is triggered by a schedule

![Alt text](m3_gitlab_ci_fundamentals/images/staging-cache.png)

#### 7 - create a new scheduled pipeline run and make it run once per day

#### 8 - manually run the scheduled pipeline and inspect the pipeline (only one job should be displayed)

![Alt text](m3_gitlab_ci_fundamentals/images/cache-schedule.png)

#### 8 - manually the pipeline (the "update cache" job should not appear in the pipeline)

![Alt text](m3_gitlab_ci_fundamentals/images/cache-schedule-staging.png)

### Deployment environments or staging

![Alt text](m3_gitlab_ci_fundamentals/images/deploy-staging.png)

![Alt text](m3_gitlab_ci_fundamentals/images/deploy-staging-pipeline.png)

### Defining Variables

![Alt text](m3_gitlab_ci_fundamentals/images/variables-1.png)

![Alt text](m3_gitlab_ci_fundamentals/images/variables-2.png)

### Manual Deployments / Manually Triggering job

![Alt text](m3_gitlab_ci_fundamentals/images/manual-deployment.png)

### Merge requests using branches

#### Jobs that run on the main branch

      only
        - master

![Alt text](m3_gitlab_ci_fundamentals/images/only-master-branch.png)

#### Create Branch 

- On the left sidebar, select Search or go to and find your project.
- Select Code > Branches.
- In the upper-right corner, select New branch.
- Enter a Branch name.
- In Create from, select the base of your branch: an existing branch, an existing tag, or a commit SHA.
- Select Create branch.

#### Develop and main branches

    git checkout main
    git checkout -b develop
    git push -u origin develop
    # Creating a feature branch
    git checkout -b feature_branch
    # work happens on feature branch
    # Finishing a feature branch
    git checkout develop
    git merge feature_branch
    git checkout main
    git merge develop
    git branch -d feature_branch

#### When using the git-flow extension library, executing git flow init on an existing repo will create the develop branch:

    git checkout main
    git flow init
    # Creating a feature branch
    git flow feature start feature_branch
    # Finishing a feature branch
    git flow feature finish feature_branch


#### see the status of the pipeline for a specific branch

![Alt text](m3_gitlab_ci_fundamentals/images/branch-status.png)

#### Protecting main branch from random push

- Go to settings -> repository -> Protected branch

![Alt text](m3_gitlab_ci_fundamentals/images/protect-branch.png)

#### Merge request

- Go to settings -> merge requests -> Fast-forward merge && pipeline must succeed

- merge request status

![Alt text](m3_gitlab_ci_fundamentals/images/merge-request-status.png)

#### Dynamic Environment - reviewing the changes on each branch

![Alt text](m3_gitlab_ci_fundamentals/images/deploy-review.png)

- branch pipeline status on feature branch

![Alt text](m3_gitlab_ci_fundamentals/images/feature-branch-pipeline.png)

- review branch pipeline status on feature branch

![Alt text](m3_gitlab_ci_fundamentals/images/review-branch-status.png)

#### Destroy Environments (Clean up after merge request)

![Alt text](m3_gitlab_ci_fundamentals/images/stop-review.png)

![Alt text](m3_gitlab_ci_fundamentals/images/stop-review-status.png)

![Alt text](m3_gitlab_ci_fundamentals/images/merged-branch-status.png)


#### Disabling a job by aadding a "." before the stages

![Alt text](m3_gitlab_ci_fundamentals/images/disable-job.png)

### Creating job template

![Alt text](m3_gitlab_ci_fundamentals/images/job-template.png)

## M5_Using_Gitlab_CI_to_build_and_deploy_a_java_application_to_AWS_Elastic_Beanstalk

#### Build Stage - Build a java application with Gitlab CI

![Alt text](m5_Using_Gitlab_CI_to_build/images/build-stage.png)

#### Test Stage - Add smoke test

![Alt text](m5_Using_Gitlab_CI_to_build/images/smoke-test.png)

#### Upload a file to AWS S3 from Gitlab CI

![Alt text](m5_Using_Gitlab_CI_to_build/images/upload-to-aws-s3.png)

#### Deploy to a Java application to AWS Elastic Beanstalk using the AWS CLI

![Alt text](m5_Using_Gitlab_CI_to_build/images/deploy-to-elastic.png)


#### Create an application version

![Alt text](m5_Using_Gitlab_CI_to_build/images/version-info.png)

