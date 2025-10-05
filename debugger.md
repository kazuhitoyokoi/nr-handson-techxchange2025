# Flow Debugger
A code debugger is also common tool in general programming languages. When using Visual Studio Code for Python programming, we set the breakpoints in the line of code. We can investigate the variables at these breakpoints while the code is executing.
The flow debugger provides the same developer exprience for Node-RED flow editor. This tutorial explains how to use the flow debugger.

## Enabling the debugger
By the default, the flow debugger is disabled in the flow editor. Therefore, the developer needs to open the debugger tab on the right sidebar and turn on the debugger by clicking the switch.

![](images/enabling-debugger.png)

## Setting a breakpoint
After enabling the flow debugger, you can add the breakpoints on the ports of the nodes. Once the mouse pointer covers the port, a shadow of the breakpoint appears.

![](images/breakpoint.png)

Clicking the shadow adds the breakpoint to the port. You can view the assigned breakpoints in the debugger tab.

![](images/breakpoint2.png)

## Stopping flow
Once you start the flow, the flow execution will stop at the breakpoint. You can observe the message payload in the debugger tab.

![](images/stoppingflow.png)

After checking the message payload, you can click the "Resume flow" button to continue the flow execution.

![](images/restartflow.png)

Alternatively, if you click the "Step flow" button next to the "Resume flow" button, the messsage will be sent to the next node one by one.

# Conclusion
This tutorial explained how to use the flow debugger. Without the flow debugger, developers tend to use the debug node to check the message payload. However, using the debug node requires changing the flow. Therefore, undoing and redoing can be a bit troublesome. In terms of the Git version history, commiting the placement of a debug node in the flow is unrelated to the flow logic. With the flow debugger, developers can check the message payload without changing the flow.
