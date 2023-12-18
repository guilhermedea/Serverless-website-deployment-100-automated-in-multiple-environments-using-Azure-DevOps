# Serverless website deployment 100% automated in multiple environments (Test, QA and Production) using Azure DevOps Repos and Pipelines (CI/CD).

![picture with the words Cloud Project and icons of the services used](https://miro.medium.com/v2/resize:fit:720/format:webp/0*0Z00KD7XGXzjB1Ow.jpg)

In another project based on a real-world scenario, I worked as a Cloud Engineer using DevOps, where I deployed a serverless website in a 100% automated 
way using Azure DevOps Repos and Azure DevOps Pipelines resources.

Azure DevOps Organization and a new project have been created. The Azure DevOps Repos stored the website files, and the CI/CD Pipelines automated the 
entire website deployment process in 3 different environments (Test, QA, and Production).

![picture showing a graph of the solution architecture](https://miro.medium.com/v2/resize:fit:720/format:webp/0*Vc-kua1EWmuiVIK1.jpg)

The setup process is much more practical than I thought, with the only obstacle being the time required to approve the parallelism extension in Azure, 
which takes around three business days to be approved. With the expansion approved, I began the process.

I created three storage accounts, each for a stage of production (Test, QA and Production). I set all three to static website mode, which prepares the 
containers to receive a static website. After that, I entered Azure DevOps and created an organization and a project. Through Git I cloned the website 
files and uploaded them to a repository in Azure DevOps Repos.

With the bases ready, I continued the process of creating CI/CD pipelines. The Azure interface is very visual and offers numerous options for you to 
configure as you like. I quickly created a continuous integration pipeline using two processes, one that zips the files from the repository directory
and another that publishes this artifact for the next step. For the delivery pipeline, the process was a little more complex, consisting of a task to 
extract the files and another process that uses Azure CLI to execute an inline command responsible for uploading the files to the containers previously
created on the storage accounts.

![Picture showing Azure DevOps pipeline dashboard showing the pipeline running](https://miro.medium.com/v2/resize:fit:720/format:webp/1*ORHsjTpPYQQ1Q_dxRT_hxg.png)

In the first test, the delivery failed. The log pointed to an error in the inline script code and I spent days trying to fix that. Eventually I realized that 
the redeploy was not using the updated configurations, and after performing a new release, the pipeline worked! I did another test, changing the index.html 
file and making a new git commit. The pipelines worked perfectly, and automatically the site was live using the links from the storage accounts and with the
updated code. All from a simple commit.

I must confess that I really enjoyed this project. Since I started studying about the area I was seduced by DevOps, and being able to carry out a practical 
project in this area was a wonderful opportunity. Here’s to the next challenges!
