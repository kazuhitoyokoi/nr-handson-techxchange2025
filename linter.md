# Flow Linter
A code linter is a common feature in the programming to check for potential errors in the code. For example, we use ESLint for JavaScript and flake8 for Python programming. The Node-RED project also provides Flow Linter, which is same idea as the code linters. Since Node-RED is visual programming tool, Flow Linter provides error sugesstions on not only for JavaScirpt code in function nodes but also for flow-based programming. In this material, we will focus on the both linter rules.

# Linter rules
## function-eslint
To observe the behaivor of Flow Linter in a funciton node, place the function node and write the following code in the node property of the function node.

```
let a;
return msg;
```

![](images/nrlint-function.png)

In this code, the variable `a` is node used. Therefore, after closing the node property UI, a warning appears on the linter tab in the sidebar.

![](images/nrlint-function2.png)

## no-loops
In flow-based development, developers sometimes create loops in the flow. This is similar to an infinite loop in the general programming languages. To avoid this situation, the Flow Linter notifies looping flows. For example, if two function nodes create a loop, the Flow Linter tab displays a warning message, "loop detected".

![](images/nrlint-loop.png)

## no-overlapping-nodes
There is another issue in flow-based development. When developers put the nodes in the workspace, they sometimes place one node on the another node. In this case, the node behind the other node is not visible. In this situation, the Flow Linter shows a warning message, "Overlapping nodes" on the linter tab. 

![](images/nrlint-overlapping.png)

## no-unconnected-http-nodes
In the Node-RED flow editor, a pair of http-in and http response nodes is used to define an HTTP endpoint. If only an http-in node is used in the flow, the HTTP client cannnot recieve the response from the HTTP request. To notify the missing pair, the linter tab displays the following messages.

![](images/nrlint-httpinresponse.png)

## no-duplicate-http-in-urls
In the one Node-RED environment, developer cannot define more than two REST APIs which has the same endpoints. If developer defines the same endpoint such as "/api" in the two http-in nodes, the linter tab displays an alert message.

![](images/nrlint-duplicatedhttpin.png)

## Conclusion
Node-RED is visual programming tool that makes development easy. However, there are unexpected issues related to visual programming. The Flow Linter is one of the tool that solves these issues.
