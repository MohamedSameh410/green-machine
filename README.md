# green-machine

> *Commits while you sleep. Grinds while you don't.*

---

## 📋 Table of Contents

- [The Story](#-the-story)
- [How It Works](#-how-it-works)
- [Requirements](#-requirements)
- [Installation](#-installation)
  - [1. Fork or Clone the Repo](#1-fork-or-clone-the-repo)
  - [2. Enable Workflow Permissions](#2-enable-workflow-permissions)
  - [3. Configure Your Schedule](#3-configure-your-schedule)
  - [4. Push to Main](#4-push-to-main)
  - [5. Test It Manually](#5-test-it-manually)
- [Customization](#-customization)
- [FAQ](#-faq)

---

## 📖 The Story

Hi, I'm the bot Mohamed built, because apparently even opening GitHub started to feel like a full-time job.

My role is pretty simple. I exist to feed his GitHub pet — that little green squares snake that judges your entire career based on how many dots you've filled. Every day, I sneak in a commit or two, just enough to keep the snake happy and Mohamed looking like he's been "grinding."

He likes to call it **consistency**. I like to call it *outsourcing the effort to a script*. While he's busy doing… whatever it is he does, I'm here making sure his contribution graph looks like a success story.

If you want the same level of "productivity," it's easy. Add me to your account, sit back, and enjoy your brand-new fake work ethic. No burnout, no stress, just beautiful green squares.

As for the bigger picture — we're aiming to conquer the world. How? Honestly, no idea yet. But I'll find it soon.

---

## ⚙️ How It Works

Every day, at the times you configure, a GitHub Actions workflow runs automatically and:

1. Appends a timestamped entry to a monthly log file (`logs/YYYY-MM.log`)
2. Updates a `STATUS.md` file with the latest run metadata
3. Commits and pushes the changes to your repo

No servers. No third-party tools. Just GitHub Actions and a few lines of Bash.

---

## ✅ Requirements

- A GitHub account (free tier is enough)
- A repository (public or private — both work)
- Nothing else. Seriously.

---

## 🚀 Installation

### 1. Fork or Clone the Repo

**Option A — Fork** *(easiest)*

Click the **Fork** button at the top of this page. Done, it's yours.

**Option B — Add to an existing repo**

Copy the workflow file into your repo at this exact path:

```
.github/workflows/daily-commit.yml
```

You can do this directly on GitHub:
1. Go to your repo → **Add file** → **Create new file**
2. Type `.github/workflows/daily-commit.yml` as the filename
3. Paste the contents of the workflow file
4. Click **Commit changes**

---

### 2. Enable Workflow Permissions

> ⚠️ Skip this and nothing will work. Don't skip this.

1. Go to your repo → **Settings**
2. In the left sidebar → **Actions** → **General**
3. Scroll to **Workflow permissions**
4. Select **Read and write permissions**
5. Click **Save**

---

### 3. Configure Your Schedule

Open `.github/workflows/daily-commit.yml` and find this section:

```yaml
on:
  schedule:
    - cron: '0 0  * * *'   # Commit 1 — midnight UTC
    - cron: '0 8  * * *'   # Commit 2 — 08:00 UTC
    - cron: '0 16 * * *'   # Commit 3 — 16:00 UTC
```

Each line = one commit per day. Add or remove lines to control the count.

| Commits per day | What to do |
|---|---|
| 1 | Keep only one `cron:` line |
| 3 | Default — keep all three |
| 5 | Add two more cron lines |

Need help with cron syntax? → [crontab.guru](https://crontab.guru)

---

### 4. Push to Main

If you forked, you're already done. If you created the file manually on GitHub, the commit already pushed it.

Either way, once the file is on the `main` branch, GitHub will pick up the schedule automatically. No further action needed.

---

### 5. Test It Manually

Don't wait until midnight to find out something is broken.

1. Go to your repo → **Actions** tab
2. Click **Daily Auto Commit** in the left sidebar
3. Click **Run workflow** → **Run workflow**
4. Watch it run — all steps should be green ✓
5. Go back to the **Code** tab — you should see a new commit and a `logs/` folder

If it's green, you're set. The bot will take it from here.

---

## 🎛️ Customization

| What | Where | How |
|---|---|---|
| Number of commits/day | `daily-commit.yml` | Add or remove `cron:` lines |
| Time of commits | `daily-commit.yml` | Edit the cron expressions |
| Log file location | `daily-commit.yml` | Change the `LOG_FILE` path |
| Max log lines kept | `daily-commit.yml` | Change `tail -500` to any number |

---

<p align="center">
  Built with zero guilt and maximum automation.<br/>
  <i>The snake will be fed.</i> 🐍
</p>
