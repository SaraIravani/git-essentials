
# Handling Large Files with Git LFS 🛠️

If you're trying to push large files to GitHub and encounter an error message indicating that the file exceeds the GitHub file size limit of 100 MB, **Git LFS (Large File Storage)** can help you manage these files. 🚫

## Steps to Resolve the Issue:

### 1. Install Git LFS (if not already installed) 📥

First, you need to install Git LFS. On Ubuntu, you can use the following command:

```bash
sudo apt-get install git-lfs
```

Then, initialize Git LFS in your repository:

```bash
git lfs install
```

### 2. Track Large Files 📂

Next, use Git LFS to track large files that exceed the file size limit. For example, if you have large files like `.zip`, `.tar.gz`, `.iso`, or any other large file types, you can track them with Git LFS:

```bash
git lfs track "*.zip"
```

This command will ensure that any `.zip` file in your repository is tracked by Git LFS. You can adjust the pattern to match other large file types as needed.

### 3. Commit the Changes 💾

Now, add the changes to Git and commit them:

```bash
git add .gitattributes
git add path/to/your/large/file.zip
git commit -m "Track large files with Git LFS"
```

### 4. Remove the Large File from History 🗑️

If the large file has already been committed to your Git history, you need to remove it. Use **BFG Repo-Cleaner** or `git filter-branch`. If you have `bfg.jar` in your repository, you can run:

```bash
java -jar bfg.jar --delete-files "*.zip" --no-blob-protection
```

Then, clean up the repository:

```bash
git reflog expire --expire=now --all
git gc --prune=now
```

### 5. Push the Changes 🚀

Now that Git LFS is tracking the large files and the history has been cleaned, you can push your changes:

```bash
git push -u origin main --force
```

### 6. Verify Everything Works ✅

Ensure that the large files are now being tracked by Git LFS and are no longer part of the regular Git history.

To check if the files are correctly tracked by Git LFS, run:

```bash
git lfs ls-files
```

This will list the files being managed by Git LFS.

---

By following these steps, your repository will be able to handle large files efficiently using Git LFS without hitting GitHub's size limit! 🎉

