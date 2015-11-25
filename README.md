# git-lava

If your project enforces [git-flow](https://github.com/nvie/gitflow) as the branching model and right now you are frustated out of your mind having to manually create hotfixes every now and then - git-lava is for you.

git-lava will create a hotfix painlessly without any user interaction and have it pushed to origin.

### Installation
For now you need to download the git-lava shell script from [here](https://raw.githubusercontent.com/WebEngage/git-lava/master/git-lava) and place in one of the `$PATH` directories (we are working on an easier installation method).

After that set a 'tag prefix' that becomes part of the hotfix tag and branch name.

```git config gitlava.tagprefix <prefix>```

Say for prefix 'shifu' and hotfix version 3.1.4
  - change commit is tagged as 'shifu-3.1.4'
  - hotfix branch is created as 'hotfix/shifu-3.1.4'

If your project doesn't have such prefixes, set it as `-` (a hyphen)
### Usage
```git lava [<commit message>]```

If commit message is omitted at the command line, user is prompted for the message later in `$GIT_EDITOR`

### Important
git-lava is only suitable for projects that follow the semantic versioning scheme.

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
