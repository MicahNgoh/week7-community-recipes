# 🍳 Community Recipe Book

A collaborative cookbook built entirely through Git and pull requests.
Every recipe in this book was contributed by a real person, reviewed by a peer, and merged through a proper workflow — just like production software.

By the time you finish, you will have practiced the full collaboration cycle used on real teams: branching, writing a good pull request, reviewing someone else's work, resolving a merge conflict, and keeping your fork in sync.

---

## What You Will Build

You will add **one recipe** of your choice to this shared cookbook. Your recipe will go through:

1. A branch on your fork
2. A pull request with a filled-in description template
3. A code review by a classmate
4. Any fixes based on feedback
5. A merge into `main`

When every student is done, this repository becomes a real cookbook anyone can browse.

---

## Project Structure

```
community-recipe-book/
├── recipes/
│   ├── breakfast/
│   ├── lunch/
│   ├── dinner/
│   ├── desserts/
│   └── drinks/
├── AUTHORS.md        ← everyone signs here (merge conflict exercise)
├── CONTRIBUTING.md   ← read this before you start
└── README.md         ← you are here
```

---

## Tasks

### Task 1 — Set Up Your Fork

You need your own copy of this repository to work on.

1. Click **Fork** (top-right on GitHub) to copy the repo to your account.
2. Clone **your fork** — not the original:
   ```bash
   git clone https://github.com/<your-username>/week7-community-recipes.git
   cd week7-community-recipes
   ```
3. Add the original as a remote called `upstream` so you can pull updates:
   ```bash
   git remote add upstream https://github.com/honorezemagho/week7-community-recipes.git
   ```
4. Verify your remotes:
   ```bash
   git remote -v
   ```
   You should see both `origin` (your fork) and `upstream` (the original).

---

### Task 2 — Read Before You Write

Before adding anything, understand the project.

1. Open `CONTRIBUTING.md` and read it fully — it explains the recipe format, branch naming rules, and what reviewers will check.
2. Browse the `recipes/` folder and open an existing recipe to see the format.
3. Decide what recipe you will add. It must be:
   - Something you have actually made or eaten
   - In a category that already exists (`breakfast`, `lunch`, `dinner`, `desserts`, `drinks`)
   - Not already in the book (check first)

---

### Task 3 — Create Your Branch

Never commit directly to `main`. Feature branches keep the main history clean and make pull requests possible.

Name your branch after the dish you are adding:
```bash
git checkout -b recipe/<dish-name>
```

Examples of good branch names:
- `recipe/jollof-rice`
- `recipe/banana-bread`
- `recipe/mango-lassi`

Check you are on the right branch before you do anything else:
```bash
git branch
```
The branch with `*` in front is your active branch.

---

### Task 4 — Add Your Recipe

1. Create a new Markdown file inside the correct category folder:
   ```
   recipes/<category>/<dish-name>.md
   ```
   Use lowercase and hyphens — no spaces in filenames.

2. Follow the recipe template exactly (see `CONTRIBUTING.md` for the full template). Every field is required.

3. When your file is ready, stage and commit it:
   ```bash
   git add recipes/<category>/<dish-name>.md
   git commit -m "Add <dish name> to <category>"
   ```
   Example: `git commit -m "Add jollof rice to dinner"`

---

### Task 5 — Sign the Authors File (Merge Conflict Exercise)

Everyone in the class edits the same file, `AUTHORS.md`. This will cause a **merge conflict** — and resolving it is part of the exercise.

1. Open `AUTHORS.md` and add your name and dish at the bottom:
   ```markdown
   | Your Name | Jollof Rice | dinner |
   ```
2. Stage and commit:
   ```bash
   git add AUTHORS.md
   git commit -m "Add my name to AUTHORS"
   ```

> **What happens next:** When you open your PR, you may see that `AUTHORS.md` has a conflict with another student's changes. `CONTRIBUTING.md` explains exactly how to resolve it. This is intentional — merge conflicts are normal, and you need to know how to handle them.

---

### Task 6 — Push and Open Your Pull Request

1. Push your branch to your fork:
   ```bash
   git push origin recipe/<dish-name>
   ```
2. Go to your fork on GitHub. Click **Compare & pull request**.
3. Set the **base repository** to the original repo and **base branch** to `main`.
4. Fill in the pull request template completely — every section. A PR with an empty description will be sent back.
5. Submit the PR.

---

### Task 7 — Review a Classmate's PR

**This task is required.** You cannot have your own PR merged until you have reviewed at least one classmate's PR.

1. Go to the **Pull requests** tab of the original repository.
2. Pick an open PR that has not yet been reviewed. If you are one of the first students to submit and no other PRs are open yet, wait — open your PR first, then review a classmate's as soon as one appears. Do not review your own.
3. Click **Files changed** and read their recipe carefully.
4. Leave a review using **Review changes**:
   - If everything looks good: **Approve** with a comment saying what you liked.
   - If something needs fixing: **Request changes** and explain clearly what to fix and why. Be specific and kind — "Missing the oven temperature in step 3" is better than "Incomplete steps."
5. Submit your review.

> Good review comments focus on the recipe being clear and followable, not on personal taste. Would someone who has never made this dish be able to follow these instructions?

---

### Task 8 — Address Feedback on Your Own PR

When a reviewer requests changes:

1. Read every comment carefully.
2. Make the fix on your **same branch** (do not open a new PR):
   ```bash
   # edit the file, then:
   git add recipes/<category>/<dish-name>.md
   git commit -m "Fix: <describe what you fixed>"
   git push origin recipe/<dish-name>
   ```
3. The PR updates automatically.
4. Reply to each review comment to confirm you addressed it — this is professional courtesy and helps the reviewer know what to re-check.
5. Re-request review when you are done.

---

### Task 9 — Resolve a Merge Conflict (if needed)

If your PR shows a conflict on `AUTHORS.md`:

1. Bring the latest `main` into your branch:
   ```bash
   git fetch upstream
   git merge upstream/main
   ```
2. Git will pause and mark the conflict in `AUTHORS.md` with markers like this:
   ```
   <<<<<<< HEAD
   | Your Name | Jollof Rice | dinner |
   =======
   | Classmate Name | Puff Puff | desserts |
   >>>>>>> upstream/main
   ```
3. Edit the file to keep **both rows** — delete only the conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`):
   ```
   | Classmate Name | Puff Puff | desserts |
   | Your Name | Jollof Rice | dinner |
   ```
4. Stage the resolved file and complete the merge:
   ```bash
   git add AUTHORS.md
   git commit -m "Resolve merge conflict in AUTHORS.md"
   git push origin recipe/<dish-name>
   ```

---

### Task 10 — Merge and Clean Up

Once your PR is approved:

1. Merge it on GitHub using **Squash and merge** (your instructor may specify which merge strategy to use).
2. Switch back to `main` locally and pull the latest:
   ```bash
   git checkout main
   git pull upstream main
   ```
3. Delete your local feature branch:
   ```bash
   git branch -d recipe/<dish-name>
   ```
4. Delete the remote branch on your fork:
   ```bash
   git push origin --delete recipe/<dish-name>
   ```

Your recipe is now part of the shared cookbook.

---

## What You Practiced

| Skill | Where |
|-------|-------|
| Forking and syncing with upstream | Task 1, Task 9 |
| Feature branch workflow | Task 3 |
| Atomic, descriptive commits | Tasks 4–5 |
| Writing a pull request description | Task 6 |
| Peer code review | Task 7 |
| Responding to review feedback | Task 8 |
| Merge conflict resolution | Task 9 |
| Branch cleanup | Task 10 |

---

## Need Help?

- Read `CONTRIBUTING.md` — it answers most questions about format and workflow.
- Open an issue on this repository with the label `question`.
- Do not ask a classmate to approve your own PR — that defeats the review.
