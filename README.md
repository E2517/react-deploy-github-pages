## Available Scripts

### `npm i gh-pages`

```
 "homepage": "https://e2517.github.io/react-deploy-github-pages/",

  "scripts": {
        "start": "react-scripts start",
        "build": "react-scripts build",
        "test": "react-scripts test",
        "eject": "react-scripts eject",
        "predeploy": "npm run build",
        "deploy": "gh-pages -d build"
    },
    
```

# OPTION 1 - LOCAL

### `npm start`

Runs the app in the development mode.<br />
Open [http://localhost:3000](http://localhost:3000) to view it in the browser.

### `Go to Settings`

GitHub Pages should be active and show a link

### `npm run deploy` local computer

### `git push` local computer

Open [GitHub pages](https://e2517.github.io/react-deploy-github-pages/) to view it in GitHub

# OPTION 2 - GITHUB ACTIONS

### `Go to Terminal and create a new SSH public/private key`
```
cd ~/.ssh
ssh-keygen -t rsa -b 4096 -C "$(git config user.email)" -f gh-pages-actions -N ""

```
### `Go to Settings -> Deploy Key and copy public key with writen`

### `Go to Settings -> secrets and copy private key`


