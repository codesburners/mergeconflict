# mergeconflict

A hands-on Git learning repository designed to demonstrate **merge conflicts** and collaborative branching workflows in a safe, reproducible environment.

---

## What is this project?

`mergeconflict` is a minimal, purpose-built Git sandbox that walks you through one of the most common challenges in collaborative software development: **merge conflicts**.

When multiple contributors work on the same file simultaneously and make different changes, Git cannot automatically decide which version to keep. This repository recreates that scenario step-by-step so you can see exactly how conflicts arise and how to resolve them.

### How it works

The repository contains a single file, `test.txt`, which is modified on two separate branches:

| Branch | Change |
|--------|--------|
| `branch1` | Sets `city` to `Bengaluru` |
| `branch2` | Sets `city` to `Chennai` |

Both branches diverge from the same base commit (where `city` is `None`). Merging them into `main` produces a conflict because both branches changed the same line in different ways. You can inspect each branch and merge step to understand exactly what Git detects and how conflict markers appear in the file.

---

## Why this project is unique

Most tutorials about merge conflicts describe the concept using diagrams or hypothetical code snippets. This repository is different:

- **Real conflict, not simulated** – The conflict is baked into the commit history. You can checkout any branch, run `git merge`, and reproduce the conflict yourself instantly.
- **Zero setup** – No dependencies, no build tools, no language runtime required. Anyone with Git installed can clone and start learning immediately.
- **Self-contained history** – Every step of the conflict lifecycle (diverging branches, conflicting changes, merge resolution) is preserved in the commit log so you can replay and study it.
- **Minimal noise** – The repository contains only what is necessary to illustrate the concept. There is no application logic to distract from the Git mechanics.
- **Beginner-friendly scope** – The conflict involves a single line in a single file, making it easy to understand the conflict markers Git inserts (`<<<<<<<`, `=======`, `>>>>>>>`) without being overwhelmed.

---

## Getting started

### Prerequisites

- [Git](https://git-scm.com/) installed on your machine.

### Clone the repository

```bash
git clone https://github.com/codesburners/mergeconflict.git
cd mergeconflict
```

### Reproduce the merge conflict

1. **Check out `branch1`** and inspect the change:
   ```bash
   git checkout branch1
   cat test.txt
   # city:Bengaluru
   ```

2. **Check out `branch2`** and inspect the conflicting change:
   ```bash
   git checkout branch2
   cat test.txt
   # city:Chennai
   ```

3. **Start a fresh merge** to see the conflict in action:
   ```bash
   git checkout branch1
   git merge branch2
   # CONFLICT (content): Merge conflict in test.txt
   cat test.txt
   ```

   Git will insert conflict markers showing both versions:
   ```
   <<<<<<< HEAD
   city:Bengaluru
   =======
   city:Chennai
   >>>>>>> branch2
   ```

4. **Resolve the conflict** by editing `test.txt` to keep the version you want, then:
   ```bash
   git add test.txt
   git commit -m "Resolve merge conflict"
   ```

---

## Repository structure

```
mergeconflict/
└── test.txt   # The file used to demonstrate merge conflicts
```

---

## Contributing

This repository is primarily educational. If you have ideas for additional conflict scenarios (e.g., conflicts across multiple files, binary files, or rename conflicts) feel free to open an issue or a pull request.

---

## License

This project is open source and available under the [MIT License](LICENSE).
