<div id="header" align="center">
    <img src="https://media.giphy.com/media/iicDrNGWxHmDrIni6j/giphy.gif" width="200" />
    <h1 align="center">Hi 👋, I'm Zephyr</h1>
    <h3 align="center">A passionate Peruvian frontend developer who is always willing to help anyone who needs it.</h3>
</div>

---

### 👨‍💻 About Me:
- 🔭 I’m try to learn new things
- 🌱 I’m currently learning JavaScript and React
- 💬 I'm trying to find a job as an intern
- 📫 Discord: Zephyr#4276
- 😄 Pronouns: he/him
- ⚡ Fun fact: I drink 1-2 coffees per day.

---

<div align="left">
    <h2>🔨 Languages and Tools:</h2>
    <div>
        <img src="https://github.com/devicons/devicon/blob/master/icons/html5/html5-plain.svg" title="HTML5" alt="HTML" width="40" height="40"/>&nbsp;
        <img src="https://github.com/devicons/devicon/blob/master/icons/bootstrap/bootstrap-original.svg" title="boostrap" alt="boostrap" width="40" height="40"/>&nbsp;
        <img src="https://github.com/devicons/devicon/blob/master/icons/css3/css3-original.svg" title="css" alt="css3" width="40" height="40"/>&nbsp;
        <img src="https://github.com/devicons/devicon/blob/master/icons/java/java-original.svg" title="java" alt="java" width="40" height="40"/>&nbsp;
        <img src="https://github.com/devicons/devicon/blob/master/icons/androidstudio/androidstudio-original.svg" title="android" alt="android" width="40" height="40"/>&nbsp;
        <img src="https://github.com/devicons/devicon/blob/master/icons/trello/trello-plain.svg" title="trello" alt="trello" width="40" height="40"/>&nbsp;
        <img src="https://github.com/devicons/devicon/blob/master/icons/visualstudio/visualstudio-plain.svg" title="vstudio" alt="vstudio" width="40" height="40"/>&nbsp;
        <img src="https://github.com/devicons/devicon/blob/master/icons/vscode/vscode-original.svg" title="vscode" alt="vscode" width="40" height="40"/>&nbsp;
        <img src="https://github.com/devicons/devicon/blob/master/icons/git/git-original.svg" title="git" alt="git" width="40" height="40"/>&nbsp;
    </div>
</div>

---
<h2 align="left">📖 Stats</h2>
<img align="center" src="https://github-readme-stats.vercel.app/api?username=Zephyr-GN&theme=dark" alt="Zephyr-GN" />
<p><img align="center" src="https://github-readme-streak-stats.herokuapp.com?user=Zephyr-GN&theme=dark" alt="Zephyr-GN" /></p>

---

<h2 align="left">✨ Actitity</h2>
<p><img align="center" src="https://lanyard.cnrad.dev/api/398248330637082626" alt="Zephyr-GN" /></p>

# GitHub Action for generating a contribution graph with a snake eating your contributions.

name: Generate Snake

# Controls when the action will run. This action runs every 6 hours.

on:
  schedule:
      # every 6 hours
    - cron: "0 */6 * * *"

# This command allows us to run the Action automatically from the Actions tab.
  workflow_dispatch:

# The sequence of runs in this workflow:
jobs:
  # This workflow contains a single job called "build"
  build:
    # The type of runner that the job will run on
    runs-on: ubuntu-latest

    # Steps represent a sequence of tasks that will be executed as part of the job
    steps:

    # Checks repo under $GITHUB_WORKSHOP, so your job can access it
      - uses: actions/checkout@v2

    # Generates the snake  
      - uses: Platane/snk@master
        id: snake-gif
        with:
          github_user_name: Zephyr-GN
          # these next 2 lines generate the files on a branch called "output". This keeps the main branch from cluttering up.
          gif_out_path: dist/github-contribution-grid-snake.gif
          svg_out_path: dist/github-contribution-grid-snake.svg

     # show the status of the build. Makes it easier for debugging (if there's any issues).
      - run: git status

      # Push the changes
      - name: Push changes
        uses: ad-m/github-push-action@master
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          branch: master
          force: true

      - uses: crazy-max/ghaction-github-pages@v2.1.3
        with:
          # the output branch we mentioned above
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
