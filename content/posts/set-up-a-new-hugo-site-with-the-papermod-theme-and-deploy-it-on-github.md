---
title: 'Set up a new Hugo site with the PaperMod theme and deploy it on GitHub'
date: 2025-01-30T22:31:00.034+06:00
draft: false
url: /2025/01/set-up-new-hugo-site-with-papermod.html
---

For Install HUGO on Windows, open PowerShell or cmd with the administrator. and run this command

choco install hugo-extended

1- open cmd

cd desktop hugo new site hugo --format yaml cd hugo git clone https://github.com/adityatelange/hugo-PaperMod themes/PaperMod --depth=1 code .

2- Rename **hugo.yaml** to **config.yml** also remove the base URL for test. dont forget to add

theme: PaperMod

in **config.yml**  
3- Create a new file **.gitmodules** and add those lines to that file.

\[submodule "themes/PaperMod"\] path = themes/PaperMod url = https://github.com/adityatelange/hugo-PaperMod

4- make a new file **.github/workflows/hugo.yaml** and add those line

name: Deploy Hugo site to Pages on: push: branches: - main workflow\_dispatch: permissions: contents: read pages: write id-token: write concurrency: group: "pages" cancel-in-progress: false defaults: run: shell: bash jobs: build: runs-on: ubuntu-latest env: HUGO\_VERSION: 0.141.0 steps: - name: Install Hugo CLI run: | wget -O ${{ runner.temp }}/hugo.deb https://github.com/gohugoio/hugo/releases/download/v${HUGO\_VERSION}/hugo\_extended\_${HUGO\_VERSION}\_linux-amd64.deb \\ && sudo dpkg -i ${{ runner.temp }}/hugo.deb - name: Install Dart Sass run: sudo snap install dart-sass - name: Checkout uses: actions/checkout@v4 with: submodules: recursive fetch-depth: 0 - name: Setup Pages id: pages uses: actions/configure-pages@v5 - name: Install Node.js dependencies run: "\[\[ -f package-lock.json || -f npm-shrinkwrap.json \]\] && npm ci || true" - name: Build with Hugo env: HUGO\_CACHEDIR: ${{ runner.temp }}/hugo\_cache HUGO\_ENVIRONMENT: production TZ: America/Los\_Angeles run: | hugo \\ --gc \\ --minify \\ --baseURL "${{ steps.pages.outputs.base\_url }}/" - name: Upload artifact uses: actions/upload-pages-artifact@v3 with: path: ./public deploy: environment: name: github-pages url: ${{ steps.deployment.outputs.page\_url }} runs-on: ubuntu-latest needs: build steps: - name: Deploy to GitHub Pages id: deployment uses: actions/deploy-pages@v4

5- in the console or cmd run those commands to make a public folder and push to remote.

hugo git init git branch -m master main git add . git commit -m "initial setup" git remote add origin ((((((repourl))))))))) git fetch origin git merge origin/main --allow-unrelated-histories git push -u origin main

type **:qa** and hit enter for close the textbox  
6- go repo settings/pages In the build and deployment section, make it "**deploy from a branch**" to "**GitHub actions**"  
7- for use local live server

hugo server

in console and go **localhost:1313**