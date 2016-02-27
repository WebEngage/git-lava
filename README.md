# git-lava

We at WebEngage use [git flow](http://nvie.com/posts/a-successful-git-branching-model/) as the branching model for our code repositories and find creating a hotfix manually an error prone and mundane chore

This is how we normally went about
- have all changes ready on the master branch
- look through `git log` to find the version of the (next) hotfix
- start hotfix
- commit changes in the hotfix branch
- finish up hotfix
- push commits to `origin/master` and `origin/develop`
- push the tag to origin

Now `git lava` automates this process for us and even rollbacks the entire operation in case of an error :+1:


### Demo
![Demo](https://github.com/WebEngage/git-lava/blob/master/static/demo.gif)


### Tag prefix
A project may need a 'tag prefix'. Tag prefix starts the names of the hotfix tag and branch

For example, with prefix `shifu` in hotfix version 3.1.4, the change commit is tagged as `shifu-3.1.4` and hotfix branch created as `hotfix/shifu-3.1.4`


### Important prerequisites
If you intend to use `git lava`, first check whether your project meets all these prerequisites
  - project should follow [semantic versioning](http://semver.org/)
  - `git lava` searches `git log` for commit messages like `Merge branch 'hotfix/shifu-7.2.1' into develop` to find the next hotfix version, 
    so you must keep the merge commit messages in the same (default) format
  - release names should also incorporate the tag prefix
    * if the tag prefix is set `shifu`, release branches need to be named like `release/shifu-7.1`
    * and if its omitted (set as `-`), release branches must be like `release/7.1`


### Installation
1. You'll need to have [git-flow](https://github.com/nvie/gitflow) installed first

2. Navigate to a directory in `$PATH` where you have write access and execute
```
curl https://raw.githubusercontent.com/WebEngage/git-lava/master/git-lava > git-lava
```

3. In a git repository, set the 'tag prefix' as decided for that project. If the project doesn't have such a prefix, set it as `-` (a hyphen)
```
git config gitlava.tagprefix <prefix>
```


### Usage
```
git lava [<commit message>]
```

If `<commit message>` is omitted, user is prompted for the message later in `$GIT_EDITOR`

All **unstaged** but tracked changes (except for submodules) are also automatically included in the hotfix. 
Explicitly `git add` submodules and new files  before running `git lava` to include them in the hotfix

### License - [WTFPL](http://www.wtfpl.net/)
```
            DO WHAT THE FUCK YOU WANT TO PUBLIC LICENSE
                    Version 2, December 2004

 Copyright (C) 2015 WebEngage <opensource {at} webengage.com>

 Everyone is permitted to copy and distribute verbatim or modified
 copies of this license document, and changing it is allowed as long
 as the name is changed.

            DO WHAT THE FUCK YOU WANT TO PUBLIC LICENSE
   TERMS AND CONDITIONS FOR COPYING, DISTRIBUTION AND MODIFICATION

  0. You just DO WHAT THE FUCK YOU WANT TO.
```
