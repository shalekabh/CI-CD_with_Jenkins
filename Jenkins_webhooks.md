To create a webhook in Jenkins that triggers a build when you push to GitHub, you can follow these steps:

Configure Jenkins:

Open Jenkins and navigate to the project for which you want to set up the webhook.
Click on "Configure" to enter the project configuration.
Enable GitHub Integration:

Install the Jenkins GitHub plugin if it's not already installed. You can install it by going to "Manage Jenkins" > "Manage Plugins" > "Available" and searching for "GitHub Plugin".
In the project configuration, scroll down to the "Source Code Management" section.
Select "Git" as the source code management system.
Provide the repository URL (e.g., git@github.com:<username>/<repository>.git).
Configure other Git-related settings as needed (branch specifier, credentials, etc.).
Configure Webhook in GitHub:

Open your GitHub repository in a browser.
Go to "Settings" > "Webhooks" > "Add webhook".
In the "Payload URL" field, enter the URL of your Jenkins server's webhook endpoint. It should be in the format http://<jenkins-server>/github-webhook/.
Choose the content type as "application/json".
Select the events that should trigger the webhook. Typically, you would select "Just the push event" or customize it based on your requirements.
Make sure the webhook is active/enabled.
Click on "Add webhook" to save the webhook configuration.
Test the Webhook::

To ensure the webhook is working correctly, you can make a test push to the GitHub repository.
After the push, check the Jenkins project's build history to verify that a build was triggered by the webhook.
You can also check the Jenkins console output to see the build logs and verify that the build process executed as expected.
Now, whenever you push changes to the GitHub repository, GitHub will send a webhook payload to the configured Jenkins webhook endpoint, triggering a build in Jenkins. The build will execute based on your Jenkins project configuration and perform the necessary actions, such as building, testing, and deploying your code...