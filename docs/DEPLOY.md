
# Step 1: Create a repo
* Create a new github repo 
* The repo should be initially empty (mo README, no .gitignore, no LICENSE) 

The reason we are creating an empty repo is that we will be pulling in starter code form another repo in a later step

# Step 2: Clone your repo
cd in the directory where you plan to do your work (ex. ~/cs48)
 
copy the URL for the new repo you created. That will for example be https://github.com/ucsb-cs48-s20/cgaucho_deployment.git  but with cgaucho replaced with your GitHub id and deploymet replaced with what you decided to call the repository. 
 
* `git clone repo-url-goes-here` 
 cd into that directory 

# Step 3: Add remote for starter code 
 type the command below into your terminal (you should be in your directory that you created)
 `git remote add starter https://github.com/ucsb-cs48-s20/project-s0-t2-env.git`

# Step 4: Pull remote into local repo
 Now we are gong to pull from the starter code remote into the lcoal repo and then push to the origin repo
* `git pull starter master`
* `git push origin master`
 At this point you should be able to see your repo listed on github and you should see that it has all of the files from the starter repo

# Step 5: See example of completed app
The example here shows what the app looks like when it is fully deployed on the web
* https://cs48-s20-s0-t2-prod.herokuapp.com/
You should be able to search any city you want and click on said city and be taken to a page that provides information about the environmental data for that city 

You should be able to login and logout:
* only once you logged in will you be able to see the individual user page 
* on the individual user page you should be able to input personal data
  
Once you've completed this lab you should be able to: 
* run this app locally
* deploy this app to the web address 


# Step 6: Install node (if you didn't already do so for lab00)
* If you are working on CSIL, you may skip this step, because as of this writing (April 12, 2020), a sufficient version of node is installed on CSIL:
```
[pconrad@csil-05 ~]$ node --version
v10.16.3
[pconrad@csil-05 ~]$ 
```
* You may also skip this step if, when you type the command `node --version` on your local system. you see a version that is `10.*` or higher.
* Otherwise, follow the instructions here for installing node:

Additional installation advice for specific platforms can be found here:
* MacOS: <https://ucsb-cs48.github.io/jstopics/node_macos/>
* Windows: <https://ucsb-cs48.github.io/jstopics/node_windows/>
* Linux: <https://ucsb-cs48.github.io/jstopics/node_linux/>

When you have finished with those instructions, you should be able to do each of these at the terminal prompt:
* type `node --version` and get a number that is `10.*` or higher (e.g. `v10.16.3`)
* type `npm --version` and get a version number (as opposed to `command not found`)
* type `npx --version` and get a version number (as opposed to `command not found`)


# Step 7: Type `npm install`

 The first time you clone this repo, as well as any time you pull/switch branches, you should update the project's 
 dependencies by running `npm install`

So, first make sure that you have done a `cd` into your proper repo, and then type:

```
npm install
```

You should see a lot of output, and with luck no error messages.
* Special note for MacOS users: if you see `gyp: No Xcode or CLT version detected!` and other errors about `gyp`, then 
  check the page <https://ucsb-cs48.github.io/jstopics/node_macos/> for instructions on fixing this.  
  * The short version is that you may need to reinstall the XCode command line tools.  This takes 3-5 minutes on a decent home internet connection.
  * After reinstalling the XCode Command Line tools, repeat the `npm install` command and the errors related to `gyp` should go away.
  
You may ignore these warnings that appear when you do npm install:
```
npm WARN bootstrap@4.4.1 requires a peer of jquery@1.9.1 - 3 but none is installed. You must install peer dependencies yourself.
npm WARN bootstrap@4.4.1 requires a peer of popper.js@^1.16.0 but none is installed. You must install peer dependencies yourself.
```

Despite the note that `you must install` these peer dependencies, in fact, you do not need to install `jquery` and `popper`. The reason is that we're installing bootstrap is only for its stylesheets, not for the javascript-based component implementations that it has. We already have `react-bootstrap` as a dependency, which reimplements those javascript-based components in react, completely removing the need for the bootstrap implementations.

# Step 8: Configuration/Set up of OAuth for Localhost (If you did not do so in lab00)  

Our repo uses Google OAuth for logins/logouts.  Before we can run the application on localhost, we need to do some configuration.

The instructions for doing this configuration are linked to in the README.md file of the starter repo of lab00_nj, which you can read here: <https://github.com/ucsb-cs48-s20/demo-nextjs-app/blob/master/docs/auth0-localhost.md> 

**If you have not done this at all start from the beginning**
**If you have done this before you can start from "Setting up Auth0 for localhost" *register a new application***

When creating a name make it more applicable rather than lab00, and after the All done! come back to these instructions

# Step 9: Adding more to our .env file

As you may have noticed now our AUTH0_DOMAIN, AUTH0_CLIENT_ID, and AUTH0_CLIENT_SECRET are filled however there are a lot more fields that we need to complete in order for our repo to work properly 

# Step 9a: Adding the Longitude/Latitude API key 

Visit this website: <https://opencagedata.com/api#quickstart>
* Click on sign up for your free API Key 
* Fill out the information prompted 
* Check your email and you should have received an API Key sent to you 
* In your .env with the API key you just received fill in LONGLAT_KEY=       

# Step 9b: Adding the Air Quality API key 

Visit the website: <https://aqicn.org/data-platform/token/#/>
* Fill out the form 
* Check your email and click confirm 
* In your .env with the API key you just received fill in AQI_KEY=   

# Step 9c: Adding the login secret

Copy and paste this directly into your .env 
`POST_LOGOUT_REDIRECT_URI="http://localhost:3000"
REDIRECT_URI="http://localhost:3000/api/callback"`

This refers to the redirect url for when you logout of your oAuth. It will take you automatically back to the homepage which on localhost is just localhost:3000

When we deploy this to heroku we will change these to correlate to Heroku 

# Step 9d: Adding the mongodb connection 

* Go to mongodb.com, click sign in and create an account
* Under Shared Clusters "create a cluster". 
* Set your cluster name to be environment and create the cluster 
 * It takes a couple of minutes to set up so just smile and wait 
* Click on Collections 

![mongo db](MongoDB.png)

* Click on Add My Own Data 
* Set the database name to be environment and the collection to be called cities inside the databases
* After you are done click Connect 
 * click add your current IP address
 * click on create a MongoDB user (this can have any username and password) 
 * click on connect your application
  * copy the connection string and put it in .env under MONGO_CONNECTION_STRING






 
 










  