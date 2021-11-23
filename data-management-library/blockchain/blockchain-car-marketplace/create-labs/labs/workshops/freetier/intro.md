# Introduction to Labs and Workshops                                   

The labs in this workshop walk you through all the steps to **develop workshops** for LiveLabs.

  > **Note:** You can find information about creating images for compute instances and storing them in Marketplace in the [Creating Compute Images for Marketplace](https://oracle.github.io/learning-library/sample-livelabs-templates/create-labs/labs/workshops/compute/) LiveLabs workshop.

## What are Labs and Workshops?
A lab is a new model adopted by the Database (DB) organization to enhance the tutorial experience. Labs are what the User Assistance community commonly knew as Oracle by example (OBE). Labs can be combined to form a workshop, formerly known as Hands-on Lab or HOL, or a Learning Path.

An individual Markdown (.md) file is called a lab. A collection of labs is called a workshop. A LiveLabs workshop must contain more than one lab. You cannot create a single lab LiveLabs (LL) workshop. In most cases, this is not a problem since most of the LL workshops contain at least one common lab titled **Get Started** that guides the user on the different types of Cloud accounts.

## What is GitHub?
GitHub is a cloud-based version control system designed for software developers.
  * At the core of GitHub is Git, an open source version control system that manages file versions and tracks the changes made by the members of a repository.
  * The Hub is a cloud-based repository that manages storage of the files and provides a folder structure.
  ![](./images/git-hub-what-is-github.png " ")

## GitHub Projects and Repositories
GitHub is organized by projects. Each project has its own repository (commonly referred to as repo) that is accessed through a unique URL. As of January 2020, there were more than 190 million repositories on GitHub.

In the following simplified example, the three-drawer filing cabinet represents three GitHub projects (one drawer per project). Each project can contain one or more repositories, represented by folders in the example. In this example, project 2 (second drawer) has three repositories (folders) and we are viewing one of those repositories.

  ![](./images/git-hub-projects-repositories.png " ")

## Oracle GitHub Project and learning-library Repository

At Oracle, we have a GitHub project named **Oracle** which has **291** repositories as of November 3, 2021. One of the repositories in the **Oracle** GitHub project is named **learning-library**. All of the LiveLabs workshops that you and others create are stored in the **learning-library** repository. This repo is sometimes referred to as **Production** since it's where customers view the completed LiveLabs workshops.

![](./images/git-hub-oracle-projects-learning-library.png " ")

+ You can access the **Oracle** GitHub project using the following URL:     
  [https://github.com/oracle](https://github.com/oracle)

  ![](./images/git-hub-oracle-project.png " ")

+ You can access the **Oracle** GitHub project repositories using the following URL:
  [https://github.com/orgs/oracle/repositories](https://github.com/orgs/oracle/repositories)

  ![](./images/git-hub-oracle-repos.png " ")

+ You can access **Oracle**'s GitHub project **learning-library** repository directly using the following URL which you should bookmark as you will use it often:
  [https://github.com/oracle/learning-library](https://github.com/oracle/learning-library)    

  ![](./images/git-hub-learning-library.png " ")

  The highlighted **sample-livelabs-templates** folder contains this workshop and also the available Livelabs templates.        

  > **Note:** The term **learning-library** that we reference in this workshop is the GitHub repository for the **Oracle** GitHub project. It is NOT the same as **Oracle Learning Library (OLL)** used formerly in the OBE world. OLL is an online resource for content about Oracle products [https://apexapps.oracle.com/pls/apex/f?p=44785:1](https://apexapps.oracle.com/pls/apex/f?p=44785:1).

## Develop LiveLabs Workshops Workflow
The following diagram shows the general workflow process that your need to follow to set up your environment to develop labs and workshops. Most of the tasks are performed only once.

![](./images/git-hub-workflow-flow-chart.png " ")

## Workshop Objectives
  * Set up the GitHub environment.
  * Install and use GitHub Desktop Client.
  * Fork the learning-library repository (copy repository content to GitHub).
  * Clone your forked learning-library repository (copy repository content to local machine).
  * Understand the lab folders' structure.
  * Install and use Atom Editor to and the LiveLabs Markdown templates to develop content.
  * Review a few Markdown features.
  * Perform GitHub operations to commit your developed content to the master (production) learning-library on GitHub.
  * Host workshops and labs in LiveLabs and optionally in OHC (User Assistance only).

## Lab Breakdown
- **Lab 1:** Get Started with Git and Set up the Environment
- **Lab 2:** Understand the Folder Structure
- **Lab 3:** Use Atom Editor and Live Server to Develop Content
- **Lab 4:** Use GitHub to Commit to Git Repository (Git Web UI)
- **Lab 5:** Add GitHub Hosted Labs to OHC

## What's Next?

  **You are all set to begin the labs! Click Lab 1: Get Started with Git and Set up the Environment in the Contents menu.**

## Want to learn more about LiveLabs workshops and GitHub?
  * [Oracle LiveLabs](https://apexapps.oracle.com/pls/apex/f?p=133:1)
  * [Get started with GitHub](https://docs.github.com/en/get-started)

## Acknowledgements

* **Authors:**
    * Anuradha Chepuri, Principal User Assistance Developer, Oracle GoldenGate
    * Lauran Serhal, Principal User Assistance Developer, Oracle Database and Big Data
* **Contributors:**
    * Aslam Khan, Senior User Assistance Manager, ODI, OGG, EDQ
    * Tom McGinn, Database and Database Cloud Service Senior Principal Product Manager, DB Development - Documentation
* **Last Updated By/Date:**
    * Lauran Serhal and Anuradha Chepuri, November 2021
