# Profile Redesign Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Redesign GitHub Profile README with dynamic elements, remove "about me" section.

**Architecture:** Single README.md with external SVG embeds + GitHub Actions for scheduled content generation.

**Tech Stack:** GitHub Actions (`platane/snk`, `yoshi389111/github-profile-3d-contrib`), Markdown, shields.io

**Global Constraints:**
- All changes must be compatible with GitHub Markdown rendering
- External services must use HTTPS
- Maintain Dracula theme consistency

---

### Task 1: Rewrite README.md

**Files:**
- Modify: `README.md`

- [ ] **Step 1: Write new README.md content**

Replace entire file with:

```markdown
<div align="center">
  <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=28&duration=3000&pause=1000&color=F7789E&center=true&vCenter=true&width=600&lines=Hi+%F0%9F%91%8B%2C+I'm+best0127;%F0%9F%94%8D+Reverse+Engineering+Lover;%F0%9F%90%8D+Python+Developer;%F0%9F%92%BB+Coding+is+my+passion" alt="Typing SVG" />
</div>

---

<div align="center">

<img src="https://github-profile-trophy.vercel.app/?username=best0127&theme=radical&no-frame=true&no-bg=true&row=1&column=7" width="85%" alt="Trophy" />

<br><br>

<img src="https://komarev.com/ghpvc/?username=best0127&style=for-the-badge&color=F7789E" alt="Profile Views" />

</div>

---

## 🛠️ 技术栈

<div align="center">

<img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python" />
<img src="https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white" alt="Java" />
<img src="https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white" alt="Git" />
<img src="https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white" alt="GitHub" />
<img src="https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black" alt="Linux" />
<img src="https://img.shields.io/badge/Windows-0078D4?style=for-the-badge&logo=windows&logoColor=white" alt="Windows" />

</div>

---

## 📊 GitHub 统计

<div align="center">

<img src="https://github-readme-stats-sigma-five.vercel.app/api?username=best0127&show_icons=true&theme=dracula&hide_border=true&count_private=true&include_all_commits=true" alt="GitHub Stats" width="60%" />

</div>

<div align="center">

<img src="https://github-readme-stats-sigma-five.vercel.app/api?username=best0127&show_icons=true&theme=dracula&hide_border=true&count_all=true&hide=rank,prs_merged,prs_merged_percentage" alt="GitHub Streak" width="60%" />

</div>

<div align="center">

<img src="https://github-readme-stats-sigma-five.vercel.app/api/top-langs/?username=best0127&layout=compact&theme=dracula&hide_border=true" alt="Top Languages" width="60%" />

</div>

---

## 🎲 3D 贡献立方体

<div align="center">

<img src="https://raw.githubusercontent.com/best0127/best0127/main/profile-3d-contrib/profile-green-animate.svg" alt="3D Contributions" width="90%" />

</div>

---

## 🐍 贪吃蛇贡献图

<div align="center">

<img src="https://raw.githubusercontent.com/best0127/best0127/output/snake.svg" alt="Snake" width="100%" />

</div>
```

- [ ] **Step 2: Verify README.md looks correct**

Run: `Get-Content "D:\MyProgram\best0127\README.md"` to confirm the file was written correctly.

- [ ] **Step 3: Commit README.md**

```bash
git add README.md && git commit -m "feat: redesign profile with dynamic elements"
```

---

### Task 2: Create snake contribution GitHub Action

**Files:**
- Create: `.github/workflows/snake.yml`

- [ ] **Step 1: Create directory and write workflow file**

```powershell
New-Item -ItemType Directory -Path "D:\MyProgram\best0127\.github\workflows" -Force
```

Create `.github/workflows/snake.yml`:

```yaml
name: Generate Snake

on:
  schedule:
    - cron: "0 0 * * *"
  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: Platane/snk@v3
        with:
          github_user_name: best0127
          outputs: |
            dist/snake.svg
            dist/snake-dark.svg?palette=github-dark
      - uses: crazy-max/ghaction-github-pages@v3
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

- [ ] **Step 2: Commit workflow**

```bash
git add .github/workflows/snake.yml && git commit -m "feat: add snake contribution action"
```

---

### Task 3: Create 3D contribution cube GitHub Action

**Files:**
- Create: `.github/workflows/profile-3d.yml`

- [ ] **Step 1: Create workflow file**

Create `.github/workflows/profile-3d.yml`:

```yaml
name: Generate 3D Contributions

on:
  schedule:
    - cron: "0 0 * * *"
  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest
    name: generate-github-profile-3d-contrib
    steps:
      - uses: actions/checkout@v3
      - uses: yoshi389111/github-profile-3d-contrib@0.7.1
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          USERNAME: best0127
      - name: Commit & Push
        run: |
          git config user.name github-actions
          git config user.email github-actions@github.com
          git add -A
          git commit -m "generated 3d contributions"
          git push
```

- [ ] **Step 2: Commit workflow**

```bash
git add .github/workflows/profile-3d.yml && git commit -m "feat: add 3d contribution cube action"
```
