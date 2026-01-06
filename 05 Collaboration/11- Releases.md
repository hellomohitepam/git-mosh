## 📦 GitHub Releases & Versioning
*Releases are essentially a way to package your software at a specific point in time (like v1.0.0) so users can download the code or compiled binaries without looking through your commit history.
*Use Releases to mark stable "milestones" of your project for users to download.*

### 1. The Relationship: Tags vs. Releases
* **Git Tag:** A permanent "bookmark" in your history tied to a specific commit.
* **GitHub Release:** A "wrapper" around that tag that adds a title, description, and downloadable files (like .exe or .zip).

### 2. Creating a Release (The GitHub Way)
1.  On your repo page, click **Releases** (on the right sidebar).
2.  Click **Create a new release**.
3.  Click **Choose a tag** and type your version (e.g., `v1.0.0`). Click **Create new tag**.
4.  Add a **Release Title** (e.g., "The Gold Update") and a **Description**.
    * *Tip: Click "Generate release notes" to automatically list all Pull Requests since the last version.*
5.  (Optional) Attach binaries, installers, or compiled files in the "Attach binaries" box.
6.  Click **Publish release**.

### 3. Creating a Tag (The Terminal Way)
If you prefer to mark the version in your command line first:
```
# 1. Create a tag locally
git tag -a v1.0.0 -m "Release version 1.0.0"

# 2. Push the tag to GitHub
git push origin v1.0.0
```

🏷️ Versioning Convention (SemVer)
Type,   Format,  When to use
Major,  1.0.0,   Big changes that break old code.
Minor,  0.1.0,   New features added in a backward-compatible way.
Patch,  0.0.1,   Small bug fixes.
