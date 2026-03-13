# mergeconflict

A hands-on educational repository designed to demonstrate Git merge conflicts — how they occur, what they look like, and how to resolve them.

## What is this project?

This repository is a practical learning tool for developers who want to understand Git merge conflicts. Instead of reading abstract documentation, you can explore real branches and pull requests that caused actual conflicts, see exactly what the conflict markers look like, and study how the resolution was applied.

The repository deliberately keeps the code simple (a single `test.txt` file) so that the focus remains entirely on the **merge conflict workflow** rather than the content of the files.

## What makes it unique?

| Feature | This project | Typical tutorials |
|---|---|---|
| Real conflict history | ✅ Preserved in Git log | ❌ Usually explained in text only |
| Explorable branches | ✅ `branch1` and `branch2` are available to checkout | ❌ Readers must set it up themselves |
| Minimal noise | ✅ Single file, no dependencies, no build steps | ❌ Often bundled with unrelated code |
| Immediate hands-on experience | ✅ Clone → inspect → resolve | ❌ Requires significant setup |

Unlike most merge-conflict tutorials that walk you through a hypothetical scenario, **this repo is the scenario** — the conflicting branches and their merge history are baked right into the repository.

## How to use this repository

### 1. Clone the repository

```bash
git clone https://github.com/codesburners/mergeconflict.git
cd mergeconflict
```

### 2. Explore the branches

```bash
git branch -a
```

Two key branches exist:
- **`branch1`** — made an edit to `test.txt`
- **`branch2`** — made a conflicting edit to the same line in `test.txt`

### 3. Reproduce the conflict

```bash
# Start fresh from main
git checkout main

# Create a test branch and merge branch1 first
git checkout -b test-merge
git merge origin/branch1   # merges cleanly

# Now try to merge branch2 — this will conflict!
git merge origin/branch2
```

Git will report a conflict. Open `test.txt` and you will see conflict markers like:

```
<<<<<<< HEAD
city:Mumbai
=======
city:Bengaluru
>>>>>>> origin/branch2
```

### 4. Resolve the conflict

Edit `test.txt` to keep the version you want, remove the conflict markers, then:

```bash
git add test.txt
git commit -m "Resolve merge conflict"
```

## Key concepts demonstrated

- **Merge conflict** — occurs when two branches edit the same part of the same file and Git cannot automatically decide which change to keep.
- **Conflict markers** — `<<<<<<<`, `=======`, and `>>>>>>>` are inserted by Git to highlight the competing changes.
- **Manual resolution** — a developer must review the conflicting sections, decide on the final content, and complete the merge with a commit.

## Repository structure

```
mergeconflict/
└── test.txt   # Simple file used to demonstrate the merge conflict
```

## Contributing

Feel free to open issues or pull requests if you want to add more conflict scenarios or improve the documentation.
