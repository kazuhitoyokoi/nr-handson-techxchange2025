# Creating a new project
After opening the flow editor via the address, http://localhost:1880, you can see the wizard UI for Git integration.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*dd4gdrXn5t_DyGv8xIOjzw.png)

The wizard is easy to understand because it provides step-by-step procedures to configure the Git integration settings with the details of the explanations. But select the "Open existing project" text next to the "Not right now" for simple explanations in this tutorial. The next dialog is the user settings of the Git client. This information is used on both local and remote repositories on GitHub to identify who changes the flow. Therefore, I strongly recommend that the username and e-mail address are the same as your GitHub account to avoid emerging different users on GitHub.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*Eu5z0pvTDo3Yf6MSWoYZ3Q.png)

User settings for Git clientThe next dialog has three options, "Open project", "Create project" and "Clone Repository". Because we need to create a new project in the first step, select "Create project" from the options. (The "Open project" options will be used to switch the project when a single Node-RED environment has multiple projects in the future. And the "Clone Repository" option is for downloading the remote project which has been uploaded on GitHub by another flow developer.)

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

# Developing flow and recording history
Once creating a new repository on the flow editor, you can start to develop a new flow from scratch. For instance, create the simplest flow which consists of the inject and debug nodes to output the timestamp data to the debug tab. After checking the intentional behaviors of the flow, you may want to create a checkpoint to record the flow on the local repository. In this case, click the "+ all" button in the "Local files" section on the history tab to make all changed files ready to record.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*XmjZI4zu3MQgTNq4fyYNog.png)

Once clicking the "commit" button next to the "Change to commit", the text area to enter the commit message is emerged. In this tutorial, "The first flow" is set to the text area. After clicking the "Commit" button located at the bottom of the text area, your flow has been completely recorded with the commit message to the version history. You can see the version history in the "Commit History" section.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*rDZbUY5_DfuB8Zrxb8_47A.png)

That is the end of this tutorial. When you have done additional changes to the flow editor, you can repeat the same procedures on the history tab.
