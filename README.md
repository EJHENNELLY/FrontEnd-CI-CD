# FrontEnd-CI-CD
Update your front-end using CI/CD

In this project, we are going to use CI/CD to update our front end automatically using GitHub.

Prerequisites:
1. Have already completed my "cloud resume" tutorial
2. Working GitHub account
3. VS Code


Let's Begin by opening up your GitHub and creating a New Respository. Type in your repo name. I would set it to "private" and create!

Create a "website" folder and place it in your local downloads. Place all of your frontend html, css, js into the website folder.

Open your terminal and go into your downloads folder. 

-> cd D:\Downloads

Create a directory using the same name as your Github repo. 

-> mkdir "github-repo-name"

-> cd "github-repo-name"

Look into your downloads folder and you should see a new folder with your repo name. Drag your "website" folder that holds your front end and drop it into your new repo folder.

Initialize the repo

->git init

Add your files to the repo
->git add .

create your first commit
->git commit -m "initial commit"

->git branch -M main

->git remote add origin "typre-your-repo-url-here".git

->git push -u origin main

You should now see the website folder in your github repo!

Now you have source control!

---
#Now we will integrate CI/CD!!

Open the terminal back up and type "code ."
This will open up VSCode
Create a new folder called "github/workflows"
Create a file for called front-end-cicd.yml within the folder.

Add the following code:

![Screenshot (84)](https://github.com/user-attachments/assets/6fb52d19-9775-4531-b3f2-671222de517a)

Explanation: This code creates a .yml file to upload the changes to s3.

name: you can use whatever you want.

on: this portion decides when the ci/cd gets triggered. In this case, we are triggering it when you make a push on the main branch.

jobs: 
   runs-on: deploys the jobs using the latest ubuntu container
   steps: uses are for a master action and the second is to sync with s3. If you want to learn more about this use you can navigate to jakejarvis github 
   with: 
   args: gives actions
   env:
   This code defines the credentials that github needs to deploys the changes you make. It is good practice to hide your credentials using github secrets which I will show below.

   name: Invalidate Cloudfront - this step creates a cloudfront invalidation so that it will deploy the newest version of your website right away.
   run: replace the ${{ secrets }} code with your cloudfront distribution #

You should see a number next to the "source control" in vscode. Go to source control and type in a name for the change "added ci/cd" and then click "commit" and push it to the main branch.

Navigate back to your repo and click the "actions" tab and you should see the commit successful. You can now automatically make changes to your front end!!
![Screenshot (85)](https://github.com/user-attachments/assets/18a6d1d6-3391-4e6e-9e4b-73858c34cdaa)





What are github secrets: This is a way to encrypt sensitive information like aws service arns and other credentials.
How to use them: Click on "settings" in your github repo and scroll down to "secrets and variables" tab. ->actions -> new repo secret -> give it a name such as AWS_ACCESS_KEY and type in your credential below and save. That's easy








