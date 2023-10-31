### Installing and configuring P4Merge for Git on Ubuntu

```sh
cd ~/Downloads
```

```sh
wget https://cdist2.perforce.com/perforce/r19.1/bin.linux26x86_64/p4v.tgz
```

```sh
tar zxvf p4v.tgz
```
```sh
sudo mkdir /opt/p4v
```

```sh
cd p4v-2019.1.1865170
```
```sh
sudo mv * /opt/p4v
```
```sh
sudo ln -s /opt/p4v/bin/p4merge /usr/local/bin/p4merge
```
```sh
sudo nano ~/.gitconfig
```
Add the following if you only want to use p4merge as a diff tool

```git
[diff]
    tool = p4merge
[difftool]
    prompt = false
[difftool "p4merge"]
    cmd = p4merge "$LOCAL" "$REMOTE"
    keepTemporaries = false
    trustExitCode = false
    keepBackup = false
```
Add the following if you also  want to use p4merge as a merge tool

```git
[merge]
    keepBackup = false;
    tool = p4merge
[mergetool]
    prompt = false
[mergetool "p4merge"]
    cmd = p4merge "$BASE" "$LOCAL" "$REMOTE" "$MERGED"
    keepTemporaries = false
    trustExitCode = false
    keepBackup = false
```

Enjoy

```sh
git difftool branchOne/pathToFile/file.ts branchTwo/pathToFile/file.ts
```

#### Notes
* https://git-scm.com/docs/git-diff
* https://www.perforce.com/products/helix-core-apps/merge-diff-tool-p4merge