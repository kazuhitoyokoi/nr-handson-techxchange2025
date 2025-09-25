# How to use Git integration
Here, I will explain how to enable the Git integration feature on your Node-RED environment. If there's no Node-RED environment on your local PC or server on the cloud, you need to install the Node-RED based on the official document in advance.
Prerequisite
 To utilize Git integration on Node-RED, the Git command should have been installed on your environment. In general, macOS and Linux have the Git command as the default but the Windows environment has no Git command. Therefore, Windows users need to install the Git command by the installer download from the following website.
https://git-scm.com/downloads
Enabling Git integration
 There are versatile ways to turn on the Git integration like environment variables and manual definition on the settings.js file. In this article, I utilize the admin command provided by the Node-RED command. To execute the admin command, please type the following command on your command prompt or terminal.
- - - - - - - - - - - 
node-red admin init
 - - - - - - - - - - -
This admin command is the command-line wizard to ask questions to generate custom settings of Node-RED. Two of the question in the Projects section are related to Git integration.
CLI wizard to configure Git integrationIn the first question to enable the project feature, select "Yes". After that, the wizard asks to select workflow mode. In this article, select the "manual" mode because this mode is the fundamental way to understand Git integration. (On the other hand, in the flow development of the production system, "auto" may be recommended to record the flow change when the flow developer clicks the deploy button because it is easy to restore the flow.) Once all questions are finished to answer, the command saves the custom configuration to the settings.js file. To start the Node-RED process using the settings.js file, type the node-red command as usual.
- - - - - 
node-red
 - - - - -


Checking Git log
If you're familiar with Git CLI operation, you may be interested in the status of the local repository. To show the Git log on the command prompt or terminal, firstly change the working directory to the path of the local repository, "~/.node-red/projects/test" on macOS and Linux, "C:¥Users¥<User name>¥.node-red¥projects¥test" on Windows. After this operation, type the "git log" command to show the version history to the command prompt or terminal.
The output of the git log commandAs you can see in the above screenshot, the git history by CLI is shown as the same as the history tab on the flow editor.
Conclusion
In this article, I briefly explained the Git integration on Node-RED which is necessary functionality in the flow development of the mission-critical system. Leading companies have already used Git integrations in their mission-critical systems. For instance, Siemens has used this functionality in their product, Industrial Edge Flow Creator. If you're interested in the details of the procedures, you can read the documentation of this product. As another example, Red Hat has also adopted this Git integration in their Node-RED operator for Red Hat OpenShift as the default. With the expansion of usage in production, Git integration will become crucial and standard development among Node-RED users.
