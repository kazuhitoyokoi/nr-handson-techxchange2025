# Using debugger
Code debugger is also common tool in general programing languages. When we use Visual Studio Code in Python programming, we set the break points in the line of code. We can investigate the variables at the break points while executing code.
Flow debugger provides the same developer expriences on Node-RED flow editor. This tutorial explains the steps to use the flow debugger.

## Enabling debugger
As the default, flow debugger is disabled in flow editor. Therefore, developer need to open the debugger tab on the right side bar and turn on the debugger by clicking the switch.

![](images/enabling-debugger.png)

## Setting break point
After enabling the flow debugger, you can add the break points on the ports of the nodes. Once mouse pointer cover the port, you can see the shadow of the break point.

![](images/breakpoint.png)

After clicking the shadow, the break point is successfully added to the port. You can see the assigned break points on the debugger tab.

![](images/breakpoint2.png)

## Stopping flow
Once start the flow, the flow execution will be stopped at the break point. You can see the message payload in the debugger tab.

![](images/stoppingflow.png)

After checking the message payload, you can click the "Resume flow" button to continue the flow execution.

![](images/restartflow.png)

If you click the "step flow" button next to the "Resume flow" button, the messsage will be sent to the next node on by one.

# Conclusion
This tutorial explained how to use the flow debugger. Without flow debugger, developers tends to use the debug node to check the message payload. However, using debug node requires to change the flow. Therfore, undo and redo are little bit troublesome. In terms of the git version history, commit of placing debug node in the flow is not related to the flow logic. Using flow debugger, developers can check the message payload without changing the flow.