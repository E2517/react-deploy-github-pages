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

### `Go to Settings (profile) -> Developer tools`

### `Go to TOKEN -> generate a new token with repo, write, read and workflow`

### `Go to Settings -> Secrets and paste token`

```
name: CI/CD React

on:
  workflow_dispatch:
  push:
    branches: [ master ]
  pull_request:
    branches: [ master ]

jobs:
  build:

    runs-on: ubuntu-latest

    strategy:
      matrix:
        node-version: [12.x]

    steps:
    - name: Checkout repository
      uses: actions/checkout@v2

    - name: Set up Node.js ${{ matrix.node-version }}
      uses: actions/setup-node@v1
      with:
        node-version: ${{ matrix.node-version }}

    - name: Install dependencies
      run: npm install

    - name: Run the tests and generate coverage report
      run: npm test -- --coverage

    - name: Build
      run: npm run build

    - name: Deploy
      run: |
        git config --global user.name $user_name
        git config --global user.email $user_email
        git remote set-url origin https://${github_token}@github.com/${repository}
        npm run deploy
      env:
        user_name: 'github-actions[bot]'
        user_email: 'github-actions[bot]@users.noreply.github.com'
        github_token: ${{ secrets.PERSONAL_ACCESS_TOKEN }}
        repository: ${{ github.repository }}
        
  ```      
        
