# Git Internals

I was learning about some of the ways to inspect the inner working of Git. Things like logs and hashes, which might not be too useful for the most part, but it might come in handy when debugging or understanding how Git works under the hood.

## Git Objects

Git stores data in the form of objects. These objects are stored in the `.git/objects` directory of your repository. There are four types of objects in Git:

1. **Blob**: Represents the contents of a file.
2. **Tree**: Represents a directory.
3. **Commit**: Represents a commit.
4. **Tag**: Represents a tag.

## Git Hashes

Each object is stored in a separate file within the `.git/objects` directory. The file name is the SHA-1 hash of the object's contents, the author, the commit message, and the parent commit(s). This makes it so that hashes will basically always be unique.

## Git Log

The `git log` command displays the commit history of a repository. It shows the commit hash, author, date, and commit message for each commit. Some useful options for `git log` include:

- `--oneline`: Displays each commit on a single line.
- `-n`: Limits the number of commits displayed.
- `--graph`: Displays a text-based graph of the commit history.

## Git Cat-File

The `git cat-file` command is used to view the contents of a Git object. You can view the contents of a commit, tree, or blob, which will all show different information depending on the object type. You can use `git cat-file` as follows:

`git cat-file -p <hash>`

Here are some examples of what you will see for each type of object:

### Commit

```plaintext
tree 5b21d4f16a4b07a6cde5a3242187f6a5a68b060f
author Nicolas Araujo <email@google.com> 1738469186 -0800
committer Nicolas Araujo <email@google.com> 1738469186 -0800

A: add contents.md
```

The commit object shows the tree hash, author, committer, timestamp, and commit message.

### Tree

```plaintext
100644 blob ef7e93fc61a91deecaa551c4707e4c3049af42c9	contents.md
```

The tree object shows the file mode, type, hash, and file name for each file in the tree.

### Blob

```plaintext
# contents
```

The blob object shows the contents of the file.
