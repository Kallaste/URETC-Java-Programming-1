# URETC-Java-Programming
---
The Java programming course offerred by URETC
---

Table of Contents
---


* Introduction  
* Resources  
* Github
* CodeEnvy (IDE)

#### Introduction
---

#### Resources
---

#### Github
---
Each Student should have a github account created in order for the mentors and teachers to keep track of their work. For the most part students do not really need to understand how Git or Github works. **Make sure to remember your username and password for GitHub!**

On a high level, Github is a website that uses a technology called git. Git is used to help keep different versions of your work. Every time you save your work using git, you create a new version. What happens when you made a mistake and saved the wrong thing? Git keeps track of versions so it can bring back the last version before you saved it.


#### CodEnvy (IDE)
---
CodEnvy is an cloud based IDE. This means that it supplies us a functional IDE to compile and debug our Java code all in our browser. Because this is in the cloud and we are using the free tier, expect it to be slow and be patient with it. Setting up a working IDE that integrates with Github takes a few steps which we will talk about now.

##### How to Setup your IDE
1. Create a Red Hat account here [https://codenvy.io/site/login](https://codenvy.io/site/login) (This link can also be used to get back to your workspaces in the future, so make sure to copy the url and save it somewhere). (Red Hat is the owner of Codenvy). (Make sure to confirm your email incase there are issues in the future).
2. Once you've registered it should take you to a website which, if you scroll all the way up, contains a big red button under "Welcome to the Developer Sandbox for Red Hat OpenShift". Click that button and it will ask you to confirm your phone number, follow the instructions until you get to a new button that says something like "Starting your Sandbox". Once you click on that it will ask you which login to use. Use DevSandbox.
3. You should see the following screen:

![alt text](https://i.imgur.com/djsD2Tb.png)
Press on "+Add" on the left handside. You will see a bunch of different options. Click "Samples", then "Java", then click "Create" at the bottom (do not need to change anything here). You will see the following page, you want to click the button circled in red in order to actually into your ide workspace:

![alt text](https://i.imgur.com/2ySiHx2.png)
4. RedHat may ask you for Authorization to continue, similar to this page here:

![alt text](https://i.imgur.com/E6YwbFK.png)
Click Allow, then it will ask you to Update your information. Do this and you should be at the Workspace environment. 
5. You are then presented to page similar to this one:

![alt text](https://i.imgur.com/RKS0ygX.png)
If you do not see the leftside (titled Red Hat CodeReady Workspaces in the image), click the little yellow arrow at the top left of the screen to expand. Red Hat creates a workspace for us, but it needs proper configuration to do what we want, so we will go ahead and deleted the workspace and create another one here. Click on the Worspaces button on the top left of the expanded screen.
6.You will see the workspace created for you. highlight that workspace by pressing the checkbox to the left of it, then click the Delete button on the top right. Like so:

![alt text](https://i.imgur.com/ppS6zQD.png)
7.Once deleted, Click the "Add Workspace" button on the top right of the page. You will be presented with a page that looks like so:

![alt text](https://i.imgur.com/O7tciPU.png)
8.We want to change the content in the text field below. Keep in mind before you read on, the YAML below needs to be updated, do not just copy and paste. Also, make sure the student has their own branch on our Github Repo before continuing. Copy and paste the following configuration, but **KEEP IN MIND THE GITHUB REPO NAME, THE GITHUB REPO URL, AND THE BRANCH PARAMETER NEEDS TO BE EDITED BEFORE CONTINUING**
```yaml
apiVersion: 1.0.0
metadata:
    generateName: java-maven-
projects:
    - name: <name of github repo>
      source:
        type: git
        location: '<link to github repo>'
        branch: <student's github username>
components:
  - type: chePlugin
    id: redhat/java/latest
    preferences:
      java.server.launchMode: Standard
  - type: dockerimage
    alias: maven
    image: 'quay.io/eclipse/che-java11-maven:7.21.2'
    env:
      - name: MAVEN_CONFIG
        value: ''
      - name: MAVEN_OPTS
        value: '-XX:MaxRAMPercentage=50 -XX:+UseParallelGC -XX:MinHeapFreeRatio=10 -XX:MaxHeapFreeRatio=20 -XX:GCTimeRatio=4 -XX:AdaptiveSizePolicyWeight=90 -Dsun.zip.disableMemoryMapping=true -Xms20m -Djava.security.egd=file:/dev/./urandom -Duser.home=/home/user'
      - name: JAVA_OPTS
        value: '-XX:MaxRAMPercentage=50 -XX:+UseParallelGC -XX:MinHeapFreeRatio=10 -XX:MaxHeapFreeRatio=20 -XX:GCTimeRatio=4 -XX:AdaptiveSizePolicyWeight=90 -Dsun.zip.disableMemoryMapping=true -Xms20m -Djava.security.egd=file:/dev/./urandom'
      - name: JAVA_TOOL_OPTIONS
        value: '-XX:MaxRAMPercentage=50 -XX:+UseParallelGC -XX:MinHeapFreeRatio=10 -XX:MaxHeapFreeRatio=20 -XX:GCTimeRatio=4 -XX:AdaptiveSizePolicyWeight=90 -Dsun.zip.disableMemoryMapping=true -Xms20m -Djava.security.egd=file:/dev/./urandom'
    memoryLimit: 512Mi
    mountSources: true
```
Make sure that the student's branch exists!
9. Hit the "Create & Open" Button at the bottom of the page and be patient for things to be set up. You will know the setup is done when you see your GitHub files on the left hand side. If your GitHub files do not show up, please check that your added the GitHub repo name, GitHub repo url, and the branch correctly and try again. You will need to delete your old Workspace to create a new one.
10. Something to keep in mind for when you return to work on your workspace. When you login in to Red Hat, in order to get back to your project files, you need to click on the Workspace named "java-maven-..." in the expanded view. When you click this, your files should come up. The Workspace to click looks like this:

![alt text](https://i.imgur.com/dhWg8Rc.png)
10. Next we are going to setup some configuration in order to save your work to GitHub. You will see on the bottom left corner of the screen there will be a settings icon that looks like this: 
![alt text](https://i.imgur.com/YVkwhDE.png)
11. Click on "Open Preferences". You should see the following: ![alt text](https://i.imgur.com/IyiCQdY.png)
12. You will see a bunch of different categories for preferences, but the first thing you need to click on is "Workspace". Its right under "Search Settings" and to the right of "User". 
13. Once you're in the Workspace section (which should look exactly the same except Workspace is no highlighted instead of Workspace), in the search bar that reads "Search Settings", paste in exactly: "Post Commit Command".  The option should read "Runs a git command after a successful commit." You will want to click the drop down and choose "push". You should see the following: ![alt text](https://i.imgur.com/6rLUtgi.png)
14. Next, search this exactly in the search bar: "Controls whether to enable automatic GitHub authentication for git commands within VS Code.",  You should see a checkbox that has been checked. Make sure this option is unchecked. 
15. Once these are completed you can exit out of the Preferences tab. Now the student should be able to push their changes to GitHub after they commit their changes using their GitHub username and password. For instructions on how to push to GitHub, please follow the below instructions (if you're setting this up for the first time, you should be going there to test that everything works!).


##### How to Push your Changes to GitHub
For these instructions we will go through the process as if I wanted to push my new changes to GitHub.

1. First I would add my changes to my code, as you can see here, the new line I added here is on line 8:

![alt text](https://i.imgur.com/JHZXj4F.png)

You can tell it is a new line because of the green bar right next to the number 8 on the left of the code (the line numbers are there if you did not know).
2. Now I need to *Add* my changes to Git. In order to do this I need to go into the Git screen of the IDE. If you look all the way to the left of your IDE, you will see the button to go there, this is the button circled in red:

![alt text](https://i.imgur.com/UMlN3dB.png)


3. When you click on this you should see the following on the left side:

![alt text](https://i.imgur.com/W25xxsY.png)
4. Under "Changes" you will see all the files where you updated. If any of the files the IDE is saying are being changed look weird (like if it's saying there are changes in a file that should not have changes), use this to fix up those files so that the "Changes" part only has changes you know about. If you hover over your files, so in this example Main.java is the only file we changed, you should see a "+" sign which will add your changes to Git's staging (Think of staging like a final area before we check everything off and send it to GitHub). Click on the + sign for all files under Changes. You will notice that when you click the plus sign for one your files it will go under Staged Changes. Ignore that for now, continue to hit the plus sign for all of your changed files under Changes. 
5. Once all your files are under Staged Changes, You will notice the text field at the top that says "Message (Ctrl Enter to commit on". In this text field, write down information that describes your change. For our example, I added "I am sending this to GitHub", so I will write that there, so it should look like this so far:

![alt text](https://i.imgur.com/yuuXEmz.png)
6. Once you put your comment, press "Ctrl + Enter". This puts the check mark on all the files you added and now the files are ready to be sent to GitHub.
7. At the top of your page it will ask for your "Username", put in your GitHub username and then press Enter.
8. Then it will ask for your Password, put in your GitHub Password.
9. After that, if no issues are present, your changes should be reflected on GitHub! Rinse and repeat for any other changes.
10. You can return back to your file directory by clicking the Icon that looks like two pages on top of one another, above the Magnifying Glass Icon.
