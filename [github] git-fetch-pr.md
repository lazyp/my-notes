##### 第一步：Fetch the reference to the pull request based on its ID number, creating a new branch in the process.
> $ git fetch origin pull/#ID/head:BRANCHNAME

##### 第二步: Switch to the new branch that's based on this pull request:

>[master] $ git checkout BRANCHNAME

>详细请看 https://help.github.com/en/articles/checking-out-pull-requests-locally
