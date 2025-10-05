# Chat application with an interactive user interface and a Granite model

Node-RED can easily connect to state-of-the-art AI technologies such as Granite Model. In this tutorial, we will develop Chat application with intractive user interface and Granite Model.
<!--
## Installing Ollama (Not required in hands-on)
To use Granite Model with Node-RED, firstly you need to install Ollama, a HTTP server to provide APIs to use AI models. To install Ollama in the Linux environment, input the following command on your terminal.

```
curl -fsSL https://ollama.com/install.sh | sh
```

After the installation process, you can use the `ollama` command in your environment. To download the Granite model into your Ollama, type the `ollama pull command` as flows.

```
ollama pull ibm/granite4.0-preview:tiny
```

In this case, the command will download the Granite 4.0 tiny model. It takes few minutes to download the model file. After the command process is finished, run the `ollama serve` command.

```
ollama serve
```

Now, on your PC, the REST API has been available. This REST API is compatible API of the OpenAI. Therefore, we can use the common way to connect to the REST API.

### Installing Node-RED dashbaord 2.0 (Not required in the hands-on)

To ceate the user interface of the Chat application, Node-RED Dashboard 2.0 is needed. To install Node-RED 2.0, open the "User Settings" from the "Manage Palette" of the top-right menu in the Node-RED flow editor. 

Select "Install" tab, to open the for the node installation. After typing the `@flowfuse/node-red-dashboard` in the search box, the target node item will be filtered on the below list. Click the `install` button of the `@flowfuse/node-red-dashboard` to install the Node-RED dashbaord 2.0 into your Node-RED environment.
After the installation, you can see the dashboard nodes on the left palette of the Node-RED flow editor.
-->
## Creating Node-RED flow
Firstly, create new project, "chat-app" using project featue.

![](images/createchatapp.png)

After creating the new project for the chat application. You can start to develop the Node-RED flow.

### Creating Node-RED flow to access Ollama server
To create simple flow to access the Ollama server, put the inject node, function node, http request node and debug node with wires as follows.

![](images/flow4ollama.png)

Double-click the inject node to open node property UI. To set the prompt for Ollama server, firstly click time icon next to "millisecounds since epoch" to open the pull down menu of the data type. As the data type of `msg.payload`, select `string` from the menu. After that, you can type the string message in the text input box next to az icon.
Type the message, "What is IBM? Describe it in 10 words."

![](images/inject4ollama.png)

In the function node, input "post data" to the name field and paste the follwoing code to set POST message for Ollama server.

```
msg.payload = {
    "messages": [
        {
            "role": "user",
            "content": msg.payload
        }
    ],
    "model": "ibm/granite4.0-preview:tiny"
};
return msg;
```
![](images/function4ollama.png)

For http request node, the following settings are needed to select or input on the node property UI.
- Method: POST
- URL:
  ```
  http://localhost:11434/v1/chat/completions
  ```
- Return: a parsed JSON object

![](images/httprequest.png)

The node property settings of the debug node is default. After clicking the deploy button, you can access the Ollama server by clicking the left button of the inject node.

![](images/whatisibm.png)

To check the answer from Ollama server, expand the recieved message on the debug tab. You will se the answer in the JSON path of `payload.choices[0].message.content`.

## Creating Simple Chat UI
Node-RED dashboard supports Vuetify UI in the template node. In this matrial, we use the timeline UI provided by Vuetify to show Chat UI.
To create simple Chat UI, place the text input node, function node and green template node in Dashboardd 2.0 with wires as follows.

![](images/flow4simplechatui.png)

On the property UI of the text input node, "Focus leave" checkbox should be turned off because Chat UI unintentionally sends to the request answer from Ollama server when switching the browser pages between dashboard UI page and Node-RED flow editor page.

![](images/focusleave.png)

Only name of the function node was changed to "user comment" to distinguish with other function node created later. In the function node, paste the following code.

```
var tmp = flow.get('data') || [];
tmp.push(
    {
        image: "https://nodered.jp/images/yokoi.jpg",
        message: msg.payload
    }
);
flow.set('data', tmp);
msg.payload = tmp;
return msg;
```

![](images/function4simplechatui.png)

In the template node, replace the existing code with the following code to show Chat UI using Vuetify.

```
<template>
  <v-timeline class="overflow-y-auto" style="max-height:400px">
    <v-timeline-item v-for="item in msg.payload">
      <template v-slot:icon>
        <v-avatar v-bind:image="item.image"></v-avatar>
      </template>
      <v-alert>{{item.message}}</v-alert>
    </v-timeline-item>
  </v-timeline>
</template>
```

Additionally, on the template node property UI, group should be chaned to "[Page 1] Group 1" because the selected default is none.

![](images/template4chatui.png)

To show the Chat UI on the Node-RED dashbaord 2.0, after clicking the deploy button, select the "Dashboard 2.0" tab from the right side bar area. And then click the "Open Dashboard" button on the top right.

![](images/button2dashboard.png)

The dashbaord has the following Chat UI which can support text input and history timeline.

![](images/simplechatui.png)

If you want to clear the chat history which flow context manages internally, you need to clear the flow context manually. Open the "context" tab from the right side bar, and then click the "refresh" button to get the latest data, and click the "Delete" button.

![](images/clearcontext.png)

From the next input on the Chat UI, the timeline will be cleared on the dashbaord.

## Integrating Chat UI with Ollama flow
To integrate two flows which we created, wiring from text input node to the function node which has "post data" as the node name. 

![](images/flow4chatapp.png)

After the http request node, to handle the retrived data, new function node is inserted between http request node and template node. In the function node, input "ai comment" into the name field and paste the following code.

```
var tmp = flow.get('data') || [];
tmp.push({image: "https://2.bp.blogspot.com/-H2eLSLfzvpA/XGjx1UapC6I/AAAAAAABRcA/5Xdh-W7tqk8X1YONndv2B1ykhJ6BRS1bgCLcBGAs/s800/ai_computer_sousa_robot.png", message: msg.payload.choices[0].message.content});
flow.set('data', tmp);
msg.payload = tmp;
return msg;
```
![](images/function4simplechatui2.png)

This code extract answer from AI, and set the answer for the Chat UI. After clicking deploy button, you can use Chat UI on dashboard.

![](images/chatapp.png)
<!-- TODO: スクリーンショット撮り直し -->
