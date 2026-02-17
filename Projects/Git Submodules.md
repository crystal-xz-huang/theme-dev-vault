Submodules allow you to keep a Git repository as a subdirectory of another Git repository. This lets you clone another repository into your project and keep your commits separate.

- Changes inside the submodule are committed in the submodule repo.
- The parent repo only commits (a) `.gitmodules` changes and/or (b) an updated submodule pointer (the gitlink commit hash), plus any other parent files.

### Introduction to Git submodules

A submodule in Git is essentially a record within a parent repository that points to a **specific commit** in another repository, rather than a branch, a ref, or any other symbolic reference.

This setup allows you to track external repositories within your project. When someone clones your repository, the submodules are not automatically cloned; instead, specific steps need to be followed to initialise and update the submodules.

### Core concept

**Submodules are tracked by the exact _commit_ specified in the parent project, not a branch, a ref, or any other symbolic reference.**

They are _never_ automatically updated when the repository specified by the submodule is updated, only when the parent project itself is updated.

> When you make changes and commit in that \[submodule\] subdirectory, the parent project notices that the HEAD there has changed and records the exact commit you’re currently working off of; that way, when others clone this project, they can re-create the environment exactly.

Or in other words:

> [...] git submodules [...] are static. Very static. You are tracking specific commits with git submodules - not branches, not references, a single commit. If you add commits to a submodule, the parent project won't know. If you have a bunch of forks of a module, git submodules don't care. You have one remote repository, and you point to a single commit. Until you update the parent project, nothing changes.


### Adding a submodule to your project

The `git submodule add` command  is used to add a new submodule to an existing repository.

```shell
git submodule add <REMOTE_URL>

# add a repository on GitHub to our repository as a submodule
git submodule add https://github.com/USERNAME/REPOSITORY-NAME  # HTTPS remote
git submodule add git@github.com:OWNER/REPOSITORY.git          # SSH remote
```

The `git submodule add` command takes a URL parameter that points to a git repository.

By default, Git will clone the subproject into a directory named the same as the remote repository. However, you can add a path at the end of the command to rename the submodule:

```shell
git submodule add <REPOSITORY_URL> <NEW_DIRECTORY_NAME>
```

> [!example]
> 
> ```shell
> git submodule add <https://github.com/example/lib.git> external/lib
> ```
> 
> This command clones the `lib` repository into the `external/lib` directory of your project and adds a new entry in a special file named `.gitmodules`, which tracks your submodules.

> [!example]- Tutorial
> Suppose we have a Git repository called `git-submodule-demo`. This is the superproject; we won't actually add the submodules yet.
> 
> ```shell
> $ mkdir git-submodule-demo
> $ cd git-submodule-demo/
> $ git init
> Initialized empty Git repository in /Users/git-submodule-demo/.git/
> ```
> 
> Next, we will add a submodule to this repo using the `git submodule add` command followed by the repository URL and the path where you want the submodule to reside within your project.
>  
> ```
> $ git submodule add https://github.com/username/subrepo.git
> Cloning into 'subrepo'...
> remote: Counting objects: 8, done.
> remote: Compressing objects: 100% (6/6), done.
> remote: Total 8 (delta 1), reused 0 (delta 0)
> Unpacking objects: 100% (8/8), done.
> ```
> 
> The `git submodule add` command does a couple of things:
> 
> - It clones the submodule under the current directory and by default checks out the master branch.
> - It adds the submodule's clone path to the `.gitmodules` file and adds this file to the index, ready to be committed.
> - It adds the submodule's current commit ID to the index, ready to be committed.
> 
> Here we have added the `subrepo` as a submodule. Git will immediately clone the submodule. We can now review the current state of the repository using `git status`...
> 
> ```
> $ git status
> On branch main
> 
> No commits yet
> 
> Changes to be committed:
>   (use "git rm --cached <file>..." to unstage)
> 
>  new file:   .gitmodules
>  new file:   subrepo
> ```
> 
> There are now two new files in the repository `.gitmodules` and the `subrepo` directory.  Add these files to the the staging index:
> 
> ```
> $ git add .gitmodules subrepo/
> $ git commit -m "added submodule"
> ```
> 
> When you commit, you see something like this:
> 
> ```console
> $ git commit -am 'Add subrepo module'
> [main fb9093c] Add subrepo module
>  2 files changed, 4 insertions(+)
>  create mode 100644 .gitmodules
>  create mode 160000 subrepo
> ```
> 
> Notice the `160000` mode for the `subrepo` entry. That is a special mode in Git that basically means you’re recording a commit as a directory entry rather than a subdirectory or a file.
> 
> Lastly, push these changes:
> 
> ```console
> $ git push origin main
> ```

### .gitmodules

The `.gitmodules` file is a way Git tracks its submodules. It stores the mapping between the project’s URL and the local subdirectory you’ve pulled into:

```
[submodule "subrepo"]
  path = subrepo
  url = https://github.com/username/subrepo
```

If you have multiple submodules, you’ll have multiple entries in this file. It’s important to note that this `.gitsubmodules` file is **version-controlled** with your other files, like your `.gitignore` file. It’s pushed and pulled with the rest of your project. This is how other people who clone this project know where to get the submodule projects from.

> [!NOTE]-
> **Note:** Since the URL in the `.gitmodules` file is what other people will first try to clone/fetch from, make sure to use a URL that they can access if possible. For example, if you use a different URL to push to than others would to pull from, use the one that others have access to. You can overwrite this value locally with `git config submodule.<repo>.url PRIVATE_URL` for your own use. When applicable, a relative URL can be helpful.

> [!aside]-
> The other listing in the `git status` output is the project folder entry. If you run `git diff` on that, you see something interesting:
> 
> ``` 
> $ git diff "subrepo"
> diff --git a/subrepo b/subrepo
> --- a/subrepo      
> +++ b/subrepo      
> @@ -0,0 +1 @@
> +Subproject commit d028de33930a8d2d744c788c5f7aeb1d27a8723f
> ```
> 
> Although `subrepo` is a subdirectory in your working directory, Git sees it as a submodule and doesn’t track its contents when you’re not in that directory. Instead, Git sees it as a particular **commit** from that repository.
> 
> If you want a little nicer diff output, you can pass the `--submodule` option to `git diff`.
> 
> ```
> $ git diff --submodule "subrepo"
> ```
> 

### Cloning a repository with submodules

When you clone a repository that contains submodules using `git clone`, Git doesn't automatically fetch the submodule content. Instead, the submodules directories are empty.

There are two methods for populating the empty submodule directories under the parent repository.

**Method 1:** To clone a repository and automatically initialize and update its submodules, add the `--recurse-submodules` option to the `git clone` command. 

```shell
git clone --recurse-submodules /url/to/repo/with/submodules
```

This will automatically initialise and update each submodule in the repository, including nested submodules if any of the submodules in the repository have submodules themselves.

**Method 2:** If you've already cloned a repository and forgot  `--recurse-submodules`, you can initialize and update them with:

```shell
# git clone /url/to/repo/with/submodules
git submodule update --init --recursive
```

This will initialize your repository with the latest version of the submodules, allowing you to compile and build, leveraging these dependencies.

> [!NOTE]-
> The `git submodule update --init --recursive` command runs two important commands under the hood:
> 
> ```shell 
> git clone /url/to/repo/with/submodules
> git submodule init
> git submodule update
> ```
> 
> - `git submodule init` to copy the mapping from the `.gitmodules` file into the local `./.git/config` file, and
> 
> - `git submodule update` to fetch all the data from that project and check out the appropriate commit listed in your parent repository.
> 
> One major difference between "submodule update" and "submodule add" is that "update" checks out a specific commit, rather than the tip of a branch. It's like checking out a tag: the head is detached, so you're not working on a branch.

### Submodule workflows

Once submodules are properly initialised and updated within a parent repository, they function exactly like stand-alone repositories. 

- **Updating submodules**: To update a submodule to the latest commit on its tracked branch, use `git submodule update --remote`. This command fetches the latest changes in the submodules' remote repositories and updates your local submodule to point to the latest commit.

- **Adding Changes to a Submodule**: If you make changes within a submodule, you'll need to commit those changes within the submodule's directory and then commit the updated submodule reference in the parent repository, as the submodule tracks its history independent of the parent project.


> [!example]
> 1. **Commit changes to the submodule:** If you want to make a change within a submodule, you should first check out a branch, make your changes, publish the change within the submodule, and then update the superproject to reference the new commit.
> 
> ```shell
> cd /path/to/submodule
> 
> git checkout experimentalv0
> echo "adding a new line to submodule" >> a.txt
> 
> git add -A # (or git add -all) stages all changes in the entire repository
> git commit -m "Updated the submodule from within the superproject."
> git push
> ```
> 
> 
> 2. **Update the parent repo to record the new submodule commit:** When you update a submodule, the parent repository notices the change to the submodule's commit pointer. To include this update in your project, add and commit the change in the parent repository:
> 
> ```shell
> cd /path/to/your/parent/repo
> 
> git add submodule   # There is a gotcha here.  Read about it below.
> git commit -m "Update submodule to latest version"
> ```
> 
> This process ensures that other developers working on your project can sync their submodules to the same commit.

## Gotchas 

If you use a forward slash (/) after the submodule name when adding changes to a submodule and updating the container repository to use the latest submodule changes that you have pulled from the remote source:

```
$ git add submodule/
```

git will think you want to delete the submodule and want to add all the files in the submodule directory. Please DONT use a forward slash after the submodule name. You must type it like this:

```
$ git add submodule
```

Always publish the submodule change *before* publishing the change to the superproject that references it. If you forget to publish the submodule change, others won't be able to clone the repository:

```
$ cd /path/to/submodule
$ echo i added another line to this file >> a.txt
$ git commit -a -m "doing it wrong this time"
$ cd ..
$ git add a
$ git commit -m "Updated submodule a again."
$ git push
```

In a cloned repository of the parent project ...

```
$ cd /path/to/cloned/parent/repo
$ git pull
$ git submodule update
error: pathspec '261dfac35cb99d380eb966e102c1197139f7fa24' did not match any file(s) known to git.
Did you forget to 'git add'?
Unable to checkout '261dfac35cb99d380eb966e102c1197139f7fa24' in submodule path 'a'
```

### Removing submodules

> [!summary]
> 1. Delete the relevant line from the `.gitmodules` file.
> 2. Delete the relevant section from `.git/config`.
> 3. Run `git rm --cached path_to_submodule` (no trailing slash).
> 4. Commit and delete the now untracked submodule files.


1. **Remove the submodule’s entry in the `.gitmodules` file.** If there is only one submodule, you can simply remove the file entirely by running `git rm .gitmodules`. Otherwise, open the `.gitmodules` file and remove the three lines relevant to the submodule being removed:

```
[submodule "repo-to-remove"]
	path = repo-to-remove
	url = https://github.com/username/repo-to-remove
```

2. **Remove the submodule’s entry in the `.git/config.`** This step isn’t strictly necessary, but it does keep your config file tidy and will help prevent problems in the future. The submodule’s entry in .git/config will only be present if you’ve run `git submodule init`on the repository. If you haven’t, you can skip this step. In this example, the following lines will be removed:

```
[submodule "repo-to-remove"]
	url = https://github.com/username/repo-to-remove
```


3. **Remove the path created for the submodule.** Simply run `git rm --cached [/path/to/submodule]`.

```
git rm --cached <repo-to-remove>
```


### Listing submodules

```shell
git submodule status
```

Use `git config --file .gitmodules --name-only --get-regexp path$` to list all submodules in your project.

```shell
git config --file .gitmodules --name-only --get-regexp path$
```


