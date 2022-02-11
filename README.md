# CI/CD

Could you explain CI/CD? - CI is continuous integration. This involves  CI/CD is a method to frequently deliver apps to customers by introducing automation into the stages of app development. The main concepts attributed to CI/CD are continuous integration, continuous delivery, and continuous deployment.

# Creating an SSH Connection

1. Generate SSH key-pair on localhost
2. Put the lock onto GitHub, copying the public SSH key onto GitHub
3. Create a new repo for CICD on our GitHub

continuous integration - every time i do a commit and push, this should automatically integrate from localhost onto github and make it available on AWS
continuous delivery - changes code on aws instance after testing
continuous deployment - changes code live and pushes the changes live (e.g. npm starting for you)
file.pub - key to get into github account using secure shell

ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
generates SSH key-pair
enter file in which to save key
enter passphrase (empty if none)
generates .pub file which is the key