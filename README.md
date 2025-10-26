
---

🧾 README.md

# 🌐 Deploy Website to GitHub Using Termux

This guide explains how to **connect Termux with GitHub**, **deploy your website**, and **fix the 403 permission error** using SSH authentication.

---

## ⚙️ Step 1: Update Termux
Update and upgrade all packages:
```bash
pkg update && pkg upgrade -y
```

---

🧩 Step 2: Install Git

Install Git in Termux:
```bash
pkg install git -y
```

Check version:
```bash
git --version
```

---

👤 Step 3: Configure Git (Your GitHub Info)

Set your username and email (replace with your own):

```bash
git config --global user.name "BuiltByAmos-1801"
git config --global user.email "builtbyiamos@gmail.com"
```

Check configuration:
```bash
git config --list
```

---

🔐 Step 4: Generate SSH Key

Generate SSH key for secure authentication:

```bash
ssh-keygen -t rsa -b 4096 -C "builtbyiamos@gmail.com"
```

Press Enter for all prompts.

View your public SSH key:
```bash
cat ~/.ssh/id_rsa.pub
```

---

🌍 Step 5: Add SSH Key to GitHub

1. Copy the key from the above command.
2. Go to GitHub → Settings → SSH and GPG Keys → New SSH key
3. Title: Termux
4. Paste the key and save.

---

🧪 Step 6: Test SSH Connection

Verify the SSH connection:
```bash
ssh -T git@github.com
```
If successful, you’ll see:

> Hi BuiltByAmos-1801! You’ve successfully authenticated...

---

📂 Step 7: Clone Your GitHub Repository

Example:
```bash
git clone git@github.com:BuiltByAmos-1801/BuiltByAmosPortfolio.git
```

Then navigate:
```bash
cd BuiltByAmosPortfolio
```

---

🕸 Step 8: Add Your Website Files

Add your index.html, style.css, and other website files inside this folder.

Create a file if needed:
```bash
touch index.html
```

---

💾 Step 9: Commit and Push Your Changes

```bash
git add .
git commit -m "Initial website deployment"
git push -u origin main
```

---

⚠️ Error: 403 Permission Denied

If you see this error:

remote: Permission to BuiltByAmos-1801/Repo.git denied to BuiltByAmos-1801.
fatal: unable to access 'https://github.com/...': The requested URL returned error: 403

That means Git is using HTTPS instead of SSH.

---

🧰 Step 10: Fix 403 Error (Switch HTTPS → SSH)

1. Check current remote URL
```bash
git remote -v
```

2. Change remote URL to SSH
```bash
git remote set-url origin git@github.com:BuiltByAmos-1801/BuiltByAmosPortfolio.git
```

3. Verify
```bash
git remote -v
```

Should show:

origin  git@github.com:BuiltByAmos-1801/BuiltByAmosPortfolio.git (fetch)  
origin  git@github.com:BuiltByAmos-1801/BuiltByAmosPortfolio.git (push)

4. Push again
```bash
git add .
git commit -m "Website deployment fixed"
git push -u origin main
```

✅ Now your website will upload without errors.

---

🚀 Step 11: Enable GitHub Pages

1. Go to your GitHub repository → Settings → Pages
2. Under Source, select main branch and /root
3. Click Save

Your site will be live at:
```
https://BuiltByAmos-1801.github.io/BuiltByAmosPortfolio/
```

---

💡 Optional: One-Line SSH Fix

To automatically switch all HTTPS remotes to SSH:
```bash
git remote set-url origin $(git remote get-url origin | sed 's#https://github.com/#git@github.com:#')
```

---

✅ Example Full Setup Commands

```bash
pkg update && pkg upgrade -y
pkg install git -y
git config --global user.name "BuiltByAmos-1801"
git config --global user.email "builtbyiamos@gmail.com"
ssh-keygen -t rsa -b 4096 -C "builtbyiamos@gmail.com"
cat ~/.ssh/id_rsa.pub
ssh -T git@github.com
git clone git@github.com:BuiltByAmos-1801/BuiltByAmosPortfolio.git
cd BuiltByAmosPortfolio
git add .
git commit -m "Initial website deployment"
git push -u origin main
```

---

👨‍💻 Author

Amos Anand  
🚀 Developer | Designer | Blogger | YouTuber  
🔗 BuiltByAmos GitHub

---

Would you like me to:
- 📦 Create this file (`README.md`) automatically in your Termux folder  
**and**
- 💥 Add the one-line SSH fix command at the end (so every future repo connects via SSH instantly)?
