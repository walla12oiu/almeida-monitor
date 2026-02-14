[README.md](https://github.com/user-attachments/files/25315505/README.md)
# 🎭 Almeida Ticket Monitor

Monitors the [Almeida American Psycho 2026 calendar page](https://almeida.co.uk/calendar/?e=american-psycho-2026) every 5 minutes and emails you when it changes.

Runs 24/7 on GitHub's servers — your PC doesn't need to be on.

---

## Setup (one time, ~10 minutes)

### Step 1 — Create a GitHub account
Go to [github.com](https://github.com) and sign up (free).

---

### Step 2 — Create a new repository
1. Click the **+** button top right → **New repository**
2. Name it `almeida-monitor`
3. Set it to **Private**
4. Click **Create repository**

---

### Step 3 — Upload the files
Upload these 3 files to your repo:
- `check_tickets.py`
- `requirements.txt`
- `.github/workflows/monitor.yml` ← this folder structure matters!

To create the folder structure on GitHub:
1. Click **Add file** → **Create new file**
2. In the filename box type: `.github/workflows/monitor.yml`
3. Paste the contents of `monitor.yml`
4. Repeat for the other files at the root level

---

### Step 4 — Set up a Gmail App Password
Gmail won't let scripts use your normal password. You need an "App Password":

1. Go to [myaccount.google.com/security](https://myaccount.google.com/security)
2. Make sure **2-Step Verification** is ON
3. Search for **App Passwords**
4. Create one → name it "Almeida Monitor"
5. Copy the 16-character password it gives you

---

### Step 5 — Add your secrets to GitHub
1. In your repo, go to **Settings** → **Secrets and variables** → **Actions**
2. Click **New repository secret** and add these two:

| Name | Value |
|------|-------|
| `NOTIFY_EMAIL` | your Gmail address (e.g. `you@gmail.com`) |
| `NOTIFY_PASSWORD` | the 16-char App Password from Step 4 |

---

### Step 6 — Done! ✅
GitHub will now run the check every 5 minutes automatically.

To test it manually: go to **Actions** tab → **Almeida Ticket Monitor** → **Run workflow**

---

## How it works
- Every 5 mins GitHub fetches the Almeida page
- It hashes the content and compares to the last saved hash
- If different → sends you an email alert
- The hash is saved back to the repo for next comparison
