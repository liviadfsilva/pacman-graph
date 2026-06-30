# Pac-Man Contribution Graph 👻

## About ✨
This is a step-by-step guide on how to add a Pac-Man contribution graph to your Github README profile.

<br/>

<div align="center">
  <img width="576" height="324" alt="pacman-gif" src="https://github.com/user-attachments/assets/4103a984-1c8c-4982-8f31-aae9cfe37e89" />
</div>

<br/>

## Step by Step 👣

### 1. Create a README.md
If you haven't already, create a repository named exactly the same as your github username.

<br/>

### 2. Set up a github workflow
In your repository, go to Actions > Set up a Workflow Yourself, then paste this in the main.yml file

```
name: Generate pacman animation

on:
  schedule: # runs every 24 hours
    - cron: "* */24 * * *"

  workflow_dispatch:
  push:
    branches:
      - main

jobs:
  generate:
    permissions:
      contents: write
    runs-on: ubuntu-latest
    timeout-minutes: 5

    steps:
      - name: Generate pacman contribution graph
        uses: abozanona/pacman-contribution-graph@main
        with:
          github_user_name: ${{ github.repository_owner }}

      - name: Push pacman graph to output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}

```

<br/>

### 3. Add the graph to your profile README
Add the following to your README.md file, replacing "your-username" for your own username.

```
<picture>
  <source 
    media="(prefers-color-scheme: dark)" 
    srcset="https://raw.githubusercontent.com/your-username/your-username/output/pacman-contribution-graph-dark.svg"
  >
  <source 
    media="(prefers-color-scheme: light)" 
    srcset="https://raw.githubusercontent.com/your-username/your-username/output/pacman-contribution-graph.svg"
  >
  <img 
    alt="Pacman contribution graph" 
    src="https://raw.githubusercontent.com/your-username/your-username/output/pacman-contribution-graph.svg"
  >
</picture>

```

<br/>

### 4. Commit the changes
Now you can enjoy your own pac-man contribution graph.

###### Have fun! 🩷
