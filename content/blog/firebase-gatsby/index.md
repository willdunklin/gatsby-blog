---
title: Publishing a Gatsby Site on Firebase
date: "2020-05-06T20:50:41.282Z"
description: Process for creating a Gatsby project and adding it to a Firebase instance
---

[Firebase](https://firebase.google.com/) is a Google service for hosting and devloping apps. It can be used with the static site generator [Gatsby](https://www.gatsbyjs.org/) for incredibly simple static hosting.

This blog site was developed with this very methodology using a template provided by [Gatsby's GitHub](https://github.com/gatsbyjs).

---

1. Creating a Gatsby Project

If you haven't installed Gatsby you can do so using:

```
$ npm install -g gatsby-cli
```

*Note: Make sure your npm and node versions are up to date.*

Now to create a project:

```
$ gatsby new tutorial-site
$ cs tutorial-site
```

Alternatively you can include a git repository in the arguments like so:

```
gatsby new tutorial-site https://github.com/user/project
```

---

2. Firebase Setup

Firstly to start you must have a [Firebase Account](https://console.firebase.google.com/).

Now we must install the Firebase CLI.

```
$ npm install -g firebase-tools
```

Now with `firebase` installed run:

```
$ firebase login
```

Now you should be primed to add the Gatsby project to Firebase.

---

3. Adding Gatsby to Firebase

Navigate into your project folder and run the following command:

```
$ firebase init
```

This command will give many promps but it is important you select `Firebase Hosting` as a Firebase product.

If you already have a project, select it, otherwise create a new project with a unique id.

When prompted to select the public directory hit enter. Gatsby's default is public as well.

Finally once initialization is complete edit `firebase,json` to be

```json
{
  "hosting": {
    "public": "public",
    "ignore": ["firebase.json", "**/.*", "**/node_modules/**"],
    "headers": [
      {
        "source": "**/*",
        "headers": [
          {
            "key": "cache-control",
            "value": "cache-control: public, max-age=0, must-revalidate"
          }
        ]
      },
      {
        "source": "static/**",
        "headers": [
          {
            "key": "cache-control",
            "value": "public, max-age=31536000, immutable"
          }
        ]
      },
      {
        "source": "**/*.@(css|js)",
        "headers": [
          {
            "key": "cache-control",
            "value": "public, max-age=31536000, immutable"
          }
        ]
      },
      {
        "source": "sw.js",
        "headers": [
          {
            "key": "cache-control",
            "value": "cache-control: public, max-age=0, must-revalidate"
          }
        ]
      },
      {
        "source": "page-data/**",
        "headers": [
          {
            "key": "cache-control",
            "value": "cache-control: public, max-age=0, must-revalidate"
          }
        ]
      }
    ]
  }
}
```

---

4. Developing on Gatsby

Now is the time to develop your Gatsby site. To see local changes run the command

```
$ gatsby develop
```

This should host a node.js server at `http://localhost:8080` that will automatically update with changes made to the site.

---

5. Publishing to Firebase

Now that you hopefully have a partially functioning Gatsby site we can push the build to be hosted by Firebase.

```
$ gatsby build
$ firebase deploy
```

This should now host your static site at `projectId.web.app` or at the custom domain you set in Firebase.