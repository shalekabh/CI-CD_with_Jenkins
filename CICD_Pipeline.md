# Creating a pipeline

Adjusting the first job creation:

- Change the GitHub branch to "dev": When setting up the first job, make sure to configure it to use the "dev" branch of your GitHub repository. This ensures that we start with the latest development code.

- Add a "Post-build Action" to build Job 2 if the build result is stable: In the settings of the first job, we need to specify an action that triggers the execution of Job 2 only when the build result of the first job is stable. This ensures that Job 2 runs only when the code in the "dev" branch has successfully passed all tests.
Creating Job 2 (merging tested code from "dev" to "main" branch):

- Build the job as usual: Set up Job 2 with the necessary build steps, such as compiling the code, running tests, or any other actions required for the code in the "dev" branch.

- Configure the "Build Triggers" to watch the first job if it's stable: We want Job 2 to start only after the first job has completed successfully and its build result is stable. To achieve this, we configure the "Build Triggers" of Job 2 to monitor the status of the first job.

- In the build step, include plugins or commands like "git checkout main" and "git merge origin/dev": In the build step of Job 2, we include the necessary plugins or commands to switch to the "main" branch and merge the changes from the "dev" branch. This allows us to integrate the tested code from the "dev" branch into the "main" branch.

- In the "Post-build Actions", add a step to build Job 3 if it's stable: After the build step in Job 2, we add an action in the "Post-build Actions" section to trigger the execution of Job 3, but only if Job 2's build result is stable. This ensures that Job 3, representing the production stage, is triggered only when the merged code from Job 2 is considered stable.
Creating Job 3 (production stage):

- Build the job as usual: Configure Job 3 with the necessary build steps for deploying the code to the production environment. This can include tasks like transferring files, configuring servers, or starting applications.
Configure the "Build Triggers" to watch the second job if it's stable: In the configuration of Job 3, we set up the "Build Triggers" to monitor Job 2. This means that Job 3 will start only when Job 2 has completed successfully and its build result is stable.

- In the "Build Environment", enable the "SSH Agent" and use the "tech230.pem" (same as EC2): In the build environment settings of Job 3, we enable the "SSH Agent" feature for secure SSH connections. We specify the "tech230.pem" key file (assuming it's the same one used for EC2) to authenticate when connecting to the target server.

- In the build step, include plugins or commands for deployment: Within the build step of Job 3, we include the necessary plugins or commands to deploy the code to the production environment. For example, we can use SSH commands to connect to the production server and perform actions such as syncing files, restarting services, or executing scripts. Please ensure to replace the IP in the provided script with the actual public IP of your production server, and adjust any security group settings in Jenkins to allow the required access.

By following these steps, we create a pipeline where changes from the "dev" branch are merged into