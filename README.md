## Deploy to surge.sh

guide : https://github.com/yavisht/deploy-via-surge.sh-github-action-template
```yml
name: Deploy Website

on: [push]

jobs:
  build:
    runs-on: ubuntu-latest
    name: Deploying to surge
    steps:
      - uses: actions/checkout@v1
      - name: Install surge and fire deployment
        uses: actions/setup-node@v1
        with:
          node-version: 8
      - run: npm install -g surge
      - run: surge ./ ${{ secrets.SURGE_DOMAIN }} --token ${{ secrets.SURGE_TOKEN }}
  ```

## deploy to firebase

`firebase login:ci --no-localhost` get token

## Deploy to glitch.com

guide: https://github.com/marketplace/actions/glitch-project-sync 

### get project ID 
```bash
https://api.glitch.com/v1/projects/by/domain?domain=faystart-start-page-work
```
The id value will be seen.

### get authtoken

- Open with Firefox https://glitch.com/edit/#!/faystart-start-page-work
- Clicking the Import from GitHub button (Tools > Import and Export > Import from GitHub) from within your Glitch project . 
- Open Firefox - Tools - Web Developer - Network , filter `Authorization`,got the auth token.
