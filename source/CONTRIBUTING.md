## 🤝 Contribution Culture & Feedback

Welcome! We’re glad you want to contribute to this project. To ensure high-quality contributions and smooth collaboration, please follow the guidelines below.

**We value teamwork, clarity, and purpose. Please read this before submitting any contributions.**

> 🧠 **Note 1:** This project follows a **fork-based workflow**.  
> Please fork the repository, create a feature branch in your fork (from `main`), and submit a pull request from your fork to this repository.

### 📌 Semantic Versioning
> 🧠 **Note 2:** We use **Semantic Versioning** (`vMAJOR.MINOR.PATCH`) to manage this project's progress:  
> - `MAJOR`: Incompatible or structural changes  
> - `MINOR`: New sections, chapters, or significant improvements  
> - `PATCH`: Minor edits like typos or formatting  
> The current version of this book is: **v1.0.0**

**Please suggest version bumps in your PR if applicable.**


## 🛠 Fork Workflow & Branch Naming

If you're contributing to this project using a fork:

### 🔁 Fork Naming
- Suggested: `my-cpp-book-<your-username>`
- Optional but helps differentiate your fork.

### 🌿 Branch Naming (Inside Your Fork)
Use this format: <your-username>/<short-feature-description>

**Examples:**
- `wahba/improve-readme`


## 🚀 Contribution Steps

### 1. Fork the Repository

Click the **Fork** button at the top of the repository to create a copy under your GitHub account.


### 2. Clone Your Fork

Clone your forked repository to your local machine:

```bash
git clone https://github.com/your-username/repo-name.git
cd repo-name
```
### 3. Add the Original Repository as a Remote
This allows you to sync your fork with the upstream repository:

```bash
git remote add upstream https://github.com/original-owner/repo-name.git
```

### 4. Create a Feature Branch

```bash
git checkout -b your-username/your-feature-name
```
Use the naming format described above.

### 5. Make Your Changes

 Focus on a single improvement or fix
 Follow existing code style and formatting
 Update documentation as needed

### 6. Commit changes: 

```bash
git commit -m "Fix: corrected typos in Chapter 3"
```

### 7. Sync with the Upstream Before Opening a PR
Before pushing your changes:

```bash
git fetch upstream
git checkout main
git merge upstream/main

```

### 8. Squash Your Commits (If Multiple)
Squash your work into a single clean commit:

```bash
git rebase -i HEAD~n  # Replace n with number of commits
```
### 9. Then force push to your fork:
If you rebased your commits locally, you'll need to force-push them to your forked repo:

```bash
git push origin your-branch-name --force-with-lease
```
**💡 We recommend using `--force-with-lease` instead of `--force`, even when pushing to your own fork, as it safely checks for remote updates before overwriting history.**

### 9. Open a Pull Request
Open a PR from your forked branch to the main branch of the upstream repo.

**✅ Ensure your PR:**

> Follows the naming format

> Includes a clear title and description

> Mentions suggested version bump (v1.1.0, v1.0.1, etc.)

**✅ PR Guidelines**

> Keep PRs focused and well-scoped.

> Use clear and meaningful commit messages.

> Follow the structure of the book.

> Be constructive and respectful in communication.

   
**To keep your work structured, we recommend following the **GitFlow branching strategy** within your fork (e.g., `feature/`, `bugfix/`, `hotfix/`).**

> 🔧 Optional but preferred:  
> Use the **[GitFlow Cheatsheet (by Daniel Kummer)](https://danielkummer.github.io/git-flow-cheatsheet/)** extension in GIT to speed up and organize your branching process, and this is the Extension **[GitHub Repo](https://github.com/petervanderdoes/gitflow-avh.git).**

Please make sure your pull requests are clear, focused, and include meaningful commit messages.

## 🤝 We need your help!
- 📝 Found a typo or bug?
- 💬 Want to improve examples? 

### ✅ Before You Start
  Read the `README.md` for project context and goals
  Choose a task aligned with open Issues or roadmap
  Fork and clone the repository
  Follow branch naming and versioning rules

| 🧠 All changes must come via fork + PR — no direct push to main.

**All contributors get:**
- Permanent credit in release notes
- Priority on feature requests or fixes

### 💬 Feedback
-  For  bug reports, please [open an Issue](https://github.com/AIOps-Vision/Mastering-Basics-in-Cpp-for-Beginners/issues).

-  For open discussions, suggestions, or to ask a question, please [start a new Discussion](https://github.com/AIOps-Vision/Mastering-Basics-in-Cpp-for-Beginners/discussions).

© 2025 Wahba Mousa
---


