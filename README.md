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


- Here is our Apps home page, which is currently visible on this app and live! So, to showcase the pipeline, lets make a slight change to it -> Lets add a Hello! to let us know that the pipeline has worked (refresh the page to make sure that you havent done anything just yet) 
  - Lets push the update to the dev branch -> As you can see we are currently on the dev branch, lets git add. git commit -m "Added Hello!" git push origin dev.
- Show CI working -> As you can see Jenkins has picked up that there was a push to the dev branch and triggered the CI job, which as mentioned earlier will run tests on the code pushed to the dev branch to ensure that any changes that have been made have not broken the core functionality of the app. So our small addition of Hello! should be fine.
  - As you can see, all of the tests have passed and the job was successful.
- Back out, see CD starts, so as you can see, because the CI job was successful, the continous delivery was triggered, lets have a look inside.
  - So this job actually shows the different stages in a nice format and as you can see it clones the repository and builds the image so this is the docker image that Sam mentioned earlier. So this essentially takes a snapshot of the app and everything it needs to succesfully work when the image is ran in a container. The image is then pushed to a dockerhub repo **show repo** as you can see the last push to the repo was from over an hour ago, so once the job has succeeded we should see this update. And then it cleans the machine. 
- The job has successfully finished **show CDE working** which triggers the CDE job, this job runs the updated version of the app from a docker image which we have just pushed to our dockerhub. **Show updated dockerhub** so the image has been successfully pushed to dockerhub and so if the job succeeds, we should see the app updated with our hello!
  - Go back to site, refresh see hello

- And there is the hello, so as you can see, all that I needed to do, was make a change to the code and push to the development branch, the pipeline then took care of the rest thus showing the power of automation and CICD.
  - So now ill be passing over to Hubert.
