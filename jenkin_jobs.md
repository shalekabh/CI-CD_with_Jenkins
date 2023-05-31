# Jenkins Jobs

Go to your Jenkins dashboard and create a new job called "Freestyle Project".

Provide a description for the job.

Configure the job to discard old builds and keep a maximum of 3 builds.

Enable the "GitHub project" option and enter the HTTPS Project URL, such as "https://github.com/shalekabh/CICD-and-Jenkins.git/".

Use the "Restrict where this project can be run" option to specify that the job should run on the "sparta-ubuntu-node" node.

Set up the job to use Git as the source code management system and enter the HTTPS link to your repository.

Create or add an SSH key for authentication, specifying the username and private key.

Change the branch specifier to "*/main".

Enable the "GitHub hook trigger for GITScm polling" option to trigger the build when changes are pushed to the repository.

Tick the "Provide Node and npm/bin/folder to PATH" option in the build environment.

Select "Execute shell" as the build step and enter the necessary commands, such as "cd app", "npm install", and "npm test".

Save the job configuration.

To link two jobs, open the configuration of one of the jobs.

Scroll down to the "Post-build Actions" section and click on "Build other projects".

Choose the other job from the list.

Apply the changes and save the configuration.

By following these steps, the second job will be triggered if the tests pass in the first job.