
# CI/CD Pipeline Setup

This guide explains the steps to set up and run the provided CI/CD pipeline using GitHub Actions for deploying a containerized application to AWS ECS.

## Prerequisites

Before you begin, ensure you have the following:

- AWS account with the necessary permissions.
- AWS CLI installed and configured.
- Docker installed on your local machine.
- GitHub repository containing your application code.
- Amazon ECR repository for storing Docker images.
- Amazon ECS cluster and service configured.

## Setup Steps

1. **Clone your repository**

    ```sh
    git clone https://github.com/devDhiraj12/Github-actions-Ecs.git
    cd your-repository
    ```

2. **Add GitHub Secrets**

    In your GitHub repository, navigate to **Settings > Secrets and variables > Actions** and add the following secrets:

    - `AWS_ACCESS_KEY_ID`
    - `AWS_SECRET_ACCESS_KEY`

3. **Configure the GitHub Actions Workflow**

    Ensure you have a `.github/workflows/ci-cd.yml` file in your repository with the following content:

    ```yaml
    # The provided workflow file content goes here
    ```

4. **Commit and Push**

    Commit your changes and push them to the `main` branch:

    ```sh
    git add .
    git commit -m "Add CI/CD pipeline workflow"
    git push origin main
    ```

5. **Trigger the Pipeline**

    The pipeline is configured to trigger on every push to the `main` branch. To manually trigger the pipeline, you can make a minor change and push it:

    ```sh
    echo "trigger pipeline" >> README.md
    git commit -am "Trigger pipeline"
    git push origin main
    ```

6. **Monitor the Pipeline**

    Go to the **Actions** tab in your GitHub repository to monitor the progress of the pipeline. The steps in the workflow include:

    - Checkout code
    - Configure AWS credentials
    - Login to Amazon ECR
    - Build, tag, and push the Docker image to Amazon ECR
    - Update the ECS service
    - Wait for the ECS service to stabilize
    - Get the running task's public IP
    - Run integration tests
    - Rollback on failure (if necessary)

## Notes

- Ensure your ECS cluster and service are correctly configured to run the Docker image.
- Modify the workflow file as needed to fit your specific requirements.
- The integration test step assumes a web application running on the public IP. Adjust the test command according to your application.

## Troubleshooting

If the pipeline fails, check the following:

- Correct AWS credentials and permissions.
- Proper configuration of the ECS cluster and service.
- Network configurations allowing access to the ECS tasks.

For detailed logs, refer to the **Actions** tab in your GitHub repository.

## Conclusion

By following these steps, you should have a functional CI/CD pipeline deploying your application to AWS ECS using GitHub Actions. Adjust and extend the workflow as needed for your specific use case.
