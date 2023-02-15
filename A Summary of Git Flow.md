# **Content**

1. [What is GitFlow and getting started](./Intro%20to%20Git%20Flow.md)
2. [`Develop` and `main` branches](./)
3. [`Features` branches](./)
4. [`Release` branches](./)
5. [`Hotfix` branches](./)
6. A summary of GitFlow (_here_)


# **Summary**

Some key takeaways to know about Gitflow are:

1. The workflow is great for a release-based software workflow.
2. Gitflow offers a dedicated channel for hotfixes to production.

The overall flow of Gitflow is:

1. A `develop branch` is created from main

    Here you can use either: 

    ```bash
    git branch develop
    git push -u origin develop
    ```

    Or using the tool (this generates for you the `develop` branch):

    ```bash
    git flow init
    ```

    So, more graphically:

    ```mermaid
    gitGraph
        commit
        branch develop
        commit
    ```
2. A `release` branch is create from `develop`
    
    You can use:

    ```bash
    git checkout develop
    git checkout -b release/0.1.0
    ```

    or using the tool:

    ```
    git flow release start 0.1.0
    ```

    So that results in:

    ```mermaid
    gitGraph
        commit
        branch develop
        commit
        branch release
        commit
    ```

3. `Feature` branches are created from `develop`

    You can use the following:
    ```bash
    git checkout develop
    git checkout -b feature_branch
    ```

    Or using the tool:

    ```bash
    git flow feature start feature_branch
    ```

    That is translated into:

    ```mermaid
    gitGraph
    commit
    branch develop
    commit
    branch feature_branch_01
    commit
    commit
    checkout develop
    branch feature_branch_02
    commit
    commit
    ```
4. When a `feature` is complete, it is merged into the `develop` branch

    You can use:
    ```bash
    git checkout develop
    git merge feature_branch
    ```
    Or using the tool:
    ```bash
    git flow feature finish feature_branch
    ```
    
    This is viewed as:

     ```mermaid
    gitGraph
    commit
    branch develop
    commit
    branch feature_branch_01
    commit
    commit
    checkout develop
    branch feature_branch_02
    commit
    commit
    checkout develop
    merge feature_branch_01
    merge feature_branch_02
    ```

5. When the `release` branch is done it is merged into `develop` and `main`

    You can do this, using:

    ```bash
    git checkout main
    git merge release/0.1.0
    git checkout develop
    git merge release/0.1.0
    ```

    and with the tool:

    ```bash
    git flow release finish '0.1.0'
    ```

    this is:
    
    ```mermaid
    gitGraph
    commit
    branch develop
    commit
    commit
    branch release
    commit
    checkout main
    merge release
    checkout develop
    merge release
    ```

    _Note_: Ensure that the `release` branch is deleted after merging processes.

6. If an issue in `main` is detected a `hotfix` branch is created from main

    You can do this, using:
    
    ```bash
    git checkout main
    git checkout -b hotfix_branch
    ```

    using the tool:

    ```bash
    git flow hotfix start hotfix_branch
    ```
    visually, this is:

    ```mermaid
    gitGraph
    commit
    commit
    branch hotfix_branch
    commit
    commit
    commit
    ```

7. Once the `hotfix` is complete, it is merged to both `develop` and `main`

    Using git basic commands:
    
    ```bash
    git checkout main
    git merge hotfix_branch
    git checkout develop
    git merge hotfix_branch
    git branch -D hotfix_branch
    ```

    now, using the tool:

    ```bash
    git flow hotfix finish hotfix_branch
    ```

    and the graphical result is:

    ```mermaid
    gitGraph
    branch develop
    commit
    checkout main
    commit
    commit
    branch hotfix_branch
    commit
    commit
    commit
    checkout main
    merge hotfix_branch
    checkout develop
    merge hotfix_branch
    ```

    _Note_: Ensure that the `hotfix` branch is deleted after merging processes.
