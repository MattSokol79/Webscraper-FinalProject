(Jenkins Test)
# Eng74 Final Project
    stage('Push image') {
        /* Finally, we'll push the image with two tags:
         * First, the incremental build number from Jenkins
         * Second, the 'latest' tag.
         * Pushing multiple tags is cheap, as all the layers are reused. */
        docker.withRegistry('https://registry.hub.docker.com', 'dockerhub_id') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
        }

# MVC - Model View Controller
MVC is a software approach used to organise code. The MVC method establishes 3 silos, the Model, View, and the controller.
  * Controller - receives user requests and decides the action to take. It ties together the Model and View
  * Model - The essential components of code.
   Retrieves data required to respond to controller
  * View - Consists of code pertaining to user interface. This would receive  data from the model and determine which webpage should be rendered to meet the users requests.

# What is Flask
Flask is a python-based web development framework. It provides access to a large collection of reusable code and extensions.

# Jenkins
- A webhook is needed in the git repository.
`<jenkins server url>/github-webhook/`

- The ssh pub key is uploaded to the repo, and private key is used in jenkins to monitor any changes on the development branches.
- Jenkins detects changes and merges with main.

# Testing 3

admin 
e25e9690cd6f483baed616cfaacaeb05


All you need to do is push a change to the development branch and the Jenkins pipeline will take it from there automating the process end-to-end