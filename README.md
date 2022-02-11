# CI/CD

Could you explain CI/CD?:
- Continuous Integration is partly a culture that involves frequent code commits and updates, rather than occasional large commits. 
- On top of that, the push should automatically integrate the data from localhost onto github and straight onto the AWS instance without your own manual interaction with the instances. 
- CD stands for either continuous delivery or continuous deployment, depending on how the user wants to approach their pipeline. 
- These both involve automation of further stages of the pipeline. 
- Continuous delivery means that the changes that are uploaded to the repository via continuous integration are automatically bug tested (such as via Jenkins) and then uploaded on the final instance, such as in AWS storage, where the operations team can manually deploy the changes to live. 
- Continuous deployment is the same as continuous delivery, except it's automatically uploaded to the live instance rather than letting the operations team manually handle it, effectively automating the final step that continuous delivery leaves to the operations team.

![cicd](cicd.png)
<br><br>
# Creating an SSH Connection

1. Generate SSH key-pair on localhost.
2. Put the lock onto GitHub, copying the public SSH key onto GitHub.
3. Create a new repo for CICD on our GitHub.
4. Use your ssh key to push changes locally into the SSH key-protected repository.

- file.pub - key to get into github account using secure shell
1. 
    - `ssh-keygen -t rsa -b 4096 -C "your_email@example.com"`
    - Generates SSH key-pair.
    - Enter file in which to save key without writing anything.
    - Enter passphrase (empty if none).
    - Generates .pub file which is the key.
2. 
    - Go onto your GitHub settings, SSH keys and copy and paste the entire key. 
    - You can list the contents of the key by using the '`cat`' command.
3. 
    - Go to your main GitHub page.
    - Click 'repositories'.
    - Create a new public repository, name it something related to CI/CD.
4. 
    - `git init`
    - `git add .`
    - `git commit -m "first commit"`
    - `git branch -M main`
    - `git remote add origin SSHGITCLONELINKHERE`
    - `git push -u origin main`

# Jenkins

- Jenkins default port is 8080

1. Testing to see if Jenkins works
    - Click "New Item"
    - Select "Freestyle Project"
    - Scroll down to the bottom and click "Add Build Step"
    - Select "Shell Commands"
    - Here, you can enter bash commands that will execute when this build is run, such as `uname -a` and `date`
    - Click 'Apply' and 'Save'
    - Build the item by choosing 'Build Now'
    - Click on the item, select the latest build and view 'Console Output' to see the outpout of the bash commands
2. Testing to see if Jenkins works by chaining two items
    - Follow the previous step right until before you select 'Apply' and 'Save'
    - At the bottom, under 'Post-build Actions', select 'Build other projects'
    - Select the first item you created, and tick "Trigger only if build is stable".
    - Now, when you build the new project, it will run the bash commands, and if everything is successful it will automatically build the first project you designed as well, and execute those commands in the same console output.
