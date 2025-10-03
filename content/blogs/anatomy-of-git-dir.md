---
date: '2025-10-03' 
darft: false 
title: Anatomy of .git/ directory
author: hrabid
image: /blogs/git-logo.png 
---
## `.git/COMMIT_EDITMSG`
A temporary git commit file that holds the commit message of last commit. 
- If we use `git commit` command  (without the `m` flag), it will store what we see in our editor while commiting any changes.  If it's not (using `git commit -m "commit message"`),  it will store only the commit message. 
- This file never leaves the local machine & remote doesn't know this file
- 
## `.git/config`
#git_core_files
Text based local/project specific configuration file in  the root of `.git` directory. 

### Sections: 
#### `[core]`
Basic repo settings: 

- `repositoryformatversion = 0`
- `filemode = true`
- `bare = false`
- `logallrefupdates = true`

#### `[user]`
User specific data like:
- `name = abid`
- `email = hrabid@outlook.com` 
#### `[remote]`
Details about remote repo including:
- Remote name: `[remote "origin"]`
- URL : `url = git@github.com:hrabid/dotfiles.git`
- Fetch Configuration: `fetch = +refs/heads/*:refs/remotes/origin/*` 

#### `[pull]`
Configuration for pull
- `rebase = true`
- `ff = only`

#### `[branch]`
- Branch Name: `[branch " main"]`
- remote info : `remote = origin`
- Merge info : `merge = refs/heads/main`

## `.git/description`
Description of the repo.
> [!note]
> `.git/description` is not used by `git` itself, rather it is used by the web feontends like `GitWeb`, `cgit` etc.

By default the repository show this message 
```
Unnamed repository; edit this file 'description' to name the repository.
```
But it can be edited. 

## `.git/FETCH_HEAD`


## `.git/HEAD`

The `HEAD` file indicates to current Branch or commit. 
It Contains a : 
- Reference `ref:refs/heads/branchname`
![[Pasted image 20250413111011.png]]

- A direct commit hash, if in a detached HEAD state (Checking out a specific commit)
 the `HEAD` file is updated with `git switch` or `git checkout` or `git branch -M` commit. 

## `.git/hooks/`

## `.git/index`

## .git/info/`

## `.git/logs/`
## .git/objects/`
### Content-Addressed Storage(CAs)

In traditional Data Storage System files are rely on Hierarchical file system or location based Addresses. 

In Content-Addressed Storage or CAS Data is Addressed based on their Contents rather than the location. 
- Every data is assigned a unique identifier (in this case a SHA-1 Hash __ Basically a 40-character hexadecimal storage)
- The Hash Value is derived from the contents of the file means any altercation in content changes the hash Value( the unique identifier)

### Facilities of CAS
#### Data Integrity & Security 
Since the Hash value or unique identifier is derived from the Contents of the data or file, any altercation or changes are easily detected. 

#### Efficient Retrieval
No Complex file path needed, just referring to the unique identifier or hash value is enough for data retrieval.

### Use Case 
- Achieving data backup in CDNs
- In Git for storing objects.


## `.git/packed-refs`

## `.git/refs/`

## `.git/tag/`

