## Adding Collaborators (Private/Team Repos)
*Use this to give specific users permission to push code to your repository.*

### 1. Invite via GitHub UI
1. Navigate to your repository on GitHub.
2. Click on **Settings** (top navigation bar).
3. In the left sidebar, click **Collaborators** (under the "Access" section).
4. Click the green **Add people** button.
5. Search for the user by their **GitHub username** or **email**.
6. Select the user and click **Add [Username] to this repository**.

### 2. Acceptance
* The collaborator will receive an email invitation.
* They **must accept** the invitation before they can push changes. 
* They can also accept by visiting `github.com/USER_NAME/REPO_NAME/invitations`.

### 3. Permission Levels
When adding a collaborator, you can often choose their role:

| Role | Permissions |
| :--- | :--- |
| **Read** | Can only view and clone (ideal for reviewers). |
| **Write** | Can pull, push, and manage issues (standard for developers). |
| **Maintain** | Can manage the repo but not sensitive actions like deleting it. |
| **Admin** | Full access, including adding other collaborators and deleting the repo. |

---

## Best Practices for Teams
* **Never push to `main` directly:** Once you have collaborators, protect the `main` branch and require **Pull Requests**.
* **Use Branches:** Each collaborator should create a new branch for their feature:
```
  git checkout -b feature-name
```
Pull before Push: Always run git pull before you start working to ensure you have the latest origin/main code.

## 🔒 Protecting the Main Branch
*Once you have collaborators, you want to prevent anyone (including yourself!) from accidentally breaking the code on GitHub.*

### 1. Why Protect it?
| Branch Protection Rule       | What It Enforces                                  | Why It Matters                                       |
| ---------------------------- | ------------------------------------------------- | ---------------------------------------------------- |
| **No direct push to `main`** | Developers cannot push commits directly to `main` | Prevents unreviewed or unsafe changes                |
| **Pull request required**    | All changes must go through a PR                  | Ensures structured review and discussion             |
| **Minimum approvals**        | Requires 1–2+ reviewers to approve                | Enforces peer review and shared responsibility       |
| **CI/CD must pass**          | Automated tests/build checks must succeed         | Prevents broken builds or failing tests from merging |
| **No force push**            | `git push --force` is blocked                     | Protects commit history from being rewritten         |
|                              |                                                   |                                                      |


### 2. How to Enable Protection
1.  Go to your repo on GitHub and click **Settings**.
2.  In the left sidebar, click **Branches**.
3.  Under **Branch protection rules**, click **Add rule**.
4.  **Branch name pattern**: Type `main`.
5.  **Check these essential boxes**:
    * ✅ **Require a pull request before merging**: This blocks `git push origin main`.
    * ✅ **Require approvals**: Set this to at least `1`. Now, someone else must "Approve" your code before it can go into `main`.
    * ✅ **Do not allow bypassing...**: (Optional) This forces even you (the Admin) to follow the rules.
6.  Click **Create** at the bottom.

---

---

## 🚀 The Team Workflow (Branching)
*With protection enabled, collaborators follow this cycle:*

1.  **Sync Local:** `git pull origin main`
2.  **Create Feature Branch:** `git checkout -b feature-xyz`
3.  **Work & Commit:** `git commit -m "Add feature"`
4.  **Push Branch:** `git push origin feature-xyz`
5.  **Open PR:** On GitHub, click "Compare & pull request."
6.  **Review & Merge:** Once approved, merge the PR into `main` via the GitHub website.
