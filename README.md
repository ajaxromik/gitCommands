# gitCommands

This is a simple list of the useful git commands that I've been using a lot recently.

---

## When the remote branch has a different history due to a forced push

```
git fetch origin
git checkout <bname>
git reset --hard origin/<bname>
```

## Move commit to another branch

If you ever forget to swap branches before committing, use this:

```sh
git reset HEAD~ --soft
git stash
git checkout <correct_branch>
git stash pop
git add .
git commit -m "message"
```

## Recent branches

For whenever you want to look a wide view of your git history, or maybe double check you've pushed everything to GitHub:

```sh
git branch -v --sort=-committerdate
```

OR for a prettier version as long as you're copying or aliasing it:

```sh
git for-each-ref --sort=-committerdate refs/heads/ --format='%(HEAD) %(align:40)%(color:yellow)%(refname:short)%(color:reset)%(end)%(align:20)(%(color:green)%(committerdate:relative)%(color:reset))%(end) - %(contents:subject)'
```

OR finally for the shorter version of that command if you keep a smaller terminal window:
  
```sh
git for-each-ref --sort=-committerdate refs/heads/ --format='%(HEAD) %(align:40)%(color:yellow)%(refname:short)%(color:reset)%(end)(%(color:green)%(committerdate:relative)%(color:reset))'
```

You can also use `git reflog` but personally I find it harder to use.

## New branches

Whenever you open a new branch:

```sh
git checkout -b <bname>
```

## Change commit message

In case you had a typo in your commit command. Beware, you may get an error about separate histories if you do this after already pushing.

```sh
git commit --amend
```

## See diff from previous commit to current

Sometimes it's helpful to remind yourself what was added right before:

```sh
git diff HEAD~1 HEAD
```

---

# GitHub things

I also find this useful a lot, so here is a PR search config that will show you recently updated PRs:
```
is:pr author:<username> archived:false updated:>2025-02-17
```

---

### License
MIT License
