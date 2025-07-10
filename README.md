# 🔥 GitHub Streak Keeper

Keep your GitHub contribution streak alive — automatically!  
A GitHub Action that checks your daily activity and makes a fallback commit to preserve your streak when needed.



## 📌 What It Does

GitHub streaks are a great way to stay consistent, but life happens — and forgetting to commit even once can reset your streak to zero.  
**GitHub Streak Keeper** helps by:

✅ Checking every day at **11:50 PM IST** whether you made any contribution  
✅ If **you did**, it does nothing  
✅ If **you didn’t**, it makes a fallback commit to this repo to keep your streak alive  
✅ Fully automated via **GitHub Actions** — no need to install or run anything manually



## 🌟 Features

- ⏰ Runs **daily** at 11:50 PM IST (adjustable)
- ✅ Detects **any type of contribution** (commits, PRs, issues, etc.)
- 💾 Fallback commits only happen when no activity is found
- 📁 Minimalistic — just one repo, one file
- 🔐 Works securely using GitHub's built-in `GITHUB_TOKEN`
- 🧠 Written in **pure GitHub Actions**, no external server required



## 🛠️ Setup Instructions

Follow these steps to set this up on your GitHub account:

### 1. 🍴 Fork this repository

Click the "Fork" button at the top right of this page to copy the repo to your account.

> You can also rename it to something like `streak-keeper`, `daily-commit-saver`, etc.



### 2. ✅ Enable GitHub Actions

In your forked repo:
- Go to the **"Actions"** tab
- Click **“I understand”** if prompted to enable GitHub Actions



### 3. 📅 Customize (Optional)

By default, this action runs **daily at 11:50 PM IST**.  
If you want to change the time, edit the cron schedule in:

`.github/workflows/streak-keeper.yml`

```yaml
on:
  schedule:
    - cron: '20 18 * * *'  # This is 11:50 PM IST (UTC+5:30)
````

> Use [crontab.guru](https://crontab.guru) to convert time zones.



## 🚀 How It Works (Under the Hood)

1. The workflow runs every night via `cron`.
2. It uses the **GitHub GraphQL API** to check if you've made any contribution that day.
3. If **none found**, it appends a line to a local `streak_log.txt` file and commits the change.
4. The commit keeps your **green square alive** and your streak going.



## 🖼️ Example Commit (when triggered)

```bash
"Streak saver commit - 2025-07-08T23:50:00Z"
```

You’ll find this in your commit history only when needed.



## 👥 Who Is This For?

* Developers who care about their GitHub contribution graph
* People working on private/local projects who may forget to push every day
* OSS contributors who want a fallback on slow days



## 🙋 FAQ

### Will it work with private repos?

Yes — it checks **your profile's overall contributions**, including private contributions (as long as they're marked as such in GitHub settings).

### Does it affect my real projects?

No. This commits only to this repo, and only when needed. Nothing else is touched.

### Does it push empty commits?

No. It writes a line in `streak_log.txt` to make the commit meaningful.



## 🙌 Contributing

Feel free to submit PRs to:

* Improve error handling
* Add support for PR/issue-specific fallback logic
* Make it work with timezone detection or dynamic scheduling



## 💖 Support

If this helped save your streak or gave you peace of mind, consider:

* 🌟 Starring this repo
* 🍴 Forking and using it
* 📢 Sharing with others who may benefit



## 📄 License

MIT License © 2025
