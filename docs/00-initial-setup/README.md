# Module 0 - Initial Setup

In this module we will setup the required pre-requisites to get started with Amplify Console Workshop. 

## Prerequisites
### AWS Account
In order to complete this workshop, you'll need an AWS account and access to create and manage the AWS resources that are used in this workshop, including CodeCommit, Amplify Console, CloudFormation and Cognito.

The code and instructions in this workshop assume only one participant is using a given AWS account at a time. If you attempt sharing an account with another participant, you may encounter naming conflicts for certain resources. You can work around this by using distinct Regions, but the instructions do not provide details on the changes required to make this work.

Please make sure not to use a production AWS environment or account for this workshop. It is recommended to instead use a development account which provides full access to the necessary services so that you do not run into permissions issues.

### Region Selection
Use a single region for the entirety of this workshop. This workshop should work in all Regions that are currently supported by Amplify Console (North Virginia, Ohio, Oregon, Ireland & Sydney)

## Module 0A - Cloning the main workshop repo

Firslty we need to clone the workshop repository from Git.

#### HTTPS
```$ git clone https://github.com/stevenbryen/amplify-console-workshop.git```
#### SSH
```$ git clone git@github.com:stevenbryen/amplify-console-workshop.git```

Now change to the workshop directory, we will be working from here for the remainder of the workshop.

```$ cd amplify-console-workshop```

This repo includes the following three folders which we will be using throughout this workshop.


- **docs** - All of these walkthrough instructions are in this folder, broken down per module.
- **amplify-sample1** - A Satic Single Page App that we will use to demonstrate the front end functionality of Amplify Console.
- **amplify-sample2** - A site that uses Amplify Framework to create backend resources. We will use this in Module 3.

## Module 0B - Setting up your own CodeCommit Repos

Each App that we deploy in Amplify console will be linked to a brand in a git repository of your own. This guide will walk you through how to set that up using AWS CodeCommit, but Amplify Console supports ***Bitbucket, GitHub, GitLab or AWS CodeCommit***. Feel free to use one of the other providers, but this guide will focus on CodeCommit only.

Firstly we need to configure Credentials for AWS CodeCommit. CodeCommit supports credentials over HTTPS with static Git Credentials, Using the AWS CLI Credential Helper or over SSH using SSH Keys. Details on all of these methods is available [here](https://docs.aws.amazon.com/codecommit/latest/userguide/setting-up.html). I will focus on using SSH Keys below, but if for any reason you need to use HTTP, take a look at the link above.

1. Ensure that you have a user created in IAM. This guide assumes that you already have at least one user in AWS Identity and Access Management that you can use. For details on creating a user look [here](https://docs.aws.amazon.com/IAM/latest/UserGuide/getting-started_create-delegated-user.html)

2. Navigate to the IAM console [https://console.aws.amazon.com/iam/home](https://console.aws.amazon.com/iam/home) and find your User object. Click on the User to get more details. Follow one of the below guides to get access to CodeCommit configured.
    - If you are using Linux/Unix or OSX use the following guide to configure access to CodeCommit [SSH Connections on Linux, macOS, or Unix](https://docs.aws.amazon.com/codecommit/latest/userguide/setting-up-ssh-unixes.html)
    - If you are using Windows use the following guide to configure access to CodeCommit [SSH Connections on Windows](https://docs.aws.amazon.com/codecommit/latest/userguide/setting-up-ssh-windows.html)

3. Now that you have access to CodeCommit, we need to create two respositories for each of our applications. We will use the AWS Console to create these. In the AWS Console, navigate to the AWS CodeCommit console using the "Services" link in the Navigation pane.

4. Select the "Create Repository" Button and create a respository with the name ***"amplify-sample1"***. Repeat this step and create a repository named ***"amplify-sample2"***

5. We now have two repos created for our sample apps. We now need to associate our code with them. Change Directory into the first sample app dir and configure the git repo.

    ```
    $ cd amplify-sample1
    $ git init
    $ git add .
    $ git commit -m "initial commit"
    ```

6. Now navigate to the repositories page on the AWS CodeCommit console. You should see a list of respositories and an option to Clone the SSH URL in the right collumn for the amplify-sample1 repo. This will copy your repo URL to the Clipboard for you to replace the one in the code snippet below.
    
    The below commands will add the remote repository into your local git configuration and then push the initial code to the remote CodeCommit Repo.

    ```
    $ git remote add origin ssh://git-codecommit.eu-west-1.amazonaws.com/v1/repos/amplify-sample1
    $ git push -u origin master
    ```

7. You can check that the **git push** was sucessful by clicking the repo in the CodeCommit console. It should no longer be empty.

8. Repeat steps 5-7 for **amplify-sample2** subfolder. We now have two remote repos in CodeCommit ready for our workshop.

You are now ready to move onto Module 1.


    

    

