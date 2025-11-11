# ASO Checklist (GitHub Pages + Firebase Auth)


A static site (hosted on GitHub Pages) with Firebase Authentication protecting the checklist app.


## 1) Firebase setup
1. Go to Firebase Console → Add project.
2. Build → Authentication → Get started.
3. Enable providers you want (Email/Password, Google).
4. Project Settings → Your apps → Web app → copy the config.
5. Authentication → Settings → Authorized domains → add:
- your-username.github.io
- your-username.github.io/<repo-name>
- any custom domain you plan to use


## 2) Configure the app
- Open `index.html` and `login.html` and replace the `firebaseConfig` placeholders with your values.
- Paste your existing checklist markup into `index.html` where indicated.
- Ensure any direct `init()` call is removed; the Auth Guard will call it.


## 3) Deploy to GitHub Pages
1. Create a public repo and push these files.
2. In GitHub → **Settings** → **Pages** → Source: `Deploy from a branch`.
3. Branch: `main`, Folder: `/ (root)` → Save.
4. Wait for the green check on the Pages deploy. Your site will be live at:
- https://<username>.github.io/<repo-name>/


## 4) Local testing
- You can open the HTML files directly, but Google sign-in may block popups from `file://` URLs. Best to run a tiny local server:
```bash
# Python 3
python3 -m http.server 8080
# then open http://localhost:8080/login.html