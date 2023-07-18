# Jenkins Deployment Guide

This guide explains how to deploy a Jenkins job that uses a Jenkinsfile from a source code management (SCM) system. This setup also assumes your SCM repository is configured with a webhook to trigger Jenkins builds automatically.

## Step-by-step Guide

1. **Access Jenkins and Create a New Job**

   Open your Jenkins server in a web browser. On the home page, click on "New Item" on the top left.

2. **Choose Pipeline and Enter an Item Name**

   Enter a name for your new job in the "Enter an item name" field, select "Pipeline", and then click OK.

3. **Configure the Pipeline**

   In the Pipeline section of the configuration page, choose "Pipeline script from SCM" in the "Definition" field.

4. **Choose Your SCM**

   In the SCM field, choose the type of source code management system that hosts your Jenkinsfile. This could be Git, Subversion, Mercurial, or another option.

5. **Enter the Repository URL**

   Enter the URL for your source code repository in the Repository URL field. 

6. **Specify the Jenkinsfile**

   As your Jenkinsfile is in the root directory of the repository, enter `Jenkinsfile` in the "Script Path" field.

7. **Set Up Credentials (if necessary)**

   If your source code repository requires authentication, click on the "Add" button next to the "Credentials" field, and then add the necessary credentials.

8. **Configure Webhook Trigger in the Pipeline**

   In the job configuration page, go to the "Build Triggers" section. Depending on the source code management system, select the option "GitHub hook trigger for GITScm polling", "Bitbucket Trigger", "Trigger builds remotely", or "Generic Webhook Trigger". If the last two options are used, provide an authentication token.

9. **Save the Pipeline Job**

   Click the "Save" button to save the job.

## Webhook Configuration

The Payload URL that you need to provide in your source code repository typically follows a specific format:

For GitHub: `http://your-jenkins-url/github-webhook/`

For Bitbucket: `http://your-jenkins-url/bitbucket-hook/`

If you're using "Trigger builds remotely", the URL would look like this: `http://your-jenkins-url/job/your-job-name/build?token=YOUR_TOKEN`

Replace `your-jenkins-url`, `your-job-name`, and `YOUR_TOKEN` with your actual Jenkins URL, job name, and the token you've set up, respectively.

Now, your Jenkins job should be set up to run automatically whenever a change is made in your repository. The pipeline will run based on your Jenkinsfile in the root directory.
