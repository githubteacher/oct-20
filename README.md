# GitHub for Developers

- October 10-21, 2016
- Facilitators:
  - Briana Swift (@brianamarie)
  - Cynthia Rich (@crichID)

## Resources

- [GitHub for Developers Manual](manual/github-for-developers-student-manual.pdf)
- [git-scm](https://git-scm.com)
 
## Scripts for Adding Files

- **Bash:** `for d in {1..6}; do touch file$d.md; git add file$d.md; git commit -m "adding file $d"; done`
- **PowerShell:** `for ($d=1; $d -le 6;$d++) { touch file$d.md; git add file$d.md; git commit -m "adding file$d.md";}`

## Playgrounds for practicing branching
- [LearnGitBranching](http://learngitbranching.js.org/?NODEMO)
- [GitSchool - Visualizing Git](http://git-school.github.io/visualizing-git/)

To show your active Git branch in your command prompt, you will need to do the following:

- If you are on a **Mac**, you can add the code shown below to your `.bash_profile` file.
- If you are on **Linux**, you will add the code shown below to your `.bashrc` file. 
- If you are on **Windows**, you probably aren't reading this because Windows provides this behavior by default.

### The Script

```shell
parse_git_branch() {
  git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/'
}
export PS1="\w\[\033[36m\]\$(parse_git_branch) \[\033[00m\] > "
```

Or, another option:

```shell
function parse_git_branch () {
  git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/'
}
 
RED="\[\033[0;31m\]"
YELLOW="\[\033[0;33m\]"
GREEN="\[\033[0;32m\]"
NO_COLOR="\[\033[0m\]"
 
PS1="$GREEN\u@\h$NO_COLOR:\w$YELLOW\$(parse_git_branch)$NO_COLOR\$ "
```
