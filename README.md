###  Connecting to GitHub with a Personal Access Token (PAT)

This section explains how to connect your local project to a remote repository on GitHub for secure version control.

* **Personal Access Token (PAT):** This is a secure password-like key you generate from your GitHub account specifically for Git operations. It provides access to your repositories without needing your main username and password. 

**Commands:**

```bash
git remote set-url origin https://<token>@github.com/<username>/<repository>.git
```

**Explanation:**

1. `git remote set-url origin`: This command sets the URL for the remote repository named "origin" (the default name for your primary GitHub repository).
2. `https://<token>@github.com/<username>/<repository>.git`: This is the URL format for connecting with a PAT. Replace the placeholders:
    * `<token>` with your actual Personal Access Token from GitHub. **Important:** Never share your PAT publicly.
    * `<username>` with your GitHub username.
    * `<repository>` with the name of your resume repository on GitHub.

**Alternative:** You can avoid including the PAT directly in the URL by configuring Git Credential Manager. This is a more secure approach, but requires additional setup.

**Adding Files and Pushing to GitHub**

Now, let's explore how to add your resume file to your local repository and push it to GitHub.

1. **Branching (Optional):**
    * `git branch main`: This creates a new branch named "main" if it doesn't already exist. You can track changes on separate branches before merging them into your main project.
    * You can skip this step if you only want to work on the default branch (usually "master").

2. **Adding Files:**
    * `git add filename`: This adds a specific file (replace "filename" with your resume file name) to the staging area for version control.

3. **Committing Changes:**
    * `git commit -m "name the changes you have done"`: This captures the added file in a snapshot with a descriptive message about your changes.

4. **Pushing to GitHub:**
    * `git push`: This pushes the local changes (the staged file and commit) to the remote repository on GitHub.

**Note:** In some cases, you might need to replace the final `git push` with `git push -u origin main` (or "master" if you didn't create a new branch). This sets the upstream branch and pushes in one step, but it's only needed the first time you push to a new remote branch.

By following these steps and understanding the purpose of each command, you can effectively manage your resume project using Git on GitHub.


