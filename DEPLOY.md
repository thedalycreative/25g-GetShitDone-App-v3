# Deployment Guide 🚀

To get **GetShitDone** live, follow these steps. This project uses a **Split Deployment** architecture:
-   **Front-End**: Hosted on **GitHub Pages** (Static)
-   **Back-End**: Hosted on **Render.com** (Live Express Server)

---

## 1. Prepare GitHub
1.  **Commit and Push** your changes to GitHub.
    ```bash
    git add .
    git commit -m "Prepare for deployment"
    git push origin main
    ```
2.  Wait for the **GitHub Action** to finish (check the **Actions** tab in your repo).
3.  Go to **Settings > Pages** in your repo:
    -   **Source**: Deploy from a branch.
    -   **Branch**: Select `gh-pages` and `/root`.
    -   **Save**. Your frontend is now live at `https://<your-username>.github.io/<repo-name>/`!

---

## 2. Deploy Back-End to [Render.com](https://render.com)
1.  Create a **New > Web Service**.
2.  Connect your GitHub repository.
3.  **Runtime**: `Node`
4.  **Root Directory**: leave blank (top-level)
5.  **Build Command**: `npm install`
6.  **Start Command**: `npm start`
7.  **Environment Variables**:
    -   Click **Advanced** and add your `.env` variables:
        -   `MONGO_URI`
        -   `GMAIL_USER`
        -   `GMAIL_PASS`
        -   `MAIL_RECIPIENT`
8.  **Deploy**. Render will give you a URL like `https://getshitdone-backend.onrender.com`.

---

## 3. Link Them Together
1.  Copy your live **Render URL**.
2.  Open `public/js/app.js` and `public/js/main.js`.
3.  Find `API_BASE` and replace the placeholder with your **Render URL**.
4.  **Push** to GitHub again:
    ```bash
    git add .
    git commit -m "Add live backend URL"
    git push origin main
    ```

---

## Why this way?
GitHub Pages is fantastic for free static hosting (HTML/CSS/JS), but it **cannot run Node.js/Express code**. By hosting the logic on Render and the site on GitHub, you get a professional, fast, and free production environment!
