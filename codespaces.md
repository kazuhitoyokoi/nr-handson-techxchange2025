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
After clicking the green button, "Open in browser", another tab on your browser will be opened for the Node-RED flow editor. At the first, the dialog for the project feature will be opened in this environment. To skip the project configuration, click the "Not right now" button in the bottom-right corner.
Now, you can start to develop great flows in the Node-RED flow editor.
