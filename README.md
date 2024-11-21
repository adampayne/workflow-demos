# workflow-demos
Demos of GitHub actions

Created a react app and then deploy to an Azure App Service instance.

> npx create-react-app my-app

Test that this can run:

> cd my-app
> npm start

This launches on http://localhost:3000/

Make the workflow file
./github/workflows/github-actions-demo.yml

The below content will create a workflow that simply checks out the current code each time main is updated
```
name: Build and deploy
'on':
  workflow_dispatch: null
  push:
    branches:
      - main
  pull_request:
    branches:
      - main
permissions:
  id-token: write
  contents: read
jobs:
  build:
    name: Build
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
        name: Checkout self

```