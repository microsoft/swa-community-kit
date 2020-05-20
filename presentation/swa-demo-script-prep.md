# Demo script

Here is one possible demo script for presenting Azure Static Web Apps.

## Your Desktop

1. Screen resolution to 1920x1080 (i use switchresx to do this )
1. clear desktop of all non essential apps
1. hide the date and time from the screen
1. use a blank desktop background or the build background
1. vs code open to demo (hello-build or whatever you name your repo)
1. browser tabs open
   - https://aka.ms/tryjamstack (and then go to the "static web apps" search)
   - https://www.shopathome.dev (or your finished version of the app)
   - https://github.com/johnpapa/shopathome (or your version of the finished repo)
   - https://github.com/johnpapa/hello-build
   - Your Shop At Home in the Portal

### Add the snippets to VS Code

1. Open VS Code
1. Open the command palette by pressing **F1**
1. Type and select **Preferences: Configure User Snippets**
1. Select **json.json**
1. Replace (or merge) the contents of the file with the three snippets in the _swa-snippets.json_

These 3 snippets will be useful in the demo:

| Snippet              | Description                                                                                                                                      |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| `swa-fallback`       | Adds the fallback route for _routes.json_                                                                                                        |
| `swa-auth-providers` | Add the routes to block google and facebook auth providers                                                                                       |
| `swa-restrict-api`   | Add the routes to restrict all API calls to authenticated users, and GET discount and PUT, POST, DELETE for requests to auth role of "preferred" |

## Prepare in advance

You'll want 2 apps:

1. A working app and repo that you won't modify. Great for showing custom domains and auth, so you dont need to keep building.

1. A repo without the routes.json or workflow, and not deployed to SWA yet.

### Prepare the demo app

These steps will give you an app you can have ready to go. With everything ready, for the demos:

- https://github.com/johnpapa/shopathome/generate
- name it hello-build
- remove workflow file (in the repo) - this stops it from running the action against the wrong SWA
- delete _routes.json_ (in the repo)
- git clone git@github.com:johnpapa/hello-build.git
- cd hello-build
- cd svelte-app && npm install (replace svelte with angular, react, svelte or vue)
- cd ..
- cd api && npm install
