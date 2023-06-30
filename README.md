# SubmoduleGitTest
Testing git submodule functionality

Workflow including git submodules:

If code changes are done entirely on machineB (editing submodule), machineA (mainProject) only has to do
``git submodule foreach git pull``. When submodule changes are ready for staging (on machineA), run
``git submodule summary`` and copy-paste changes in submodule as commit message in mainProject history.


## Cloning repo with submodules
Option 1:

``git clone --recurse-submodules <mainProjectURL>``

Option 2 (if forget '--recurse-submodules'):

``git clone <mainProjectURL>``

``cd <mainProject>``

``ls -la`` -> empty directory

``git submodule init``

``git submodule update``

## Updating submodule

Option 1:

``cd <submodule>``
``git pull``
``cd ..``
``git add -A``
``git commit``
``git push``

Option 2:

``cd <submodule>``
``git fetch``
``git merge``

Option 4:

``git submodule foreach git pull origin master``

## Running submodule command in loop

``git submodule foreach git pull``

## Aliases for submodules

alias gds='git diff --submodule'
alias gss='git submodule summary'

## Removing submodule from mainProject

* Delete the relevant section from the .gitmodules file.
* Stage the .gitmodules changes git add .gitmodules
* Delete the relevant section from .git/config.
* Run git rm --cached path_to_submodule (no trailing slash).
* Run rm -rf .git/modules/path_to_submodule (no trailing slash).
* Commit git commit -m "Removed submodule "
* Delete the now untracked submodule files rm -rf path_to_submodule

## Setting Personal Access Token when using HTTPS (prefer SSH)

While cloning:

``git clone https://<username>:<githubtoken>@github.com/<username>/<repositoryname>.git``

After cloning:

``git remote set-url origin https://<githubtoken>@github.com/<username>/<repositoryname>.git``
