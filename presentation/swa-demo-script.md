# Demo script

Here is one possible demo script for presenting Azure Static Web Apps.

## Demo 1 - part a (App)

Estimated time: 5:00 min

Publish the app with these steps:

1. We have a GitHub repo here (https://github.com/hello-build)
1. Create SWA in Azure
   - Go to the open portal tab (https://aka.ms/tryjamstack)
   - create new resource
   - Fill in the subsription & region (ex: papa-hello-build and west us2)
   - Name it papa-hello-build
1. Choose your repo
   - org: johnpapa
   - repo: hello-build
   - branch: master
1. Fill in the locations (see table at top of this doc for framework specifics):
   - app: svelte-app
   - api: functions (intentionally WRONG)
   - artifact: public
1. Press review/create & create
1. Press go to resource (when it appears after 15s) - this triggers your action
1. Show the links on the overview page (workflow file, action, branch, web app)
1. go to GitHub Actions from the link
1. Explore the workflow file in GitHub while it builds
   - show them the app, api and artifact locations (take your time)
   - Go to the folders in GitHub to show them the svelte-app
1. come back to the actions/build ... success ... show link at the bottom of the build output
1. go to portal to click the link, too (easier)
1. hooray it works!
1. and what about SSL? we have that too. (show this in the address bar )
1. and custom domains? let's look at our completed app and see where that is. (show www.shopathome.dev or yours)
1. go to demo's portal and show where to add the custom domain
1. back to our app and refresh on /products
1. oops! 404 - because "products" is not a server side page. It is a client side route.
1. we'll fix that next

## Demo 1 - part b (API)

Estimated time: 4:00 min

Publish the API and add the fallback route for the app:

1. Go to vs code (first time you are here)
1. git pull (because you need to get the workflow file)
1. Create a new branch my-api
1. add routes.json file to your public folder (assets for angular)
1. add fallback routes.json (swa-fallback snippet)
1. oh, look! our api is in the api folder!
1. fix the workflow file (api_location was functions, should now be api)
1. commit
1. push (press ok when prompted)
1. go to GitHub and make the PR
   - this triggers the action for your new branch and PR
   - go to GitHub actions workflow to see it run
1. instead of waiting for this build, let's go see the final product
1. flip to www.shopathome.dev github repo (johnpapa/shopathome)
1. go to the PR in this repo and click the staging URL is added in a comment
1. go to products and discounts
1. notice we now have data!
1. refresh, notice we now have a fallback route!

## demo 2

Estimated time 4:30 minutes.

Add authentication and authorization to the app

1. Auth and Auth
   - Authentication: verifies who you are
1. Authorization: verifies what you can do
1. ASWA supports multiple authentication providers
   - twitter, github, AAD, google and facebook
1. All auth providers "just work"
1. but if we dont want to suport all providers, we can block some providers
1. Go to vs code routes.json file
1. use snippet `swa-auth-providers` BEFORE the fallback route
   - here we are blocking google and facebook. the others will be allowed
   - we also alias the logout route
1. We can restrict API routes to specific roles
1. In routes.json again ...
1. use snippet `swa-restrict-api` BEFORE fallback route
   - products requires authentication with one of our providers
   - discounts requires preferred roles, we'll see how to set roles next
1. but first, commit the changes to routes.json
1. then git push, so our PR is updated
1. go to the shopathome (or your final app) portal
1. Go to Role Management
1. Show them the github invitation you already had with the preferred role
1. Click "Add an invitation" and show how you can add one for your github account
1. Mention how you can generate and copy and send it to the person and they click and accept ( no need to actually do it )
1. In VS Code on one half the screen show routes.json side by side with the browser on the other.
   - www.shopathome.dev
1. Notice we're not authenticated (or logout if you are)
1. We cant see any data in lists or discounts
1. This makes sense. we restricted the products and data apis (see the routes.json)
1. Let's auth with twitter. now we can see the product lists
1. but we cant see discounts
1. This makes sense, as per our routes.json setup
1. Logout of twitter
1. We need to login with a user with a preferred role, which was github!
1. (optionally show the final portal again with the preferred role)
1. Login with github
1. Now we see discounts!
