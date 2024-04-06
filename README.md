Let's continue our CICD journey by creating a Continuous Integration Pipeline that uses S3 and CodeBuild along with Github to add files to an S3 bucket. So if you were following along in my last article this will be simple, if not I strongly advise you to follow along with it to learn how to deploy a Code Build project and build your own BuildSpec file, because I will not be going step by step in this article on those parts.


## Create S3 Bucket
Create an S3 bucket that we will use to store our code. You can do this via the CLI if you wish using the following command.

``aws s3api create-bucket --bucket <bucket name>``
***

## Create a GitHub Repo
Create a GitHub repo on GitHub. Then head to your local machine and clone that repo.

git clone <URL of Repo>
***


In this repo create two files one named **text.txt** and the other named **buildspec.yml**

## Create CodeBuild Project
This project will be very similar to the other article so go through and build your CodeBuild project. Choose the correct GitHub repo and make sure to choose **PUSH** on the **webhooks** section. Once created head into your IAM Role for **CodeBuild** and give it access to our bucket by giving it the AWS **S3FullAccess** policy. I know it is not the safest, but since this is a simpler project I am keeping it simple for now.

## Push to GitHub
Now with our files created we will push our files to GitHub, this may require you to add in your access token from GitHub and configure your Git credentials. Since we didn't make an additional branch this will push directly to main, which is a no-no in production but this is just a simple project to learn how CodeBuild behaves. This will cause CodeBuild to run and update our S3 bucket. You can go to CodeBuild and see it deploying.
