---
marp: true
theme: default
paginate: true
---
![bg cover](images/title4handson.png)
<!--
Hello everyone. Thank you for attending this session. This session is a Node-RED hands-on. Today, we will create a Node-RED application using the Project Feature.
-->
---
# Kazuhito Yokoi
- Core contributor of Node-RED project
- Organizer of Node-RED User Group
- Member of LF AI & Data Foundation Community

![h:100% bg right:46%](images/openjsf.png)
<!--
Let me introduce myself. My name is Kazokoy. I am a contributor to the Node-RED project, and in Japan, I am one of the organizers of the Node-RED user group. In Japan, we also organize the AI and Data Foundation community. I also hold the Node-RED and data meetup in Japan with other companies. Last year, the OpenJS Foundation kindly published my blog content on the OpenJS website. If you have any questions or are interested in our activities, please see the website.
-->
---
## What is Node-RED?
Low-code development tool from novice users to IT professionals

- Released by IBM as an open source software
- Hosted by the OpenJS Foundation
- Used in manufacturing industry to realize industrial IoT

![h:400 bg right:50%](images/floweditor.png)
<!--
This slide explains what Node-RED is. Node-RED is a low-code development tool for everyone, from novice users to IT professionals. About 10 years ago, IBM UK released Node-RED as open-source software. Currently, the OpenJS Foundation, under the Linux Foundation, hosts the project. Node-RED is especially used in the manufacturing industry to realize industrial IoT, and a lot of manufacturing companies have used Node-RED on their production sites.
-->
---
# Node-RED statistics
Node-RED has been widely used for 10 years.
- 155 releases
- 9,802 commits
- 237 contributors
- 22k GitHub stars
- 3B+ Docker pulls
- 5,562 community nodes
![h:400 bg right:50%](images/npmstat.png)
<!--
These are the Node-RED statistics for the past 10 years. Node-RED has been widely used. The Node-RED development community has released Node-RED more than 100 times, and there are almost 10,000 commits. In the GitHub repository, there are more than 200 contributors. The Node-RED project has gained over 22,000 GitHub stars, and amazingly, the number of Docker pulls is more than three billion. On the Node-RED website, there are more than 5,000 community nodes. According to the statistics on npm, the number of downloads has been gradually increasing.
-->
---
# Supported Envionments
Node-RED supports environments that can run Node.js.
- Local PC
  - Windows
  - macOS
  - Ubuntu
- Docker
- Raspberry Pi
- Cloud
![h:560 bg right:48%](images/environment.png)
<!--
Node-RED supports versatile environments that can run Node.js. So, any environment is supported if it supports Node.js. For example, on a local PC—Windows, macOS, Ubuntu, and other Linux operating systems—Node.js can run in these environments. Therefore, Node-RED also supports these environments. A Docker container is the most common way to use Node-RED.

Historically, Raspberry Pi OS included Node-RED for many years, but currently, Raspberry Pi OS does not include Node.js by default. The evolution of Node-RED and Node.js is very rapid. So, if we need to use Node-RED on a Raspberry Pi, we need to install it manually, but it is a fully supported environment. In cloud environments, if you have an IaaS or PaaS environment, you can use Node-RED. On the Node-RED website, there is a lot of documentation for using Node-RED in these environments: running locally, on Raspberry Pi, Docker, Android, Azure, AWS, and FlowFuse.
-->
---
# How to install
- Local environment
```
sudo npm install -g --unsafe-perm node-red
node-red
```
- Docker
```
docker run -it -p 1880:1880 --name
mynodered nodered/node-red
```
- Raspberry Pi
```
bash <(curl -sL
https://raw.githubusercontent.com/node-red/linuxinstallers/master/deb/update-nodejs-and-nodered)
```
<!--
In general, you can use Node-RED using the command-line interface in a local environment. You just type `npm install -g node-red`. After that, you can execute the `node-red` command in your environment. If you want to use a Docker environment, just run the `nodered/node-red` Docker image. For the Raspberry Pi environment, the Node-RED community has published a script to install Node-RED. So, you just copy and paste the command, and Node-RED will be installed automatically.
-->
---
# Node-RED nodes
Many predefined and custom nodes for services and devices
- Data collection
- Machine control
- External server access
- Database connection
- Data analysis
- Visualization

![h:540 bg right:57%](images/library.png)
<!--
As I said, there are 5,000 nodes in the community library, with many pre-built custom connectors for services and devices. Node-RED can deliver sensor data using data collection nodes. If I want to use Node-RED on a Raspberry Pi, I can use the GPIO port to control machines. Node-RED supports the HTTP, MQTT, and WebSocket protocols, so we can easily connect to external servers. The Node-RED community has published database connection nodes to connect to major databases like MongoDB, MySQL, PostgreSQL, and others. For data analysis, Node-RED can be used with TensorFlow projects and other AI environments. For data visualization, today we will use the dashboard user interface to visualize sensor data or image data. Today, we will create a chat application on Node-RED using the dashboard nodes.
-->
---
# Pre-installed Devices
Many devices equip Node-RED as a pre-installed software.
- Seeed Studio, reTerminal DM, reCamera
- Advantech, ADAM-6700
- ADLINK, Vizi-AI Devkit
- QNAP, QIoT Suite
- Emerson, PACEdge

![h:400 bg right:57%](images/recamera.png)
<!--
In the industrial community, a lot of devices come with Node-RED as pre-installed software. For example, Seeed Studio released the reTerminal, which is an industrial Raspberry Pi. They also published a camera; this small camera contains a Linux OS and Node-RED. Advantech released their own original devices using Node-RED. Amazon also published devices with Node-RED pre-installed.
-->
---
# GAIA-X Federation Services
OSS set for data exchange between companies
- Hosted by the Eclipse Foundation from 2023
- GXFS Workflow Engine based on Node-RED

https://github.com/eclipse-xfsc/orchestration-engine

![h:400 bg right:57%](images/orchestration-engine.jpg)
<!--
This is the Gaia-X Federation Services. Gaia-X is a concept to connect all factories to exchange data. For example, if I am a car manufacturing company, we need to calculate the total CO2 usage, which is, of course, for the good of the environment. In this case, a car manufacturing company creates one car after getting a lot of parts from other companies. To do this, we need to gather CO2 data for each machine and each part, and then we can calculate the total CO2 emission per car. In this case, of course, we need to use a standard environment and standard software to retrieve all of the CO2 emission data from other companies. So, they published the Gaia-X Federation Services, and one of the components is Node-RED. This has been hosted by the Eclipse Foundation since 2023.
As I said, the Gaia-X Federation Services workflow engine is based on Node-RED. This is a customized user interface, but internally they use Node-RED. Of course, my flows will work in that environment.
-->
---
# Opera Browser
Opera Software adopted Node-RED for their browser, Opera GX for smart home use cases
  - Getting your room ready for watching movies
  - Syncing the colors of smart bulbs with the theme of Opera GX

https://github.com/operasoftware/opera-smart-home

![h:400 bg right:50%](images/opera.png)
<!--
Recently, Opera released some great news: they adopted Node-RED in their Opera GX browser for smart home use cases. For example, when a user watches a movie, they might want to control the speaker volume, room lights, and window shades. Using Node-RED, Opera GX automatically controls home devices. Syncing the color of smart bulbs based on the theme of Opera GX is another use case for the Opera browser. If you want to see the Opera browser use case, please access their GitHub website.
-->
---
## Advanced features
Features to improve developer experiences
- Project feature (Git functionality)
  - Managing flows
  - Tracking changes
- Flow Linter
- Flow Debugger
<!--
Today, I will explain three features. The first is the Project Feature, which is based on Git functionality, and I will explain it later. After that, I will explain the Flow Linter and Flow Debugger. From now on, we will use the GitHub repository which I shared before the session. Please access that URL to proceed with our hands-on.
-->
---
# Issues without project feature
We encounter the following issues in default setting.

![h:400](images/issues.webp)
<!--
First, I will explain the issues you might face without the Project Feature, meaning in the default environment of Node-RED. In the default environment, developers tend to encounter these issues. For example, Node-RED can accommodate a lot of flows. In this case, sometimes one component might use a lot of CPU, and it affects the entire environment. So, we need to separate the environments based on the application, of course.
Without the Project Feature, in the default Node-RED environment, Node-RED cannot manage information about when and by whom a flow was modified. So, if we encounter an issue in the application, we cannot investigate who modified the flow. The last one is documentation. As you know, on a GitHub repository, developers use Markdown documents. But if developers use documentation files like Google Docs or Microsoft Word, it is not a common way to share usage instructions for Node-RED. As a result, other developers may not understand the contents, and developers need to continuously update the document. Sometimes, it is a little difficult to reflect the changes in a Word document.
-->
---
# Solution with project feature
Project feature solves the previous issues.

![h:400](images/solution.webp)
<!--
To solve this situation, we recommend the Project Feature. Firstly, the Project Feature supports switching between projects. A developer can select and switch between projects, and each project contains one application inside. The second solution is version control of the flow. In the Project Feature, Node-RED internally uses Git commands to record history. Using this standard method, a flow developer can control the version of their flow. Today, we will not be using a remote Git repository to share the Node-RED flow. But if we share the Node-RED flow to a GitHub repository, other developers can easily understand the documentation and the history of changes.
-->
---
# Flow Linter
Provides real-time feedback same as code linter

- Supprted potential issues:
  - http-in node without http-response node
  - Looping flows
  - Overlapping nodes
  - Unset node names
- Custom rules:
  - Recommendation of English node names

![h:600 bg right:40%](images/flowlinter.png)
<!--
Next is the Flow Linter. This is the same as a general linter for other programming languages. For example, if we use JavaScript, we use ESLint, and if we use Python, we use Flake8. So, when we use Node-RED, we use the Flow Linter. The Flow Linter provides real-time feedback, same as other code linters. It alerts you to potential issues, such as an HTTP In node without an HTTP Response node, looping flows, overlapping nodes, and unset node names. If we want to create custom rules, we can create our own. For example, in our case, we created a custom rule to recommend English node names in a global company. In some cases, local people use their local language. For example, Japanese developers tend to use Japanese in comments or node names, but this linter flags custom flows that use a local language instead of English.
-->
---
# Flow Debugger
Provides same user experience as code debugger
- Creating breakpoints 
- Pausing flows
- Inspecting messages
- Step by step execution

<!-- TODO: injectとdebugでフローデバッガ設定の画面 -->
![h:600 bg right:40%](images/debugger.png)
<!--
The Flow Debugger also provides the same user experience as a code debugger. For example, Visual Studio Code supports debugger functionality. Node-RED provides the same user interface and developer experience for its users. We can create breakpoints on the nodes. We can stop the flow, and we can inspect the messages at the breakpoints. We can also step through the flow.
-->
---
# Conclusion
- We learned the advanced features of Node-RED
  - Project feature 
  - Flow Linter
  - Flow Debugger
- Development example of Chat UI application

-> I believe that you will develop the great flows using these features and example.
<!--
Today, we will run the advanced features of Node-RED. The first is the Project Feature, the second is the Flow Linter, and the third is the Flow Debugger. We also developed an example chat UI application. I believe that you will develop great flows using these features and examples. Thank you for listening. Thank you for attending this hands-on session. That's all. Thank you.
-->
---
# Node-RED Conference 2025
- Date: Tuesday, November 4, 2025
- Location: Online
- Speakers: Intel, FlowFuse, Victron Energy, Fluidy Financial Services, City of Morro Bay / GCIS and more
- Registration: Free
https://nrcon.nodered.org/

![h:380 bg right:40%](images/nrcon.png)

<!--
---
![bg cover](images/title4session.png)

---
## Setup Node-RED environment on GitHub codespaces

## Simple demonstration

---
# Chat application with an interactive user interface and a Granite model

To realize modern factory systems, Node-RED can easily connect to the devices in the factory and state-of-the-art AI such as Granite Model. 
-->