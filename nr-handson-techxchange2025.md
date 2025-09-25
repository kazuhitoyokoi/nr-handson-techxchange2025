# Introduction to Git integration with Node-RED
In this material, I will introduce Git integration functionality in Node-RED. Using Raspberry Pi devices or cloud services, many hobby users have quickly been developing their flow by just connecting nodes to realize their idea of IoT systems like home automation or RPA. To utilize these great experiences as flow developers in their job, they may consider using Node-RED for mission-critical systems. For example, these systems are factory automation and visualization dashboard in their factories, or financial backend APIs for mobile applications. However, in this case, flow developers tend to encounter the following problems with their production systems.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*OHoMnUUDaytPp0xkIaQ4Zw.png)

## Problem 1: All functionalities exist in a single flow on a single Node-RED environment
 If only one Node-RED environment is available in the mission-critical system, the huge flow which contains many nodes will exist in this single environment. Because the single flow will use huge memory and CPU resources, it leads to performance problems. In other respects, context variables or HTTP endpoints which have the same names are sometimes conflicted due to a single environment. In terms of the Node-RED dashboard, all components according to the different applications have existed in the same dashboard UI.

## Problem 2: Who modified the Node-RED flow? When flow was modified?
 In the default usage, a lot of flow developers will use a single environment simultaneously. Flow editor has user authentication for login but doesn't manage who edits the flow and when a flow developer changes it. Due to this mechanism, flow developers cannot revert the flow when the problem occurs in mission-critical systems. Furthermore, the responsibility for the serious situation will be vague.

## Problem 3: Manual flow backup and uncommon flow sharing with other developers
 To avoid loss of the flow on the flow editor, the flow developer manually backup the flow using the "exporting flow" functionality and then save it as a JSON file to their local PC in a conventional way. They need to set the file name to identify the flows but it is a time-consuming task. Additionally, it will also be difficult for other flow developers to understand the details of the flow and required modules in the case of sharing flow files because the pieces of information are written to the other files like word files by flow developers in their way.

As I described above, there are a lot of concerns in flow development for production systems. If the Node-RED environment is prepared as same as the personal environment, the progress of the flow development may be a slog.

# What is Git integration?
This functionality is known as a project feature on the Node-RED official document. Using the Git integration, flow developers can manage their flows on the flow editor as same as general code development by Git command or IDE like Visual Studio Code. In the systems development, three issues described in the previous section can be solved as follows.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*XLcbUcW0CGWHb4dWyGv9Ag.png)

## Solution for problem 1: Switching projects
 After enabling Git integration, the flow developer can select one development project from multiple projects on the flow editor. Because each project has a minimal flow only to realize one application, flow developers can solve the problems in terms of computer resources and artifact conflicts inside the flow. In my experience, I have seen a nightmare situation in that unnecessary configuration nodes remain in the flow due to sharing the flow development environment among multiple projects. Using the switching projects functionality, flow developers can avoid contamination due to the other project and proceed with a couple of flow development in different projects on the single Node-RED environment in parallel.

## Solution for problem 2: Version control of flow
 In the project created by Git integration functionality, the flow editor has the "History" tab on the sidebar area. On the tab, flow developers can manually input the commit message when the flow should be in checkpoint to record the developed flow. If the automatic mode is selected in the user setting instead of manual mode, it is also possible to add commits with the default message automatically when the flow developer clicks the deploy button. In both modes, the version-managed flow can be recovered to the previous commit which has executable flow by CLI Git operation when the latest flow doesn't work due to an error. On the single Node-RED environment, all commits are by a single user. However, if flow developers share their flow on the GitHub repository, each commit has information about the developer who modified the flow. This information will be useful to identify when and who made the mistake when solving problems in the flow.

## Solution for problem 3: Flow sharing on GitHub
 In addition to the version control in the local repository, Node-RED has the ability to upload to the remote repository on GitHub. Using the ability, it is beneficial for the flow developer to back up the flow in preparation for the loss of the environment like a PC broken or a server down. Flow developers can also input information about how to use the flow and dependency modules to execute flows on the flow editor. The inside flow editor outputs this information to general files like README.md, and package.json files. When other flow developers download the shared flow, they can easily check the details of the application from the documentation files. And they can also install required modules by just clicking the module installation button on the flow editor. Furthermore, this functionality can be used in the automated deployment of the flow for cloud and edge devices using CI/CD pipelines like GitHub Actions.

# How to execute Node-RED on GitHub Codespaces
In this article, I will introduce how to execute Node-RED on GitHub Codespacesas one of the Web IDE environments.

# What is GitHub Codespaces?
 GitHub Codespases is the Web IDE integrated with GitHub and you can use it using your GitHub account. Currently, all users are able to use the Codespases environment for 60 hours a month for free. And we can use 2 CPUs, 4 GB memory, and 32 GB storage for the period. It is suitable not only for code development but also for temporary application execution like Node-RED.

# Procedures to execute Node-RED on Codespaces
 I prepared the Codespaces template for Node-RED on the GitHub repository.

https://github.com/kazuhitoyokoi/node-red-codespaces

This repository is the template to create the Node-RED environment on GitHub Codespases. Using the Codespases, you can…github.com
The followings are step-by-step procedures about how to use this template.

## 1. Create your GitHub account

 If you have no GitHub account, create your GitHub account from the following URL.

https://github.com/signup

To register for the account, you need to input your information like your e-mail address, password, and user name.

## 2. Extend the timeout of GitHub Codespaces

 As the default, the environment prepared by Codespaces will be terminated in 30 minutes. Because this period is too short to develop Node-RED flows, extend the timeout from the user's settings URL.

https://github.com/settings/codespaces#default-idle-timeout-header

 In the text input area, type the maximum value, 240 minutes.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*cjPrDKd_EftXOdluDPjkIA.png)

By this setting change, you can use the Node-RED flow editor for four hours. After four hours, the Node-RED instance will be automatically shut down. Therefore, you need to relaunch the instance which has saved flow on GitHub Codespaces. Due to GitHub pricing, 60 hours per month is the total time in the free plan. But it will be enough for trying Node-RED.

## 3. Move to the GitHub Codespaces

 When accessing the Node-RED template repository, you can see the green button, "Use this template" in the top-right corner. After clicking the button, two options emerge to be able to select. Here, select "Open in a codespace" to open the template repository on the Codespaces.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*RcSsE8ol_J9aLdx8OeuZSw.png)

## 4. Open Node-RED flow editor

 After about one minute, this environment will automatically download Node-RED and then start up. When the Node-RED flow editor is ready to use, the dialog will be pop-up in the bottom-right corner.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*s5NuxzW8R6fKg0NW2EGuug.png)

After clicking the green button, "Open in browser", another tab on your browser will be opened for the Node-RED flow editor. At the first, the dialog for the project feature will be opened in this environment. To skip the project configuration, click the "Not right now" button in the bottom-right corner.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*da7loI9f8EhfKPLFgWjCGw.png)

Now, you can start to develop great flows in the Node-RED flow editor.

# Creating a new project
After opening the flow editor via the address, http://localhost:1880, you can see the wizard UI for Git integration.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*dd4gdrXn5t_DyGv8xIOjzw.png)

The wizard is easy to understand because it provides step-by-step procedures to configure the Git integration settings with the details of the explanations. But select the "Open existing project" text next to the "Not right now" for simple explanations in this tutorial. The next dialog is the user settings of the Git client. This information is used on both local and remote repositories on GitHub to identify who changes the flow. Therefore, I strongly recommend that the username and e-mail address are the same as your GitHub account to avoid emerging different users on GitHub.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*Eu5z0pvTDo3Yf6MSWoYZ3Q.png)

User settings for Git clientThe next dialog has three options, "Open project", "Create project" and "Clone Repository". Because we need to create a new project in the first step, select "Create project" from the options. (The "Open project" options will be used to switch the project when a single Node-RED environment has multiple projects in the future. And the "Clone Repository" option is for downloading the remote project which has been uploaded on GitHub by another flow developer.)

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*rT0iDmmsPfygAVkIDPg0UQ.png)

At the bottom of the "Create project" button, there are four settings as follows.

- Project name

  This is the project name for the local repository. To consider the situation that it will be used for the part of the URL on GitHub after uploading flow to the remote repository in the future, the length of the project name should be as short as possible. In general, the characters in the project name should also be lower cases or numbers with hyphens as delimiters. In this article, I inputted "test" as the project name.

- Description

  It is an optional setting to input the description of the created project. You can write the text in the natural language.

- Flow file

  This is also an optional setting to specify the flow file name. But there is no reason why the flow developer changes the name in the single flow file. Remain the default name, "flow.json".

- Credential

  The final setting is to select whether the credential of the flow should be encrypted by an encryption key or not. Because this tutorial uses a local repository on your local PC or a remote repository created as a private mode on GitHub, encryption is not needed. Therefore, select the bottom option, "Disable encryption". (When publishing the flow with credentials to a public repository on GitHub, it should be "Enable encryption" to protect confidential information.)

# Using version control for Node-RED flows

In this article, I will introduce version control of Node-RED flows using the Git integration functionality. This version control functionality is the core of Git integration with Node-RED, as the Git command is used within Node-RED to record version history. Even flow developers who are not familiar with Git commands, such as factory engineers, can easily use this functionality because it is available through the Node-RED flow editor interface.

## (1) Create your first flow
In this tutorial, we will use the simplest flow consisting of inject and debug nodes. After placing these nodes in the central workspace, create the wire between the nodes. Then press the deploy button to run the flow on the Node-RED backend server.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/0*QElp-A9hrsLr4sht.png)

When you click the inject node’s left button, the inject node triggers the message to the wire. From the wire, the debug node connected to the inject node outputs the received timestamp number to the debug tab of the sidebar.

## (2) Change the status of the flow file to the staging
The next step is to change the status of the first flow to staging. The staging state is the Git principle equivalent of “git add” to select files that should be committed to the version. Once the files are ready to commit, you make the record with the message, timestamp, and developer information in the case of the general step. In another case, we can also restore the flow to the previous state. In the next step, we will try both procedures to perform the commit after changing the flow status to staging and then restore the previous flow. On the History tab, there are two sections, “Local Changes” and “Commit History”, as you can see in the screenshot.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/0*7jHnviAQDiH0fF8j.png)

The Local Changes section is used to manipulate the local flow and associated files to add and remove them from the history. (“Commit History” is an area to check the recorded history. I will explain it later). In addition, the “Local Changes” section is divided into “Local files” and “Changes to commit”. In the next step, we will use the Local Changes section first.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/0*-7zq9NLI3rs8y0um.png)

Click the plus button on the flow file that has the “Stage change” tooltip. Clicking the plus button changes the status of the flow file to staging status and moves the flow file to the “Changes to commit” section, which means it is ready for commit.

## (3) Commit the change with a message
The next step is to use the “Changes to commit” section. To commit to history with a specific message, click the “Commit” button in this section.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/0*4qSVjqixr7sFL7KH.png)

This will bring up the text area at the bottom of the section, where you can enter your commit message. As an example message, I typed “The first flow” into the area and then clicked the “Commit” button at the bottom of the text area.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/0*0nCzUABXCyLbuCj2.png)

If you’re familiar with the Git command, it might be easier to explain that “git commit -m <message>” was executed internally.

It deletes all working files from both sections within the “Local Changes”. This means that the file is recorded in the version history. When you open the “Commit History” section, there is a version history that includes the commit that was made.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/0*-ULWY4tiMcJwSz9f.png)

At this point, the initial procedure for adding the commit to the version history is complete. As the next step, I will modify the flow and return it to the state of “The first flow”.

## (4) Modify the flow
As an example of modifying the flow, the template node is inserted between the inject and debug nodes. To add the node to the flow, search and pick the template node from the palette, then release the node on the wire.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/0*HPyB7lqW2blEaoM8.png0)

When the inject node’s button is clicked in this flow, the template node creates a new message, “This is the payload: <timestamp>!”. Using the debug node, you can check this message in the debug tab.

## (5) Restore the flow
If you are having problems with the modified flow, you may want to revert to the previous flow, which you have named “The first flow”. To revert the flow, simply click the revert arrow button with the tooltip “Revert Change” in the “Local files” section of the “Local Changes” panel.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/0*HREMF-J_57pPh8ON.png)

After clicking the button, the following notification dialog will appear. Of course, you should press the “Revert Changes” button in this dialog.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/0*LMPpW24ZxkYR0uGb.png)

The flow editor immediately reverts the flow to the previous commit. So you can see the previous flow, which only consists of the inject and debug nodes.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/0*LMPpW24ZxkYR0uGb.png)

As I explained above, the flow development is recoverable using Git’s integration functionality. All states of operations are stored in the persistent local filesystem. So even if you close or reload your browser, you can still recover your flow.
