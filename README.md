# lts-driven-git-submodules
This provide specification for using `git submodule` &amp; branching for simplified/naive package system.

You can use your git repository as submodule inside another one. One reason for that is using development approach specified by this document.

## Motivation
You have combination of these problems:
1. internal library
2. library with minimal/small/no so big need for updating ~ technically done, just support
3. no (stable) developer team for given library

`git submodule`s give you:
1. way to provide such library
2. update library is just `git pull`
3. developer using library has ability to create fix/change from inside his/her repository as a new PR request
4. ↘this have to be tested (as „non LTS” version) in project where the library is used
5. ↘it can make PR aproving quicker

## Specification (version *LTS+sub-branches*)
To allow library be used as submodule and make library „working”/sustainable you should follow:
1. There are reserved LTS (long term support) branches
    1. default branch (*main*/*master*) = the latest version
    1. branch with prefix **lts_**: lts_a, …, lts_z, lts_aa, …
1. When change is needed (user):
    1. try existing non-lts branch for your lts branch
    1. or
        1. create new branch with patternt **source-unique** (*source*= name of the lts branch, *unique*= not used identificator to prevent colision)
        1. create Pull Request
    1. **automatically non-lts** ⇒ hast to be considered when testing parent library/app
    1. commits
1. When there are PRs:
    1. Contact coleagues about tests
    1. Additional testing - reimplementation (prefering **backward support**)
    1. Submit PR + delete branch

## Label (version *LTS+sub-branches*)
For make statement that repo follows these instruction use:
```markdown
[![LTS+sub-branches](https://img.shields.io/badge/submodule-LTS+sub--branches-informational?style=flat-square&logo=git)](https://github.com/IndigoMultimediaTeam/lts-driven-git-submodules)
```
in your `README.md` → [![LTS+sub-branches](https://img.shields.io/badge/submodule-LTS+sub--branches-informational?style=flat-square&logo=git)](https://github.com/IndigoMultimediaTeam/lts-driven-git-submodules)
