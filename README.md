# 🚀 Pantheon WordPress to Vercel Deployment Guide

A step-by-step guide to exporting your WordPress site from Pantheon and deploying it as a static site on Vercel.

---

## 📋 Prerequisites

*   A [Pantheon](https://pantheon.io/) account with a WordPress site.
*   A [GitHub](https://github.com/) account.
*   A [Vercel](https://vercel.com/) account.
*   Git installed on your computer (optional but recommended).

---

## 🔹 STEP 1: Login to Your Pantheon WordPress Admin

1.  Navigate to your WordPress dashboard URL:
    ```
    https://your-site-name.pantheonsite.io/wp-admin
    ```
2.  Log in using your WordPress credentials.

---

## 🔹 STEP 2: Install “Simply Static” Plugin

1.  Go to **Plugins → Add New** in the sidebar.
2.  Search for **Simply Static**.
3.  Click **Install Now**.
4.  Click **Activate**.

---

## 🔹 STEP 3: Configure Simply Static (VERY IMPORTANT)

Go to **Simply Static → Settings**.

### A️⃣ General Settings

*   **Destination URLs**: Select **Local Directory**.
*   **Local Directory Path**:
    *   Set this to a writable path, for example: `/wp-content/uploads/static-site`
*   **URLs to include**: Leave as default.

### B️⃣ Advanced Settings

*   **Check (✔) the following:**
    *   Include images
    *   Include CSS & JS
    *   Include pages & posts
*   **Uncheck (❌) the following:**
    *   Search pages
    *   Admin pages

Click **Save Settings**.

---

## 🔹 STEP 4: Generate Static Website

1.  Go to **Simply Static → Generate**.
2.  Click **Generate Static Files**.
3.  Wait for the process to finish (usually 2–5 minutes).
4.  You will see a success message: **“Export completed successfully”**.

---

## 🔹 STEP 5: Download the Static ZIP

1.  Go to **Media → Library**.
2.  Locate the folder (or zip if packaged) corresponding to your export path (e.g., `/static-site/`).
3.  **Download ALL files**.
    *   *Tip: If you have file access via SFTP (Cyberduck/FileZilla) or the Pantheon dashboard, you can download the entire folder as a ZIP.*

**Your folder structure should look like this:**
```text
index.html
about/index.html
contact/index.html
wp-content/
...
```

---

## 🔹 STEP 6: Prepare Files on Your Computer

1.  Extract the downloaded ZIP (if zipped).
2.  **Verify the structure**: Ensure `index.html` is in the **ROOT** folder.

    ❌ **Wrong**:
    ```text
    static-site/index.html
    ```

    ✅ **Correct**:
    ```text
    index.html
    wp-content/
    ```

---

## 🔹 STEP 7: Create GitHub Repository

1.  Go to [https://github.com](https://github.com).
2.  Click the **+** icon and select **New Repository**.
3.  Name it (e.g., `wordpress-static-site`).
4.  Set visibility to **Public**.
5.  Click **Create Repository**.

---

## 🔹 STEP 8: Push Files to GitHub

### Method A: Upload via GitHub UI (Easiest for Beginners)

1.  Open your new repository on GitHub.
2.  Click **Add file → Upload files**.
3.  **Drag & drop ALL extracted files** (folders and files) into the area.
4.  Wait for uploads to finish.
5.  Click **Commit changes**.

### Method B: Git Commands (Terminal)

Open your terminal in the project folder and run:

```bash
git init
git add .
git commit -m "Static export from WordPress"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/wordpress-static-site.git
git push -u origin main
```

---

## 🔹 STEP 9: Deploy on Vercel 🚀

1.  Go to [https://vercel.com](https://vercel.com).
2.  Log in with **GitHub**.
3.  Click **Add New... → Project**.
4.  **Import** your `wordpress-static-site` repository.
5.  **Configure Project**:
    *   **Framework Preset**: Select **Other**.
    *   **Build Command**: Leave empty (default).
    *   **Output Directory**: Leave empty (default).
6.  Click **Deploy**.
7.  Wait 30–60 seconds.

---

## 🎉 DONE! YOUR SITE IS LIVE

Your site will be available at a URL like:
`https://wordpress-static-site.vercel.app`

### ✅ Benefits
*   Never expires.
*   Super fast performance.
*   Works independently of Pantheon.

### ⚠️ Limitations (Static Site)
*   **No WordPress Admin**: You cannot edit content on the live site. You must edit on Pantheon, re-export, and push to GitHub to update.
*   **Forms**: Standard WP forms/comments won't work. Use alternatives like [Formspree](https://formspree.io/) or Google Forms.
*   **Dynamic Plugins**: E-commerce or membership plugins requiring backend logic will not function.

---

*Verified for Portfolio, College Projects, and Read-Only Blogs.*
