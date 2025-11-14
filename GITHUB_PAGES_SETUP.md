# 🚨 GitHub Pages Setup - Visual Guide

## Why Deployments Are Failing

The GitHub Actions deployments are failing because **GitHub Pages is not enabled yet** in your repository settings. This is a **one-time setup** that must be done manually.

---

## ✅ SOLUTION: Enable GitHub Pages (2 minutes)

### Step-by-Step Instructions:

#### 1️⃣ Open GitHub Pages Settings

Click this link: **https://github.com/pikumandal2005/Smart-Tourist-Management/settings/pages**

You should see a page titled "Pages" with settings options.

---

#### 2️⃣ Configure Build and Deployment

You'll see a section called **"Build and deployment"**. Configure it as follows:

**Option A: Simple Deployment (RECOMMENDED)** ⭐

```
Source: Deploy from a branch
  ↓ (Select from dropdown)
  
Branch: main
  ↓ (Select from dropdown)
  
Folder: / (root)
  ↓ (Select from dropdown)
  
[ Save ] ← Click this green button
```

**What This Does:**
- GitHub automatically deploys your `index.html` from the main branch
- Every time you push code, it rebuilds automatically
- No complex GitHub Actions needed
- Works immediately

---

**Option B: GitHub Actions (Advanced)** 🔧

```
Source: GitHub Actions
  ↓ (Select from dropdown)
  
(No other options needed)
  
[ Save ] ← Click this green button
```

**What This Does:**
- Uses the `.github/workflows/pages.yml` file we created
- More control over deployment process
- Requires the workflow to run successfully

---

#### 3️⃣ Wait for Deployment

After clicking "Save":

1. **GitHub starts building** (you'll see a yellow dot ⚠️)
2. **Takes 2-3 minutes** for first deployment
3. **Page refreshes** and shows success message
4. You'll see: **"Your site is live at https://pikumandal2005.github.io/Smart-Tourist-Management/"** ✅

---

#### 4️⃣ Verify Deployment

Once you see the success message:

**Open your live site:**
```
https://pikumandal2005.github.io/Smart-Tourist-Management/
```

**Test the application:**
- ✅ Page loads correctly
- ✅ Can click "Sign up"
- ✅ Firebase connection works
- ✅ Can create account and login

---

## 🔍 What You'll See in GitHub

### Before Enabling Pages:
```
❌ Failed to deploy (completed)
   The environment "github-pages" does not exist
```

### After Enabling Pages:
```
✅ Deployed successfully
   Your site is published at https://...
```

---

## 📊 Check Deployment Status

### View Active Deployments:
https://github.com/pikumandal2005/Smart-Tourist-Management/deployments

### View GitHub Actions (if using Option B):
https://github.com/pikumandal2005/Smart-Tourist-Management/actions

---

## 🐛 Troubleshooting

### Problem: "Source" dropdown is grayed out
**Solution:** 
- Make sure you're the repository owner
- Check if repository is public (go to Settings → General)
- Try logging out and back in to GitHub

### Problem: Still seeing "Failed to deploy"
**Solution:**
1. Make sure you clicked "Save" after configuring
2. Wait 3-5 minutes (first deployment takes time)
3. Refresh the Settings → Pages page
4. Check if you see a green checkmark

### Problem: 404 Error when visiting site
**Solution:**
1. Verify URL is correct (no typos)
2. Make sure `index.html` exists in repository root
3. Clear browser cache (Ctrl+Shift+Delete)
4. Wait another 2-3 minutes

### Problem: Blank page loads
**Solution:**
1. Check browser console (F12) for errors
2. Verify Firebase config is correct in `index.html`
3. Enable Authentication in Firebase Console
4. Check Firestore rules are deployed

---

## 📝 Quick Reference

### Repository URL:
```
https://github.com/pikumandal2005/Smart-Tourist-Management
```

### Settings → Pages URL:
```
https://github.com/pikumandal2005/Smart-Tourist-Management/settings/pages
```

### Live Site URL (after deployment):
```
https://pikumandal2005.github.io/Smart-Tourist-Management/
```

### Files Deployed:
- ✅ index.html (main app)
- ✅ README.md (documentation)
- ✅ All other markdown files
- ✅ Firebase config files

---

## ⚡ After First Deployment

Once GitHub Pages is enabled and working:

### Future Updates are Automatic:
```bash
# Make changes to files
git add .
git commit -m "Updated features"
git push

# GitHub automatically rebuilds and deploys!
# Wait 1-2 minutes, changes are live
```

### No Need to Re-Enable:
- Pages stays enabled forever
- Every push automatically triggers rebuild
- No manual deployment needed

---

## ✅ Checklist

Complete these steps:

- [ ] Open https://github.com/pikumandal2005/Smart-Tourist-Management/settings/pages
- [ ] Select "Deploy from a branch" as Source
- [ ] Select "main" as Branch
- [ ] Select "/ (root)" as Folder
- [ ] Click "Save"
- [ ] Wait 2-3 minutes
- [ ] See "Your site is live" message
- [ ] Visit https://pikumandal2005.github.io/Smart-Tourist-Management/
- [ ] Test signup/login works
- [ ] Verify map loads for tourists

---

## 🎉 Success!

When you see this message on the Settings → Pages page:

```
✅ Your site is live at 
   https://pikumandal2005.github.io/Smart-Tourist-Management/
```

**Your deployment is complete!** 🚀

Share the live URL with anyone to test your application.

---

**Last Updated:** November 14, 2025  
**Status:** ⏳ Waiting for you to enable GitHub Pages  
**Action Required:** Follow steps above
