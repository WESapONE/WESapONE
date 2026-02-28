<!--💬GREETINGSTITLE / 🌐WEBSITE: https://github.com/denvercoder1/readme-typing-svg -->
<p align="center">
<img src="https://readme-typing-svg.herokuapp.com?font=Orbitron&size=40&color=%2379A500&height=67&duration=3000&center=true&lines=%F0%9F%85%B6%F0%9F%86%81%F0%9F%85%B4%F0%9F%85%B4%F0%9F%86%83%F0%9F%85%B8%F0%9F%85%BD%F0%9F%85%B6%F0%9F%86%82">

<!--🖼️SSURFER-->
<p align="center">
<img src="https://media1.tenor.com/m/lVIyA0HR7PEAAAAd/silver-surfer.gif">

<!--📏LINE-->
<img src="https://i.imgur.com/dBaSKWF.gif" height="20" width="100%">

<h1 align="center">Welcome2👋WESapONE!</h1>

###

<div align="center">
  <img src="https://skillicons.dev/icons?i=ts" height="60" alt="typescript logo"  />
  <img width="12" />
  <img src="https://skillicons.dev/icons?i=nextjs" height="60" alt="nextjs logo"  />
  <img width="12" />
  <img src="https://skillicons.dev/icons?i=tailwind" height="60" alt="tailwindcss logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/storybook/storybook-original.svg" height="60" alt="storybook logo"  />
  <img width="12" />
  <img src="https://skillicons.dev/icons?i=graphql" height="60" alt="graphql logo"  />
  <img width="12" />
  <img src="https://skillicons.dev/icons?i=go" height="60" alt="go logo"  />
  <img width="12" />
  <img src="https://skillicons.dev/icons?i=rust" height="60" alt="rust logo"  />
  <img width="12" />
  <img src="https://skillicons.dev/icons?i=nestjs" height="60" alt="nestjs logo"  />
  <img width="12" />
  <img src="https://skillicons.dev/icons?i=py" height="60" alt="python logo"  />
  <img width="12" />
  <img src="https://skillicons.dev/icons?i=aws" height="60" alt="amazonwebservices logo"  />
</div>

###

<div align="center">
  <img src="https://img.shields.io/static/v1?message=LinkedIn&logo=linkedin&label=&color=0077B5&logoColor=white&labelColor=&style=for-the-badge" height="25" alt="linkedin logo"  />
  <img src="https://img.shields.io/static/v1?message=Twitter&logo=twitter&label=&color=1DA1F2&logoColor=white&labelColor=&style=for-the-badge" height="25" alt="twitter logo"  />
  <img src="https://img.shields.io/static/v1?message=Discord&logo=discord&label=&color=7289DA&logoColor=white&labelColor=&style=for-the-badge" height="25" alt="discord logo"  />
  <img src="https://img.shields.io/static/v1?message=Twitch&logo=twitch&label=&color=9146FF&logoColor=white&labelColor=&style=for-the-badge" height="25" alt="twitch logo"  />
  <img src="https://img.shields.io/static/v1?message=dev.to&logo=dev.to&label=&color=0A0A0A&logoColor=white&labelColor=&style=for-the-badge" height="25" alt="devto logo"  />
</div>

###

<div align="center">
  <img src="https://streak-stats.demolab.com?user=WESapONE&locale=en&mode=daily&theme=dracula&hide_border=false&border_radius=5&order=3" height="150" alt="streak graph"  />
  <img src="https://github-profile-trophy.vercel.app?username=WESapONE&theme=dracula&column=-1&row=1&margin-w=8&margin-h=8&no-bg=false&no-frame=false&order=4" height="150" alt="trophy graph"  />
</div>

###

<picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/WESapONE/WESapONE/output/pacman-contribution-graph-dark.svg">
    <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/WESapONE/WESapONE/output/pacman-contribution-graph.svg">
    <img alt="pacman contribution graph" src="https://raw.githubusercontent.com/WESapONE/WESapONE/output/pacman-contribution-graph.svg">
</picture>

###


# 🏠 The WesLab

This repository is the **Single Source of Truth** for the WesLab infrastructure. 
Managed by **[Komodo](https://komodo.software)** using a **GitOps** workflow and 
further documentation using rackpeek and netbox.
## 🚀 Architecture Overview
- **Deployment:** [Komodo](https://komodo.software) (Automatic Webhook Deploys)
- **Runtime:** Docker Engine / Proxmox
- **Ingress:** [Traefik Proxy](https://traefik.io) (Automatic SSL via Cloudflare)
- **Auth:** [Authentik](https://goauthentik.io) (Optional)

## 📁 Repository Structure
- `/infrastructure`: Core services (Networking, Monitoring, Backups)
- `/apps`: User-facing services (Media, Productivity)
- `/provisioning`: System-level automation (Ansible/Terraform)
- `/documentation`: Network maps and hardware specs

## 🌐 Network Map
| Service | URL | Deployment Type | Internal IP |
| :--- | :--- | :--- | :--- |
| **Komodo** | `https://komodo.local` | Docker | `192.168.1.5` |
| **Traefik** | `https://traefik.example.com` | Docker | `192.168.1.5` |
| **Proxmox** | `https://pve.example.com` | Bare Metal | `192.168.1.10` |
| **NAS** | `https://nas.example.com` | Bare Metal | `192.168.1.20` |

## 🛠️ Disaster Recovery
### Initial Setup
1. Clone this repo to the Docker host.
2. Create the external network: `docker network create proxy_network`.
3. Set up the `acme.json` permissions: `chmod 600 infrastructure/networking/data/acme.json`.
4. Define secrets in the [Komodo Dashboard](url-to-your-local-komodo).

### Secrets Management
Secrets are **not stored in Git**. 
Reference the `.env.example` file for required variables such as:
- `CF_API_KEY`
- `DOMAIN_NAME`
- `MYSQL_PASSWORD`

## 📊 Maintenance
To update a stack, simply push a change to the `main` branch:
```bash
git add .
git commit -m "feat: add jellyfin stack"
git push origin main

​```mermaid
graph TD
    %% External Traffic
    Internet((Internet)) -->|Port 80/443| Router[ISP Router / Firewall]
    Router -->|Port Forward| Traefik[Traefik Reverse Proxy]

    subgraph "Docker Host (Komodo Managed)"
        Traefik -->|Internal Proxy| Apps[App Stack]
        Apps --> Jellyfin[Jellyfin]
        Apps --> Vaultwarden[Vaultwarden]
        Apps --> Nextcloud[Nextcloud]
    end

    subgraph "External Nodes"
        Traefik -.->|Dynamic Link| PVE[Proxmox VE]
        Traefik -.->|Dynamic Link| NAS[TrueNAS]
    end

    %% Styles
    style Traefik fill:#f96,stroke:#333,stroke-width:2px
    style Internet fill:#85C1E9
    style Router fill:#D5D8DC
```
```mermaid
sequenceDiagram
    participant Dev as 💻 Local Workstation
    participant Git as 🐙 GitHub/GitLab
    participant Komodo as 🦎 Komodo Core
    participant Host as 🐋 Docker Host

    Dev->>Git: git push (Update docker-compose.yml)
    Note over Git: Webhook Triggered
    Git-->>Komodo: POST /api/webhook/repo-sync
    
    rect rgb(240, 240, 240)
        Note right of Komodo: Automated Phase
        Komodo->>Git: Pull latest changes
        Komodo->>Komodo: Validate Compose Syntax
        Komodo->>Host: docker compose up -d (Update Container)
    end

    Host-->>Dev: Service updated at https://app.example.com
```

<!--💬🃏FUNFACT / 🌐https://github.com/siddharth2016/quote-readme#update-your-readme -->
<p align="center">

<b>FUN FACT EVERYDAY🤔 :</b>
<!--STARTS_HERE_QUOTE_README-->
<i>❝ClueBot NG, an AI-powered bot on English Wikipedia, uses machine learning (neural networks and Bayesian classifiers) to analyze edits in real-time, detecting and reverting 40-55% of vandalism with over 90% accuracy—often exceeding 99% accuracy at high confidence thresholds.❞</i>
<!--ENDS_HERE_QUOTE_README-->

<img src="https://raw.githubusercontent.com/WESapONE/WESapONE/a5f17399d881c5651a89bfe4a621014b08346cf0/images/marquee2.svg">

<!--📏LINE-->
<img src="https://i.imgur.com/dBaSKWF.gif" height="20" width="100%">

<!--📊💬STATTITLE / 🌐WEBSITE: https://textanim.com/ -->
<p align="center">
<img src="https://i.imgur.com/YCw47Dm.gif">



<!--🌯GITHUBTERMINALSTATS💻 / 🌐WEBSITE: https://github.com/yogeshwaran01/github-stats-terminal-style -->
<p align="center">
<img src="https://raw.githubusercontent.com/WESapONE/github-stats-terminal-style/master/github_stats.svg">

<!--📊STATSGRAPH / 🌐WEBSITE: https://github.com/anuraghazra/github-readme-stats -->
<p align="center">
<img src="https://github-readme-stats-WESapONE-projects.vercel.app/api?username=WESapONE&show_icons=true&theme=merko&border_color=599200">

<!--📊STREAKSTATSGRAPH / 🌐WEBSITE: https://github.com/denvercoder1/github-readme-streak-stats -->
<img src="https://github-readme-streak-stats-WESapONE-projects.vercel.app/?user=WESapONE&theme=merko&border=599200">

<!--📙LANGUAGES / 🌐WEBSITE: https://github.com/anuraghazra/github-readme-stats -->
<p align="center">
<a href="https://github.com/WESapONE/AdGuard-WireGuard-Unbound-DNScrypt"><img src="https://github-readme-stats-WESapONE-projects.vercel.app/api/top-langs?username=WESapONE&theme=merko&layout=compact&border_color=599200&langs_count=6">


<!--👀VIEWS / 🌐WEBSITE: https://github.com/antonkomarev/github-profile-views-counter -->
<p align="center">
<img src="https://komarev.com/ghpvc/?username=WESapONE&color=0E9C47&style=for-the-badge">

<!--📈ACTIVITYGRAPH / 🌐WEBSITE: https://github.com/Ashutosh00710/github-readme-activity-graph -->
<img src="https://github-readme-activity-graph-WESapONEs-projects.vercel.app/graph?username=WESapONE&theme=react-dark&hide_border=true&color=00d668&line=00d668&point=8b007e" width="100%">

<!--🐍💬SNAKETITLE / 🌐WEBSITE: https://textanim.com/ -->
<p align="center">
<img src="https://i.imgur.com/x1KbuCq.gif" width="500">

<!--🐍📈SNAKEGRAPH / 🌐WEBSITE: https://github.com/Platane/snk & https://github.com/ironmaniiith/Github-profile-name-writer -->
<img src="https://raw.githubusercontent.com/WESapONE/WESapONE/snake/github-snake-dark.svg" width="100%">

###

<img src="https://raw.githubusercontent.com/WESapONE/WESapONE/output/snake.svg" alt="Snake animation" />

###

<!--📉METRICS / 🌐WEBSITE: https://github.com/lowlighter/metrics -->
<h4 align="right">
<details><summary><b>𝓟&nbsp;𝓡&nbsp;𝓞&nbsp;𝓕&nbsp;𝓘&nbsp;𝓛&nbsp;𝓔&nbsp;&nbsp; 𝓜&nbsp;𝓔&nbsp;𝓣&nbsp;𝓡&nbsp;𝓘&nbsp;𝓒&nbsp;𝓢<img src="https://media.giphy.com/media/mBYkXvLxkHZFmqBHIC/giphy.gif" width=50px height=40px></b></summary>
<p>
<p align="center">
<img src="https://raw.githubusercontent.com/WESapONE/WESapONE/main/github-metrics.svg">
</p>
</details>

<!--📏LINE-->
<img src="https://i.imgur.com/dBaSKWF.gif" height="20" width="100%">

<!--😂💬JOKETITLE / 🌐WEBSITE: https://textanim.com/ -->
<p align="center">
<img src="https://i.imgur.com/KwHw09D.gif" height="30" width="150">

<!--🤣JOYEMOJI / 🌐WEBSITE: https://github.com/seanprashad/slackmoji/ -->
<p align="center">
<img src="https://github.com/seanprashad/slackmoji/blob/master/emoji/blob/blob-joy-gif.gif" width="30"><img src="https://github.com/seanprashad/slackmoji/blob/master/emoji/blob/blob-joy-gif.gif" width="30"><img src="https://github.com/seanprashad/slackmoji/blob/master/emoji/blob/blob-joy-gif.gif" width="30"><img src="https://github.com/seanprashad/slackmoji/blob/master/emoji/blob/blob-joy-gif.gif" width="30"><img src="https://github.com/seanprashad/slackmoji/blob/master/emoji/blob/blob-joy-gif.gif" width="30"><img src="https://github.com/seanprashad/slackmoji/blob/master/emoji/blob/blob-joy-gif.gif" width="30"><img src="https://github.com/seanprashad/slackmoji/blob/master/emoji/blob/blob-joy-gif.gif" width="30"><img src="https://github.com/seanprashad/slackmoji/blob/master/emoji/blob/blob-joy-gif.gif" width="30"><img src="https://github.com/seanprashad/slackmoji/blob/master/emoji/blob/blob-joy-gif.gif" width="30">

<!--😂🃏JOKECARD / 🌐WEBSITE: https://github.com/ABSphreak/readme-jokes -->
<p align="center">
<img src="https://readme-jokes-trinibs-projects.vercel.app/api" alt="Jokes Card" width="400">

<!--💬QUOTESTITLE / 🌐WEBSITE: https://textanim.com/ -->
<p align="center">
<img src="https://i.imgur.com/OFloXS3.gif" height="30" width="150">

<!--🍷WINEEMOJI / 🌐WEBSITE: https://github.com/seanprashad/slackmoji/ -->
<p align="center">
<img src="https://github.com/seanprashad/slackmoji/blob/master/emoji/blob/blob-wine-gif.gif" width="30"><img src="https://github.com/seanprashad/slackmoji/blob/master/emoji/blob/blob-wine-gif.gif" width="30"><img src="https://github.com/seanprashad/slackmoji/blob/master/emoji/blob/blob-wine-gif.gif" width="30"><img src="https://github.com/seanprashad/slackmoji/blob/master/emoji/blob/blob-wine-gif.gif" width="30"><img src="https://github.com/seanprashad/slackmoji/blob/master/emoji/blob/blob-wine-gif.gif" width="30"><img src="https://github.com/seanprashad/slackmoji/blob/master/emoji/blob/blob-wine-gif.gif" width="30"><img src="https://github.com/seanprashad/slackmoji/blob/master/emoji/blob/blob-wine-gif.gif" width="30"><img src="https://github.com/seanprashad/slackmoji/blob/master/emoji/blob/blob-wine-gif.gif" width="30"><img src="https://github.com/seanprashad/slackmoji/blob/master/emoji/blob/blob-wine-gif.gif" width="30">

<!--💬🃏QUOTESCARD / 🌐WEBSITE: https://github.com/PiyushSuthar/github-readme-quotes#Demo & https://github.com/cheehwatang/github-readme-daily-quotes & https://github.com/shravan20/github-readme-quotes -->
<p align="center">
<img src="https://piyu-github-readme-quotes-trinibs-projects.vercel.app/api?theme=merko&border=true">
<p align="center">
<img src="https://github-readme-quotes-trinibs-projects.vercel.app/quote?theme=merko&layout=churchill&animation=grow_out_in&font=Architect">
<p align="center">
<img src="https://github-readme-daily-quotes-trinibs-projects.vercel.app/api?theme=merko&category=programming&border=true&border_color=bdf259&border_width=3&border_radius=40&font=new_rocker"><br><br>

<!--💬🃏MEMESTITLE / 🌐WEBSITE: https://textanim.com/ -->
<p align="center">
<img src="https://i.imgur.com/vKOQi1L.gif" height="30" width="150">

<!--😻CATEMOJI / 🌐WEBSITE: https://github.com/seanprashad/slackmoji/ -->
<p align="center">
<img src="https://github.com/seanprashad/slackmoji/blob/master/emoji/llamas/llama-blood-tears-gif.gif" width="30"><img src="https://github.com/seanprashad/slackmoji/blob/master/emoji/llamas/llama-blood-tears-gif.gif" width="30"><img src="https://github.com/seanprashad/slackmoji/blob/master/emoji/llamas/llama-blood-tears-gif.gif" width="30"><img src="https://github.com/seanprashad/slackmoji/blob/master/emoji/llamas/llama-blood-tears-gif.gif" width="30"><img src="https://github.com/seanprashad/slackmoji/blob/master/emoji/llamas/llama-blood-tears-gif.gif" width="30"><img src="https://github.com/seanprashad/slackmoji/blob/master/emoji/llamas/llama-blood-tears-gif.gif" width="30"><img src="https://github.com/seanprashad/slackmoji/blob/master/emoji/llamas/llama-blood-tears-gif.gif" width="30"><img src="https://github.com/seanprashad/slackmoji/blob/master/emoji/llamas/llama-blood-tears-gif.gif" width="30"><img src="https://github.com/seanprashad/slackmoji/blob/master/emoji/llamas/llama-blood-tears-gif.gif" width="30">

<!--🃏MEMEPHOTOS / 🌐WEBSITE: https://github.com/trinib/Subreddit-Memes -->
<p align="center">
<img src="https://subreddit-memes-trinibs-projects.vercel.app/api/meme" width="400px"/>

<!--📏LINE-->
<img src="https://i.imgur.com/dBaSKWF.gif" height="20" width="100%">

<!--💬FUNTITLE / 🌐WEBSITE: https://textanim.com/ -->
<p align="center">
<img src="https://i.imgur.com/jdd2GPv.gif" height="37" width="250">

<!--♟️CHESS / 🌐WEBSITE: https://github.com/marcizhu/readme-chess --> 
 <h4 align="center">
<table>
  <tr>
  </tr>
  <tr>
    <td><h5 align="center"><details>
  <summary><h2><img src="https://media.giphy.com/media/9qCnMFHeiUVdVaTihl/giphy.gif" width="35px" height="35px">&nbsp;Chess Tournament&nbsp;<img src="https://media.giphy.com/media/9qCnMFHeiUVdVaTihl/giphy.gif" width="40px" height="40px"></h2></summary><p>

<h4 align="left">

ANYONE can take a turn on the board  
<i>Make your move !!. It's <!-- BEGIN TURN -->black(solid)<!-- END TURN --> to play(instructions beneath)</i>

<!-- BEGIN CHESS BOARD -->
|   | A | B | C | D | E | F | G | H |   |
|---|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| **8** | <img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/black/king.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | **8** |
| **7** | <img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/black/knight.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/black/pawn.png" width=50px> | **7** |
| **6** | <img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/black/pawn.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/black/pawn.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/white/bishop.png" width=50px> | **6** |
| **5** | <img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/white/queen.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | **5** |
| **4** | <img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/black/pawn.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/black/rook.png" width=50px> | <img src="img/blank.png" width=50px> | **4** |
| **3** | <img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/white/pawn.png" width=50px> | **3** |
| **2** | <img src="img/white/pawn.png" width=50px> | <img src="img/white/pawn.png" width=50px> | <img src="img/white/pawn.png" width=50px> | <img src="img/white/king.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/white/pawn.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | **2** |
| **1** | <img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/white/rook.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/white/rook.png" width=50px> | **1** |
|   | **A** | **B** | **C** | **D** | **E** | **F** | **G** | **H** |   |
<!-- END CHESS BOARD -->

To move a piece to a postion
 
**_Choose one from the following table_** :
<!-- BEGIN MOVES LIST -->
|  FROM  | TO (Just click a link!) |
| :----: | :---------------------- |
| **E4** | [E3](https://github.com/WESapONEWESapONE/issues/new?body=Please+do+not+change+the+title.+Just+click+%22Submit+new+issue%22.+You+don%27t+need+to+do+anything+else+%3AD&title=Chess%3A+Move+E4+to+E3) |
| **E7** | [C8](https://github.com/WESapONEWESapONE/issues/new?body=Please+do+not+change+the+title.+Just+click+%22Submit+new+issue%22.+You+don%27t+need+to+do+anything+else+%3AD&title=Chess%3A+Move+E7+to+C8), [D5](https://github.com/WESapONEWESapONE/issues/new?body=Please+do+not+change+the+title.+Just+click+%22Submit+new+issue%22.+You+don%27t+need+to+do+anything+else+%3AD&title=Chess%3A+Move+E7+to+D5), [F5](https://github.com/WESapONEWESapONE/issues/new?body=Please+do+not+change+the+title.+Just+click+%22Submit+new+issue%22.+You+don%27t+need+to+do+anything+else+%3AD&title=Chess%3A+Move+E7+to+F5), [G6](https://github.com/WESapONEWESapONE/issues/new?body=Please+do+not+change+the+title.+Just+click+%22Submit+new+issue%22.+You+don%27t+need+to+do+anything+else+%3AD&title=Chess%3A+Move+E7+to+G6), [G8](https://github.com/WESapONEWESapONE/issues/new?body=Please+do+not+change+the+title.+Just+click+%22Submit+new+issue%22.+You+don%27t+need+to+do+anything+else+%3AD&title=Chess%3A+Move+E7+to+G8) |
| **E8** | [D7](https://github.com/WESapONEWESapONE/issues/new?body=Please+do+not+change+the+title.+Just+click+%22Submit+new+issue%22.+You+don%27t+need+to+do+anything+else+%3AD&title=Chess%3A+Move+E8+to+D7), [D8](https://github.com/WESapONEWESapONE/issues/new?body=Please+do+not+change+the+title.+Just+click+%22Submit+new+issue%22.+You+don%27t+need+to+do+anything+else+%3AD&title=Chess%3A+Move+E8+to+D8), [F7](https://github.com/WESapONEWESapONE/issues/new?body=Please+do+not+change+the+title.+Just+click+%22Submit+new+issue%22.+You+don%27t+need+to+do+anything+else+%3AD&title=Chess%3A+Move+E8+to+F7) |
| **F6** | [F5](https://github.com/WESapONEWESapONE/issues/new?body=Please+do+not+change+the+title.+Just+click+%22Submit+new+issue%22.+You+don%27t+need+to+do+anything+else+%3AD&title=Chess%3A+Move+F6+to+F5) |
| **G4** | [F4](https://github.com/WESapONEWESapONE/issues/new?body=Please+do+not+change+the+title.+Just+click+%22Submit+new+issue%22.+You+don%27t+need+to+do+anything+else+%3AD&title=Chess%3A+Move+G4+to+F4), [G1](https://github.com/WESapONEWESapONE/issues/new?body=Please+do+not+change+the+title.+Just+click+%22Submit+new+issue%22.+You+don%27t+need+to+do+anything+else+%3AD&title=Chess%3A+Move+G4+to+G1), [G2](https://github.com/WESapONEWESapONE/issues/new?body=Please+do+not+change+the+title.+Just+click+%22Submit+new+issue%22.+You+don%27t+need+to+do+anything+else+%3AD&title=Chess%3A+Move+G4+to+G2), [G3](https://github.com/WESapONEWESapONE/issues/new?body=Please+do+not+change+the+title.+Just+click+%22Submit+new+issue%22.+You+don%27t+need+to+do+anything+else+%3AD&title=Chess%3A+Move+G4+to+G3), [G5](https://github.com/WESapONEWESapONE/issues/new?body=Please+do+not+change+the+title.+Just+click+%22Submit+new+issue%22.+You+don%27t+need+to+do+anything+else+%3AD&title=Chess%3A+Move+G4+to+G5), [G6](https://github.com/WESapONEWESapONE/issues/new?body=Please+do+not+change+the+title.+Just+click+%22Submit+new+issue%22.+You+don%27t+need+to+do+anything+else+%3AD&title=Chess%3A+Move+G4+to+G6), [G7](https://github.com/WESapONEWESapONE/issues/new?body=Please+do+not+change+the+title.+Just+click+%22Submit+new+issue%22.+You+don%27t+need+to+do+anything+else+%3AD&title=Chess%3A+Move+G4+to+G7), [G8](https://github.com/WESapONEWESapONE/issues/new?body=Please+do+not+change+the+title.+Just+click+%22Submit+new+issue%22.+You+don%27t+need+to+do+anything+else+%3AD&title=Chess%3A+Move+G4+to+G8), [H4](https://github.com/WESapONEWESapONE/issues/new?body=Please+do+not+change+the+title.+Just+click+%22Submit+new+issue%22.+You+don%27t+need+to+do+anything+else+%3AD&title=Chess%3A+Move+G4+to+H4) |
<!-- END MOVES LIST -->

Having fun? Ask a friend to play next move to get the next turn !

<details>
  <summary>How it works</summary>
When you click on a link it will submit a new issue with the desired move, create the issue and a GitHub action is triggered, which in turn runs a small python script that performs the specified movement, updates this README file and commits the changes.
</details>


<details>
  <summary>Last 5 moves in this game</summary>
<!-- BEGIN LAST MOVES -->

| Move | Author |
| :--: | :----- |
| `H2` to `H3` | [ @StackOverflowIsBetterThanAnyAI](https://github.com/StackOverflowIsBetterThanAnyAI) |
| `G8` to `G4` | [ @Odinwattez](https://github.com/Odinwattez) |
| `D1` to `E1` | [ @StackOverflowIsBetterThanAnyAI](https://github.com/StackOverflowIsBetterThanAnyAI) |
| `H8` to `G8` | [ @benFrnklnDuck](https://github.com/benFrnklnDuck) |
| `E3` to `H6` | [ @StackOverflowIsBetterThanAnyAI](https://github.com/StackOverflowIsBetterThanAnyAI) |

<!-- END LAST MOVES -->
</details>

<details>
  <summary>Top 10 most moves across all games</summary>
<!-- BEGIN TOP MOVES -->

| Total moves |  User  |
| :---------: | :----- |
| 26 | [@WESapONE](https://github.com/WESapONE) |
| 14 | [@JayantGoel001](https://github.com/JayantGoel001) |
| 8 | [@viktoriussuwandi](https://github.com/viktoriussuwandi) |
| 6 | [@StackOverflowIsBetterThanAnyAI](https://github.com/StackOverflowIsBetterThanAnyAI) |
| 5 | [@lulunac27a](https://github.com/lulunac27a) |
| 3 | [@Sabyasachi-Seal](https://github.com/Sabyasachi-Seal) |
| 3 | [@harshendram](https://github.com/harshendram) |
| 2 | [@Basvdlouw](https://github.com/Basvdlouw) |
| 2 | [@TomfromBerlin](https://github.com/TomfromBerlin) |
| 2 | [@SagXD](https://github.com/SagXD) |

<!-- END TOP MOVES -->

</details>
</details><h5 align="center">
  </tr>
 </table>
      
<!--CONNECTDOT🔴🟡 / 🌐WEBSITE: https://github.com/bloedboemmel/bloedboemmel --> 
 <h4 align="center">
<table>
  <tr>
  </tr>
  <tr>
    <td><h5 align="center"><details>
  <summary><h2>&nbsp;&nbsp;<img src="https://media.giphy.com/media/L3LNfB3IXIUmySN67Z/giphy.gif" width="40px" height="40px">&nbsp;Connect 4 Dots&nbsp;<img src="https://media.giphy.com/media/Y0slbp1Hr4C8lUA5UG/giphy.gif" width="40px" height="40px">&nbsp;&nbsp;</h2></summary><p>

<h4 align="left">

Here you can play Connect4. Just click a number under the grid to move. It's <!-- BEGIN TURN2 -->red<!-- END TURN2 --> turn.

<!-- BEGIN CONNECT4 BOARD -->
|   | 1 | 2 | 3 | 4 | 5 | 6 | 7 |   |
|---|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
|---|<img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | |---|
|---|<img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | |---|
|---|<img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | |---|
|---|<img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | |---|
|---|<img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/yellow.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/blank.png" width=50px> | |---|
|---|<img src="img/red.png" width=50px> | <img src="img/red.png" width=50px> | <img src="img/blank.png" width=50px> | <img src="img/yellow.png" width=50px> | <img src="img/red.png" width=50px> | <img src="img/yellow.png" width=50px> | <img src="img/yellow.png" width=50px> | |---|
|   | [1](https://github.com/WESapONE/WESapONE/issues/new?body=Please+do+not+change+the+title.+Just+click+%22Submit+new+issue%22.+You+don%27t+need+to+do+anything+else+%3AD&title=Connect4%3A+Put+1) | [2](https://github.com/WESapONE/WESapONE/issues/new?body=Please+do+not+change+the+title.+Just+click+%22Submit+new+issue%22.+You+don%27t+need+to+do+anything+else+%3AD&title=Connect4%3A+Put+2) | [3](https://github.com/WESapONE/WESapONE/issues/new?body=Please+do+not+change+the+title.+Just+click+%22Submit+new+issue%22.+You+don%27t+need+to+do+anything+else+%3AD&title=Connect4%3A+Put+3) | [4](https://github.com/WESapONE/WESapONE/issues/new?body=Please+do+not+change+the+title.+Just+click+%22Submit+new+issue%22.+You+don%27t+need+to+do+anything+else+%3AD&title=Connect4%3A+Put+4) | [5](https://github.com/WESapONE/WESapONE/issues/new?body=Please+do+not+change+the+title.+Just+click+%22Submit+new+issue%22.+You+don%27t+need+to+do+anything+else+%3AD&title=Connect4%3A+Put+5) | [6](https://github.com/WESapONE/WESapONE/issues/new?body=Please+do+not+change+the+title.+Just+click+%22Submit+new+issue%22.+You+don%27t+need+to+do+anything+else+%3AD&title=Connect4%3A+Put+6) | [7](https://github.com/WESapONE/WESapONE/issues/new?body=Please+do+not+change+the+title.+Just+click+%22Submit+new+issue%22.+You+don%27t+need+to+do+anything+else+%3AD&title=Connect4%3A+Put+7) |   |
<!-- END CONNECT4 BOARD -->
<!-- BEGIN MOVES LIST2 -->
<!-- END MOVES LIST2 -->

<details>
  <summary>Last 5 moves in this game</summary>
<!-- BEGIN LAST MOVES2 -->

| Move | Author |
| :--: | :----- |
| `4` |  [ @harshendram](https://github.com/harshendram) | |
| `2` |  [ @StackOverflowIsBetterThanAnyAI](https://github.com/StackOverflowIsBetterThanAnyAI) | |
| `5` |  [ @StackOverflowIsBetterThanAnyAI](https://github.com/StackOverflowIsBetterThanAnyAI) | |
| `5` |  [ @StackOverflowIsBetterThanAnyAI](https://github.com/StackOverflowIsBetterThanAnyAI) | |
| `6` |  [ @StackOverflowIsBetterThanAnyAI](https://github.com/StackOverflowIsBetterThanAnyAI) | |

<!-- END LAST MOVES2 -->
</details>

<details>
  <summary>Top 10 most moves across all games</summary>
<!-- BEGIN TOP MOVES2 -->

| Total moves |  User  |
| :---------: | :----- |
| 35 |  [@StackOverflowIsBetterThanAnyAI](https://github.com/StackOverflowIsBetterThanAnyAI) | |
| 12 |  [@WESapONE](https://github.com/WESapONE) | |
| 9 |  [@viktoriussuwandi](https://github.com/viktoriussuwandi) | |
| 6 |  [@lulunac27a](https://github.com/lulunac27a) | |
| 5 |  [@oxoovo](https://github.com/oxoovo) | |
| 4 |  [@benzlokzik](https://github.com/benzlokzik) | |
| 3 |  [@jhoitenga](https://github.com/jhoitenga) | |
| 2 |  [@JayantGoel001](https://github.com/JayantGoel001) | |
| 2 |  [@mauro-balades](https://github.com/mauro-balades) | |
| 2 |  [@Cophhy](https://github.com/Cophhy) | |

<!-- END TOP MOVES2 -->
</details>
</details>
</details><h5 align="center">
  </tr>
 </table>
      
#
<!--✏️WORDBOARD / 🌐WEBSITE: https://github.com/JessicaLim8/JessicaLim8 --> 
<h2 align="center">
Join the Word Cloud Board :cloud: :pencil2:

### :thought_balloon: <a href="https://github.com/WESapONE/word-cloud/issues/new?template=addword.md&title=wordcloud%7Cadd%7C%3CINSERT-WORD%3E"><b>Add your name</b></a> to see the word cloud update in real time :rocket:

:star2: Don't like the arrangement? <a href="https://github.com/WESapONE/word-cloud/issues/new?template=shufflecloud.md&title=wordcloud%7Cshuffle"><b>Regenerate it</b></a> :game_die:

<h3 align="center">
📛Github Usernames📛 
</br> 
<img src="https://raw.githubusercontent.com/WESapONE/word-cloud/main/wordcloud/wordcloud.png" alt="WordCloud" width="100%">

<!--📏LINE-->
<img src="https://i.imgur.com/dBaSKWF.gif" height="20" width="100%">
<p align="center">

<!--🐱CAT-->
<p align="center">
<img src="https://media.giphy.com/media/WUlplcMpOCEmTGBtBW/giphy.gif" width="100">

<!--🤔INTERESTTITLE-->
<p align="center">
<img src="https://i.imgur.com/ozEwbHs.gif">

<!--🖼️🖼️INTERSTLOGOS-->
<p align="center">
<img src="https://www.vectorlogo.zone/logos/flutterio/flutterio-icon.svg" width="60">
<img src="https://www.vectorlogo.zone/logos/python/python-icon.svg" width="60">
<img src="https://www.vectorlogo.zone/logos/firebase/firebase-icon.svg" width="60">
<img src="https://www.vectorlogo.zone/logos/dartlang/dartlang-icon.svg" width="60">
<img src="https://www.vectorlogo.zone/logos/adobe_illustrator/adobe_illustrator-icon.svg" width="60">
<img src="https://raw.githubusercontent.com/github/explore/80688e429a7d4ef2fca1e82350fe8e3517d3494d/topics/visual-studio-code/visual-studio-code.png" width="60">
<img src="https://www.vectorlogo.zone/logos/linux/linux-icon.svg" width="60">
<img src="https://www.vectorlogo.zone/logos/android/android-icon.svg" width="60">
<img src="https://www.vectorlogo.zone/logos/microsoft/microsoft-icon.svg" width="60">
<img src="https://www.vectorlogo.zone/logos/github/github-icon.svg" width="60">
</h4>

<!--🖼️⭐🔱STARRED/FORK-->
<h4 align="right">
 
<table>
  <tr>
   <img src="https://c.tenor.com/SOVMSXmWB1kAAAAi/tony-star-jumping.gif" width="70">
   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
   <img src="https://c.tenor.com/XSbD902n1fwAAAAi/rennen-fast.gif" width="50">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
  </tr>
  <tr>
    <td><p align="center"><a href="https://github.com/WESapONE?tab=stars"><b>MY STARRED REPOS <br>AND TOPICS</b></a>
    <td><p align="center"><a href="https://github.com/WESapONE/WESapONE/edit/main/README.md"><b>FORK PROFILE WITH <br>EASY EDITING</b></a>
  </tr>
 </table>
 
<!--📏LINE-->
<p align="center">
<img src="https://i.imgur.com/dBaSKWF.gif" height="20" width="100%">

<!--🎨THEMEMODE / 🌐WEBSITE: https://fancytext.blogspot.com/ -->
<h4 align="left">
</h4>
 
╔═&nbsp;&nbsp;👀 𝕐&nbsp;𝕆&nbsp;𝕌&nbsp;ℝ&nbsp;&nbsp;𝕋&nbsp;ℍ&nbsp;𝔼&nbsp;𝕄&nbsp;𝔼&nbsp;&nbsp;𝕄&nbsp;𝕆&nbsp;𝔻&nbsp;𝔼 👀
<h4>
<h4 align="left">  
 
╚═════ &nbsp;𝐈𝐓'𝐒 [𝐃𝐀𝐑𝐊⚫](https://github.com/settings/appearance#gh-dark-mode-only)[𝐁𝐑𝐈𝐆𝐇𝐓⚪](https://github.com/settings/appearance#gh-light-mode-only) 𝐈𝐍 𝐇𝐄𝐑𝐄...
<h4>

<!--🪳ROACH&🕷️SPIDER--> 
<p align="left">
<img src="https://media.giphy.com/media/2fC8cduAc35UIAxHDE/giphy.gif" width="150">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<img src="https://c.tenor.com/3dgbcMt6Kx4AAAAi/spider-insect.gif" width="40">
 
<!--🦶FOOTER--> 
<img src="https://raw.githubusercontent.com/WESapONE/WESapONE/82213791fa9ff58d3ca768ddd6de2489ec23ffca/images/footer.svg" width="100%">

<!--⚽️ACTIVITY / 🌐WEBSITE: https://github.com/Readme-Workflows/recent-activity -->
<!--RECENT_ACTIVITY:start-->
<!--RECENT_ACTIVITY:end-->
<p align="right">
<!--RECENT_ACTIVITY:last_update-->
<i>Last refresh</i> : <b>Thursday, October 9th, 2025, 11:26:28 AM</b>
<!--RECENT_ACTIVITY:last_update_end-->


<a href="https://github.com/WESapONE/WESapONE/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=WESapONE/WESapONE&anon=true" />
</a>

<!-- 

<!--🖼️ILOVEOPENSOURCE-->
<img src="https://i.imgur.com/AZa5yxa.png" height="120" width="600">

𝐈𝐅 𝐘𝐎𝐔 𝐑𝐄𝐀𝐂𝐇𝐄𝐃 𝐇𝐄𝐑𝐄 (C O N G R A T S 🎉🎈🎊) 

𝐂𝐇𝐄𝐂𝐊 𝐎𝐔𝐓 𝐓𝐇𝐄𝐒𝐄:


██████╗ ███████╗ █████╗ ██╗   ██╗████████╗██╗███████╗██╗   ██╗     ██████╗ ██╗████████╗██╗  ██╗██╗   ██╗██████╗ 
██╔══██╗██╔════╝██╔══██╗██║   ██║╚══██╔══╝██║██╔════╝╚██╗ ██╔╝    ██╔════╝ ██║╚══██╔══╝██║  ██║██║   ██║██╔══██╗
██████╔╝█████╗  ███████║██║   ██║   ██║   ██║█████╗   ╚████╔╝     ██║  ███╗██║   ██║   ███████║██║   ██║██████╔╝
██╔══██╗██╔══╝  ██╔══██║██║   ██║   ██║   ██║██╔══╝    ╚██╔╝      ██║   ██║██║   ██║   ██╔══██║██║   ██║██╔══██╗
██████╔╝███████╗██║  ██║╚██████╔╝   ██║   ██║██║        ██║       ╚██████╔╝██║   ██║   ██║  ██║╚██████╔╝██████╔╝
╚═════╝ ╚══════╝╚═╝  ╚═╝ ╚═════╝    ╚═╝   ╚═╝╚═╝        ╚═╝        ╚═════╝ ╚═╝   ╚═╝   ╚═╝  ╚═╝ ╚═════╝ ╚═════╝                                         
https://github.com/rzashakeri/beautify-github-profile


 ██████╗ ██╗████████╗██╗  ██╗██╗   ██╗██████╗     ███████╗███████╗ █████╗ ██████╗  ██████╗██╗  ██╗
██╔════╝ ██║╚══██╔══╝██║  ██║██║   ██║██╔══██╗    ██╔════╝██╔════╝██╔══██╗██╔══██╗██╔════╝██║  ██║
██║  ███╗██║   ██║   ███████║██║   ██║██████╔╝    ███████╗█████╗  ███████║██████╔╝██║     ███████║
██║   ██║██║   ██║   ██╔══██║██║   ██║██╔══██╗    ╚════██║██╔══╝  ██╔══██║██╔══██╗██║     ██╔══██║
╚██████╔╝██║   ██║   ██║  ██║╚██████╔╝██████╔╝    ███████║███████╗██║  ██║██║  ██║╚██████╗██║  ██║
 ╚═════╝ ╚═╝   ╚═╝   ╚═╝  ╚═╝ ╚═════╝ ╚═════╝     ╚══════╝╚══════╝╚═╝  ╚═╝╚═╝  ╚═╝ ╚═════╝╚═╝  ╚═╝
https://github.com/gennaro-tedesco/gh-s


███████╗██╗   ██╗███╗   ██╗ ██████╗    ███████╗ ██████╗ ██████╗ ██╗  ██╗███████╗
██╔════╝╚██╗ ██╔╝████╗  ██║██╔════╝    ██╔════╝██╔═══██╗██╔══██╗██║ ██╔╝██╔════╝
███████╗ ╚████╔╝ ██╔██╗ ██║██║         █████╗  ██║   ██║██████╔╝█████╔╝ ███████╗
╚════██║  ╚██╔╝  ██║╚██╗██║██║         ██╔══╝  ██║   ██║██╔══██╗██╔═██╗ ╚════██║
███████║   ██║   ██║ ╚████║╚██████╗    ██║     ╚██████╔╝██║  ██║██║  ██╗███████║
╚══════╝   ╚═╝   ╚═╝  ╚═══╝ ╚═════╝    ╚═╝      ╚═════╝ ╚═╝  ╚═╝╚═╝  ╚═╝╚══════╝
https://github.com/wei/pull

██████╗ ███████╗███████╗██╗███╗   ██╗███████╗██████╗        ██████╗ ██╗████████╗██╗  ██╗██╗   ██╗██████╗ 
██╔══██╗██╔════╝██╔════╝██║████╗  ██║██╔════╝██╔══██╗      ██╔════╝ ██║╚══██╔══╝██║  ██║██║   ██║██╔══██╗
██████╔╝█████╗  █████╗  ██║██╔██╗ ██║█████╗  ██║  ██║█████╗██║  ███╗██║   ██║   ███████║██║   ██║██████╔╝
██╔══██╗██╔══╝  ██╔══╝  ██║██║╚██╗██║██╔══╝  ██║  ██║╚════╝██║   ██║██║   ██║   ██╔══██║██║   ██║██╔══██╗
██║  ██║███████╗██║     ██║██║ ╚████║███████╗██████╔╝      ╚██████╔╝██║   ██║   ██║  ██║╚██████╔╝██████╔╝
╚═╝  ╚═╝╚══════╝╚═╝     ╚═╝╚═╝  ╚═══╝╚══════╝╚═════╝        ╚═════╝ ╚═╝   ╚═╝   ╚═╝  ╚═╝ ╚═════╝ ╚═════╝ 
https://github.com/refined-github/refined-github

-->                                                                                                        

<!--
**WESapONE/WESapONE** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->
