# GitHub Profile README Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Create the `README.md` that GitHub renders on `github.com/kestevesPUC` (profile README), per the approved design spec.

**Architecture:** Single static `README.md` in repo root, built from markdown + inline HTML, pulling in free external badge/stat services (no build step, no secrets, no CI).

**Tech Stack:** Markdown, `readme-typing-svg`, `github-readme-stats`, `github-readme-streak-stats`, `shields.io`, `skillicons.dev`.

## Global Constraints

- Repository must be named exactly `kestevesPUC` (same as GitHub username) for the profile page to render this README — verify before pushing.
- Theme: dark (`theme=dark` / `tokyonight`) consistently across all embedded widgets.
- Content language: Portuguese (pt-BR) only.
- GitHub username for all stats/streak URLs: `kestevesPUC`.
- Contact info: email `kaiogomesbh@gmail.com`, LinkedIn `https://www.linkedin.com/in/kaio-esteves/`, GitHub `https://github.com/kestevesPUC`.
- No GitHub Actions / automation in this plan (out of scope per spec).

---

### Task 1: Write README.md content

**Files:**
- Create: `README.md`

**Interfaces:**
- Produces: final `README.md` consumed directly by GitHub's profile-page renderer. No other tasks depend on internal structure beyond the file existing at repo root.

- [ ] **Step 1: Create the banner + typing effect header**

Write the top of `README.md`:

```markdown
<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:1a1a2e,100:16213e&height=200&section=header&text=Kaio%20Gomes&fontSize=50&fontColor=ffffff&animation=fadeIn&fontAlignY=35" width="100%"/>

<a href="https://github.com/kestevesPUC">
  <img src="https://readme-typing-svg.demolab.com/?font=Fira+Code&weight=600&size=24&duration=3000&pause=1000&color=58A6FF&center=true&vCenter=true&width=600&lines=Full+Stack+Developer;Systems+Analyst;React+%7C+.NET+%7C+PHP%2FLaravel;React+Native+%7C+REST+APIs" alt="Typing SVG" />
</a>

</div>
```

- [ ] **Step 2: Add "Sobre mim" section**

Append:

```markdown
## Sobre mim

Desenvolvedor Full Stack e Analista de Sistemas com mais de 4 anos de experiência
no desenvolvimento de aplicações web e mobile, atuando com **React**, **.NET**,
**PHP (Laravel)** e **React Native**. Tenho experiência sólida na construção,
manutenção e evolução de sistemas, com foco em performance, escalabilidade e
eficiência operacional.

Atuo desde o levantamento de requisitos até a entrega da solução, com destaque
para criação de automações e scripts que reduzem trabalho manual e aumentam a
confiabilidade das operações. No dia a dia, uso ferramentas de IA como
**Claude Code** e **Codex** para acelerar desenvolvimento, revisão de código e
automação de tarefas.

- 🔭 Atualmente em: **AETHRA - Automotive Systems**, como Analista de Desenvolvimento de Sistemas
- 🎓 Bacharelado em Sistemas de Informação — PUC Minas (2021–2025)
- 📍 Belo Horizonte, MG, Brasil
- 💬 Stack principal: React · .NET · PHP (Laravel) · React Native · PostgreSQL · APIs REST · Power BI
```

- [ ] **Step 3: Add stack/skills icons section**

Append:

```markdown
## Stack & Ferramentas

**Frontend & Mobile**

![React](https://skillicons.dev/icons?i=react) ![ReactNative Badge](https://img.shields.io/badge/React_Native-20232A?style=for-the-badge&logo=react&logoColor=61DAFB) ![SwiftUI](https://img.shields.io/badge/SwiftUI-000000?style=for-the-badge&logo=swift&logoColor=white) ![JavaScript](https://skillicons.dev/icons?i=js) ![TypeScript](https://skillicons.dev/icons?i=ts)

**Backend**

![.NET](https://skillicons.dev/icons?i=dotnet) ![C#](https://skillicons.dev/icons?i=cs) ![PHP](https://skillicons.dev/icons?i=php) ![Laravel](https://skillicons.dev/icons?i=laravel) ![NodeJS](https://skillicons.dev/icons?i=nodejs)

**Dados**

![PostgreSQL](https://skillicons.dev/icons?i=postgres) ![Power BI](https://img.shields.io/badge/Power_BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)

**Ferramentas & Infra**

![Git](https://skillicons.dev/icons?i=git) ![GitHub](https://skillicons.dev/icons?i=github) ![Docker](https://skillicons.dev/icons?i=docker) ![AWS](https://skillicons.dev/icons?i=aws)

**IA & Produtividade**

![Claude Code](https://img.shields.io/badge/Claude_Code-D97757?style=for-the-badge&logo=anthropic&logoColor=white) ![Codex](https://img.shields.io/badge/Codex-412991?style=for-the-badge&logo=openai&logoColor=white)
```

- [ ] **Step 4: Add GitHub stats section**

Append:

```markdown
## GitHub Stats

<div align="center">

<img height="165" src="https://github-readme-stats.vercel.app/api?username=kestevesPUC&show_icons=true&theme=tokyonight&hide_border=true&count_private=true" alt="GitHub Stats" />
<img height="165" src="https://github-readme-stats.vercel.app/api/top-langs/?username=kestevesPUC&layout=compact&theme=tokyonight&hide_border=true" alt="Top Langs" />

<img src="https://github-readme-streak-stats.herokuapp.com/?user=kestevesPUC&theme=tokyonight&hide_border=true" alt="GitHub Streak" />

</div>
```

- [ ] **Step 5: Add contact footer**

Append:

```markdown
## Contato

<div align="center">

[![Email](https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:kaiogomesbh@gmail.com)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/kaio-esteves/)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/kestevesPUC)

</div>
```

- [ ] **Step 6: Commit**

```bash
git add README.md
git commit -m "feat: add GitHub profile README"
```

---

### Task 2: Verify rendering and links

**Files:**
- Read-only check: `README.md`

**Interfaces:**
- Consumes: `README.md` produced in Task 1.

- [ ] **Step 1: Check every external image URL responds**

Run (PowerShell):

```powershell
$urls = @(
  "https://readme-typing-svg.demolab.com/?font=Fira+Code&weight=600&size=24&duration=3000&pause=1000&color=58A6FF&center=true&vCenter=true&width=600&lines=Full+Stack+Developer",
  "https://github-readme-stats.vercel.app/api?username=kestevesPUC&show_icons=true&theme=tokyonight",
  "https://github-readme-stats.vercel.app/api/top-langs/?username=kestevesPUC&layout=compact&theme=tokyonight",
  "https://github-readme-streak-stats.herokuapp.com/?user=kestevesPUC&theme=tokyonight",
  "https://skillicons.dev/icons?i=react"
)
foreach ($u in $urls) {
  $r = Invoke-WebRequest -Uri $u -Method Head -UseBasicParsing
  "$($r.StatusCode) - $u"
}
```

Expected: every line shows `200 - <url>`. If `github-readme-streak-stats.herokuapp.com` fails (Heroku free tier can be flaky), swap the streak line in `README.md` to `https://streak-stats.demolab.com?user=kestevesPUC&theme=tokyonight` and re-run this check for that one URL.

- [ ] **Step 2: Confirm no leftover placeholder text**

Run:

```powershell
Select-String -Path README.md -Pattern "TBD|TODO|lorem ipsum" -SimpleMatch
```

Expected: no matches (empty output).

- [ ] **Step 3: Commit if the streak URL was swapped**

```bash
git add README.md
git commit -m "fix: use working streak-stats endpoint"
```

(Skip this step if Step 1 required no change.)

---

### Task 3: Prepare repo for GitHub publish

**Files:**
- Read-only check: repo root

**Interfaces:**
- Consumes: committed `README.md` from Tasks 1–2.

- [ ] **Step 1: Confirm repo name matches username requirement**

Explain to the user (no code action): the local folder/repo must be pushed to a **new GitHub repository literally named `kestevesPUC`** (matching the username exactly) and set to **public** — this is what makes GitHub render it as the profile page. This step is a manual action on github.com, not done via git commands here.

- [ ] **Step 2: Confirm remote and push (only after explicit user go-ahead)**

```bash
git remote add origin https://github.com/kestevesPUC/kestevesPUC.git
git branch -M main
git push -u origin main
```

Expected: push succeeds; visiting `https://github.com/kestevesPUC` shows the new README.

- [ ] **Step 3: Commit any final fixups discovered while checking the live render**

```bash
git add README.md
git commit -m "fix: polish profile README after live check"
```

(Only if changes were needed.)
