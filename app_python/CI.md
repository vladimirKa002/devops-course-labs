# GitHub Actions Best Practices


## Speedup Workflow

To optimise the performance of the workflow, I used caching `cache: "pip"` for its stages.

## Github Secrets

Usually, a good practice from security point of view is to avoid hardcoding sensitive information into files. 
In my case, I created Github secrets (CI variables), like `DOCKERHUB_USERNAME` or `DOCKERHUB_PASSWORD`, which enhances 
security of my application and can be also useful for readability.

## Separate Dependent Jobs

There are multiple separate jobs created for the workflow: `lint`, `test`, `docker`. By splitting them into multiple
and making them depend on each other, I make sure that release to DockerHub will happen only when there are no any issues in code.

## Stages Naming

I named all stages and their actions in a way that it will always be clear what is the current step or failure in the execution
of CI pipeline.

## Testing Job

There is a testing job which runs test using `pytest`. It allows us avoiding any bugs in released product.

## Security Check

I use Snyk GitHub Action to check the application for security vulnerabilities.