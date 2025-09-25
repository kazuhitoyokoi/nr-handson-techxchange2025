# Using version control for Node-RED flows

## (1) Create your first flow
In this tutorial, we will use the simplest flow consisting of inject and debug nodes. After placing these nodes in the central workspace, create the wire between the nodes. Then press the deploy button to run the flow on the Node-RED backend server.

Press enter or click to view image in full size

When you click the inject node’s left button, the inject node triggers the message to the wire. From the wire, the debug node connected to the inject node outputs the received timestamp number to the debug tab of the sidebar.

## (2) Change the status of the flow file to the staging
The next step is to change the status of the first flow to staging. The staging state is the Git principle equivalent of “git add” to select files that should be committed to the version. Once the files are ready to commit, you make the record with the message, timestamp, and developer information in the case of the general step. In another case, we can also restore the flow to the previous state. In the next step, we will try both procedures to perform the commit after changing the flow status to staging and then restore the previous flow. On the History tab, there are two sections, “Local Changes” and “Commit History”, as you can see in the screenshot.

Press enter or click to view image in full size

The Local Changes section is used to manipulate the local flow and associated files to add and remove them from the history. (“Commit History” is an area to check the recorded history. I will explain it later). In addition, the “Local Changes” section is divided into “Local files” and “Changes to commit”. In the next step, we will use the Local Changes section first.

Press enter or click to view image in full size

Click the plus button on the flow file that has the “Stage change” tooltip. Clicking the plus button changes the status of the flow file to staging status and moves the flow file to the “Changes to commit” section, which means it is ready for commit.

## (3) Commit the change with a message
The next step is to use the “Changes to commit” section. To commit to history with a specific message, click the “Commit” button in this section.

Press enter or click to view image in full size

This will bring up the text area at the bottom of the section, where you can enter your commit message. As an example message, I typed “The first flow” into the area and then clicked the “Commit” button at the bottom of the text area.

Press enter or click to view image in full size

If you’re familiar with the Git command, it might be easier to explain that “git commit -m <message>” was executed internally.

It deletes all working files from both sections within the “Local Changes”. This means that the file is recorded in the version history. When you open the “Commit History” section, there is a version history that includes the commit that was made.

Press enter or click to view image in full size

At this point, the initial procedure for adding the commit to the version history is complete. As the next step, I will modify the flow and return it to the state of “The first flow”.

## (4) Modify the flow
As an example of modifying the flow, the template node is inserted between the inject and debug nodes. To add the node to the flow, search and pick the template node from the palette, then release the node on the wire.

Press enter or click to view image in full size

When the inject node’s button is clicked in this flow, the template node creates a new message, “This is the payload: <timestamp>!”. Using the debug node, you can check this message in the debug tab.

## (5) Restore the flow
If you are having problems with the modified flow, you may want to revert to the previous flow, which you have named “The first flow”. To revert the flow, simply click the revert arrow button with the tooltip “Revert Change” in the “Local files” section of the “Local Changes” panel.

Press enter or click to view image in full size

After clicking the button, the following notification dialog will appear. Of course, you should press the “Revert Changes” button in this dialog.

Press enter or click to view image in full size

The flow editor immediately reverts the flow to the previous commit. So you can see the previous flow, which only consists of the inject and debug nodes.

Press enter or click to view image in full size

As I explained above, the flow development is recoverable using Git’s integration functionality. All states of operations are stored in the persistent local filesystem. So even if you close or reload your browser, you can still recover your flow.
