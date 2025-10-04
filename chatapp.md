
```
ollama run ibm/granite4.0-preview:tiny
```

https://www.ibm.com/jp-ja/new/announcements/ibm-granite-4-0-tiny-preview-sneak-peek


```
var tmp = flow.get('data') || [];
tmp.push({ image: "https://nodered.jp/images/yokoi.jpg", message: msg.payload });
flow.set('data', tmp);
msg.payload = tmp;
return msg;
```


```
var tmp = flow.get('data') || [];
tmp.push({ image: "https://2.bp.blogspot.com/-H2eLSLfzvpA/XGjx1UapC6I/AAAAAAABRcA/5Xdh-W7tqk8X1YONndv2B1ykhJ6BRS1bgCLcBGAs/s800/ai_computer_sousa_robot.png", message: msg.payload });
flow.set('data', tmp);
msg.payload = tmp;
return msg;
```


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