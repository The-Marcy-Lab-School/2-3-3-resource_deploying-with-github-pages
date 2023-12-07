# Deploying a Vite Project with Github Pages
This resource covers deploying a Vanilla JS Vite app using Github Pages. 

**Table of Contents**
- [Prerequisites](#prerequisites)
- [Configure Vite for Deployment on Github Pages](#configure-vite-for-deployment-on-github-pages)
- [Publish on Github Pages](#publish-on-github-pages)

## Prerequisites

In order to deploy to Github using this guide, you will need 
* A project built using Vite
* A Github repo for that project.

## Configure Vite for Deployment on Github Pages

**Objective(s)**: Prepare for deployment and build the production version of the app.

So, you've built an app - congrats! You can run it locally, but wouldn't it be sweet if everyone on the internet could use it??

Assuming you built that app using Vite, the first make the **production version** of the application. In order to do that, we'll need to configure Vite to create that version in the right location.

Create a Vite configuration file

```sh
touch vite.config.js
```

And put this inside:

```js
import { defineConfig } from 'vite'

export default defineConfig({
  // GitHub Pages expects an index.html in the root directory
  // so just run npm build before pushing to GitHub and this will rebuild our assets to the root
  build: { outDir: '..' },
  // needed for github pages just put the repo name here
  base: '/your-repo-name-here/', 
});
```

Now, run the command

```sh
npm run build
```

This will **compile** the code you've written in your `app/` folder into optimized static files that can quickly be served by Github pages. It will put those files in the root directory of your repo, where Github expects to find an `index.html` file and any associated `assets`.

You can see what this "deployed" version will look like by running the command...

```sh
npm run preview
```

...which will serve the application at http://localhost:4173/

Finally, **commit and push** your new compiled version to Github!

## Publish on Github Pages

**Objective(s)**: Publish your web app!

Deploying your application on Github Pages is about as easy as it gets:

1. Open the repo on Github.com
2. Go to the <kbd>Settings</kbd> tab
3. Find the <kbd>Pages</kbd> section
4. Make sure that **Source** is **Deploy from a branch**
5. Below, set **Branch** to `main` (or whatever branch you're using)
6. Click **Save** and wait a few minutes! You should see the URL of your application.
7. Each time you push a new commit to `main`, your page will redeploy!