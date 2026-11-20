# Contributing to Community Recipe Book

This guide covers everything you need to know before opening a pull request: recipe format, branch naming, commit style, and what reviewers will check.

Read it once before you start. It will save you a round-trip of review feedback.

---

## Recipe Format

Every recipe must use this exact template. Copy it, fill it in, and delete the placeholder text.

```markdown
# Recipe Name

**Category:** breakfast | lunch | dinner | desserts | drinks  
**Prep time:** X minutes  
**Cook time:** X minutes  
**Servings:** X  
**Difficulty:** Easy | Medium | Hard  

> One sentence that makes someone want to cook this dish.

---

## Ingredients

- 2 cups all-purpose flour
- 1 tsp salt
- ...

*List every ingredient with exact quantities. Use standard units (cups, tbsp, tsp, g, ml).*

---

## Instructions

1. Preheat the oven to 180°C (350°F).
2. In a large bowl, combine the flour and salt.
3. ...

*Each step must be its own numbered item. Be specific — "bake until golden" is not enough; write "bake for 25–30 minutes until the top is golden brown and a toothpick inserted in the center comes out clean."*

---

## Notes

- *Optional: substitutions, storage tips, variations, or anything a first-timer should know.*
- *Remove this section if you have nothing to add.*

---

## About This Recipe

*One or two sentences about where this dish comes from or why you like it. This is the human part — make it yours.*
```

---

## File Naming

- Location: `recipes/<category>/<dish-name>.md`
- Use only lowercase letters, numbers, and hyphens.
- No spaces, no underscores, no special characters.

| Good | Bad |
|------|-----|
| `recipes/dinner/jollof-rice.md` | `recipes/dinner/Jollof Rice.md` |
| `recipes/desserts/banana-bread.md` | `recipes/desserts/banana_bread.md` |
| `recipes/drinks/mango-lassi.md` | `recipes/drinks/MangoLassi.md` |

---

## Branch Naming

```
recipe/<dish-name>
```

The dish name in the branch should match the filename.

| Good | Bad |
|------|-----|
| `recipe/jollof-rice` | `feature/my-recipe` |
| `recipe/banana-bread` | `add-stuff` |
| `recipe/mango-lassi` | `patch-1` |

---

## Commit Messages

Write commit messages that are specific and self-explanatory — someone reading the history should immediately know what this commit contains:

| Good | Bad |
|------|-----|
| `Add jollof rice to dinner` | `Added file` |
| `Fix missing oven temperature in step 2` | `Fixed` |
| `Add my name to AUTHORS` | `update` |

Format: start with a capital letter, use the imperative mood ("Add", "Fix", "Update"), no period at the end, under 72 characters.

---

## Pull Request Checklist

Before you submit, verify every item:

- [ ] My branch is named `recipe/<dish-name>`
- [ ] My file is in the correct category folder
- [ ] My filename uses lowercase and hyphens only
- [ ] I used the recipe template and filled in every required field
- [ ] Every ingredient has a quantity
- [ ] Every instruction step is numbered and specific
- [ ] I added myself to `AUTHORS.md`
- [ ] I have reviewed at least one other open PR

---

## What Reviewers Check

Reviewers are looking for one thing: **can someone who has never made this dish follow these instructions and get a good result?**

Specifically:

| Area | What to look for |
|------|-----------------|
| Ingredients | Are all quantities present? Are units clear? |
| Instructions | Is every step numbered? Is each step specific enough? |
| Completeness | Are preheat temperatures included? Cook times? |
| Format | Does the file follow the template? |
| Filename | Lowercase, hyphens, correct folder? |

Reviewers should **not** request changes based on personal taste, ingredient choices, or cultural differences. A dish is valid if it can be made and eaten.

---

## Resolving Merge Conflicts

Merge conflicts happen when two people edit the same part of the same file. In this project, `AUTHORS.md` is edited by everyone, so conflicts are expected and normal.

When you see a conflict, Git marks the file like this:

```
<<<<<<< HEAD
your changes
=======
their changes
>>>>>>> upstream/main
```

To resolve it:

1. Open the file in your editor.
2. Keep both sets of changes — delete only the three marker lines.
3. Save the file.
4. `git add AUTHORS.md`
5. `git commit -m "Resolve merge conflict in AUTHORS.md"`
6. `git push origin recipe/<dish-name>`

If you are unsure, ask for help in an issue. Never delete a classmate's row from `AUTHORS.md`.

---

## Questions

Open an issue with the label `question`. Include which task you are on and what you have already tried.
