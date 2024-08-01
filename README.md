
### Hello, My name is Victória Tassi! 🌹

<img align="right" height="150" src="https://pa1.aminoapps.com/7200/49f80fa06aa8c8500d2ee22fe51b6dd2ce6dde52r1-540-302_00.gif"  />

[![Instagram](https://img.shields.io/badge/Instagram-E4405F?style=for-the-badge&logo=instagram&logoColor=white)](https://www.instagram.com/victoriatassi/)
[![Linkedln](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/victoria-tassi-574694304/)


![Anurag's GitHub stats](https://github-readme-stats.vercel.app/api?username=Tassizinha&show_icons=true&theme=buefy)

![Top Langs](https://github-readme-stats.vercel.app/api/top-langs/?username=Tassizinha&hide_progress=true&theme=buefy)

<br clear="both">

<img src="https://raw.githubusercontent.com/Tassizinha/Tassizinha/output/snake.svg" alt="Snake animation" />


name: Generate snake animation

on:
  schedule: # execute every 12 hours
    - cron: "* */12 * * *"

  workflow_dispatch:

  push:
    branches:
    - master

jobs:
  generate:
    permissions:
      contents: write
    runs-on: ubuntu-latest
    timeout-minutes: 5

    steps:
      - name: generate snake.svg
        uses: Platane/snk/svg-only@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: dist/snake.svg?palette=github-dark


      - name: push snake.svg to the output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}





