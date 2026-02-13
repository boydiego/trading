# GitHub Sync & Deployment Guide

This guide will help you deploy your Trading Journal to GitHub Pages and set up automatic synchronization across all your devices.

## 📋 Table of Contents

1. [Deploy to GitHub Pages](#deploy-to-github-pages)
2. [Create GitHub Personal Access Token](#create-github-personal-access-token)
3. [Configure GitHub Sync](#configure-github-sync)
4. [Using the Dashboard](#using-the-dashboard)
5. [Troubleshooting](#troubleshooting)

---

## 🚀 Deploy to GitHub Pages

### Step 1: Push Your Code to GitHub

You mentioned you already have a private repository at `https://github.com/boydiego/trading`

If you haven't pushed the latest changes yet:

```bash
cd c:\Users\dboy\trading
git add .
git commit -m "Add GitHub Gist auto-sync functionality"
git push origin main
```

### Step 2: Enable GitHub Pages

1. Go to your repository: https://github.com/boydiego/trading
2. Click **Settings** (top navigation)
3. In the left sidebar, click **Pages**
4. Under **Source**, select:
   - **Branch:** `main`
   - **Folder:** `/ (root)`
5. Click **Save**

GitHub will start deploying your site. This takes about 1-2 minutes.

### Step 3: Access Your Dashboard

Once deployed, your dashboard will be available at:

```
https://boydiego.github.io/trading/trading-journal.html
```

**Bookmark this URL** on all your devices (work laptop, personal laptop, phone)!

---

## 🔑 Create GitHub Personal Access Token

The GitHub token allows the dashboard to automatically sync your trading data across all devices using a private GitHub Gist.

### Step 1: Generate Token

1. Go to: https://github.com/settings/tokens/new
2. Fill in the form:
   - **Note:** `Trading Journal Sync`
   - **Expiration:** `No expiration` (or your preference - 90 days is recommended)
   - **Select scopes:** ✅ **gist** (ONLY this permission needed)
3. Scroll down and click **"Generate token"**

### Step 2: Copy Your Token

⚠️ **IMPORTANT:** Copy the token immediately! You won't be able to see it again.

The token will look like: `ghp_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx`

**DO NOT SHARE THIS TOKEN WITH ANYONE!**

---

## ⚙️ Configure GitHub Sync

### On Your First Device (e.g., Work Laptop)

1. Open the dashboard: https://boydiego.github.io/trading/trading-journal.html
2. Click the **"⚙️ Setup GitHub Sync"** button (top right)
3. Paste your GitHub token in the input field
4. Click **"Save & Enable Sync"**

The dashboard will:
- ✅ Verify your token is valid
- ✅ Create a private GitHub Gist to store your data
- ✅ Upload your current trades to the Gist
- ✅ Enable automatic sync (every 30 seconds)

### On Your Other Devices (Personal Laptop, Phone)

1. Open the same dashboard URL: https://boydiego.github.io/trading/trading-journal.html
2. Click **"⚙️ Setup GitHub Sync"**
3. Paste the **same GitHub token** you created earlier
4. Click **"Save & Enable Sync"**

The dashboard will:
- ✅ Load your existing trades from GitHub Gist
- ✅ Enable automatic sync

**All your devices are now synced!** 🎉

---

## 💡 Using the Dashboard

### Automatic Sync

Once configured, the dashboard automatically syncs:
- ✅ Every **30 seconds** in the background
- ✅ Immediately when you add, edit, or delete a trade
- ✅ When you import new strategies

You'll see the sync status in the header:
- **⟳ Syncing...** - Currently uploading to GitHub
- **⟳ Synced ✓** - Successfully synced (shows for 3 seconds)
- **⟳ Synced** - Idle, ready to sync
- **⟳ Sync Failed** - Error occurred (check your internet connection)

### Manual Sync

Want to force a sync right now?
- Click the **"🔄 Sync Now"** button in the header

### Offline Support

The dashboard works offline using localStorage:
- ✅ Add/edit/delete trades without internet
- ✅ Data is saved locally in your browser
- ✅ When internet returns, data syncs automatically

---

## 🔍 How It Works

### Data Storage

Your trading data is stored in **two places**:

1. **Browser localStorage** (local, per-device)
   - Fast access
   - Works offline
   - Persists across browser sessions

2. **GitHub Gist** (cloud, synced across devices)
   - Private Gist (only you can see it)
   - Auto-synced every 30 seconds
   - Accessible from all your devices

### Sync Flow

**When you add a trade on Work Laptop:**
1. Trade is saved to localStorage (instant)
2. Trade is uploaded to GitHub Gist (within 30 seconds)
3. Personal Laptop and Phone automatically load the new trade

**When you open the dashboard on Personal Laptop:**
1. Dashboard loads local data from localStorage (instant)
2. Dashboard checks GitHub Gist for latest data
3. If GitHub has newer data, it's merged with local data

### Conflict Resolution

If you edit the same trade on two devices at the same time:
- **Last write wins** - The most recent change is kept
- For best results, close trades on one device at a time

---

## 🛠️ Troubleshooting

### "Invalid GitHub token" Error

**Cause:** Token is incorrect or doesn't have the `gist` permission

**Solution:**
1. Go to https://github.com/settings/tokens
2. Delete the old token
3. Create a new token with `gist` permission
4. Configure sync again with the new token

### "Sync Failed" Message

**Possible causes:**
1. **No internet connection** - Wait until you're online, sync will resume automatically
2. **Token expired** - Create a new token and reconfigure
3. **Gist was deleted** - The dashboard will create a new Gist automatically

**Solution:** Click **"🔄 Sync Now"** to retry manually

### Data Not Syncing Between Devices

**Check:**
1. ✅ All devices are using the **same GitHub token**
2. ✅ Sync status shows "Synced" (not "Sync Failed")
3. ✅ Internet connection is active
4. ✅ Refresh the page (Ctrl+R or Cmd+R)

### I Switched Browsers and Lost My Trades

**Cause:** localStorage is browser-specific

**Solution:**
1. Configure GitHub sync on the new browser
2. Your trades will load automatically from GitHub Gist

### Storage Quota Exceeded

**Cause:** Too many trades in localStorage

**Solution:**
1. Export old trades to CSV
2. Clear old trades from the dashboard
3. GitHub Gist will keep your historical data safe

---

## 🔐 Security & Privacy

### Is My Data Safe?

✅ **YES!** Your data is secure:
- GitHub Gist is **private** (only you can access it)
- Your token is stored in browser localStorage (never sent to third parties)
- All communication with GitHub uses **HTTPS**
- No external servers are used (everything is client-side)

### Who Can See My Data?

**Only YOU!**
- Your GitHub Gist is **secret** (not public)
- Your repository is **private**
- Your GitHub token is stored **locally** in your browser

### Can I Revoke Access?

Yes! To disable sync:
1. Go to https://github.com/settings/tokens
2. Find "Trading Journal Sync" token
3. Click **Delete**

The dashboard will continue to work offline using localStorage.

---

## 📱 Mobile Usage

### iOS (iPhone/iPad)

1. Open Safari (or your preferred browser)
2. Navigate to: https://boydiego.github.io/trading/trading-journal.html
3. Tap the **Share** button
4. Select **"Add to Home Screen"**

Now you have a shortcut on your home screen!

### Android

1. Open Chrome (or your preferred browser)
2. Navigate to: https://boydiego.github.io/trading/trading-journal.html
3. Tap the **3-dot menu** (top right)
4. Select **"Add to Home screen"**

The dashboard will work like a native app!

---

## 🎯 Quick Reference

### URLs

- **Dashboard:** https://boydiego.github.io/trading/trading-journal.html
- **GitHub Repo:** https://github.com/boydiego/trading
- **Create Token:** https://github.com/settings/tokens/new
- **Manage Tokens:** https://github.com/settings/tokens

### Sync Settings

- **Auto-sync interval:** Every 30 seconds
- **Storage:** Private GitHub Gist + localStorage
- **Required permission:** `gist` scope only

### Commands (Git)

```bash
# Update dashboard
cd c:\Users\dboy\trading
git add .
git commit -m "Update dashboard"
git push origin main

# Check deployment status
# Go to: https://github.com/boydiego/trading/actions
```

---

## ✅ Success Checklist

- [ ] GitHub Pages deployed successfully
- [ ] Can access dashboard at https://boydiego.github.io/trading/trading-journal.html
- [ ] Created GitHub Personal Access Token
- [ ] Configured GitHub sync on work laptop
- [ ] Configured GitHub sync on personal laptop
- [ ] Configured GitHub sync on phone
- [ ] Added sample trade and verified sync across devices
- [ ] Bookmarked dashboard URL on all devices

---

## 🆘 Need Help?

If you encounter any issues:

1. Check the browser console for error messages (F12 → Console)
2. Verify your internet connection
3. Try creating a new GitHub token
4. Clear browser cache and refresh the page
5. Check GitHub Gist directly: https://gist.github.com/

---

**Happy Trading! 📈**
