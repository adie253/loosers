GITHUB FOR BEGINNERS

A simple, practical guide to Git and GitHub With commands, examples, and
common problems

============================================================ 1. WHAT ARE
GIT AND GITHUB?
============================================================

Git: Git is a version-control system. It keeps a history of changes in
your project.

Think of Git like SAVE POINTS in a game.

Example: You build a website today. Tomorrow you change 20 files and
accidentally break everything. With Git, you can go back to an earlier
working version.

GitHub: GitHub is a website where Git repositories can be stored online.

Simple difference:

Git = tool on your computer GitHub = online place where your Git project
can be stored

You can use Git without GitHub. You can use GitHub with Git.

Common workflow:

Your computer | | git push v GitHub | | git clone / git pull v Another
computer

============================================================ 2.
IMPORTANT WORDS YOU MUST KNOW
============================================================

Repository (repo): A project tracked by Git.

Example: my-ecommerce-backend/

Working directory: The actual files you are currently editing.

Commit: A saved checkpoint in Git.

Branch: A separate line of development.

Remote: A connection between your local repository and an online
repository.

Origin: The usual default name given to your main remote repository.

Clone: Download a GitHub repository to your computer.

Push: Send your local commits to GitHub.

Pull: Get changes from GitHub and integrate them into your local branch.

Fetch: Download information about remote changes without integrating
them.

Merge: Combine changes from one branch into another.

Pull Request (PR): A request to merge your changes into another branch,
usually on GitHub.

HEAD: The commit/branch you are currently working from.

Staging area: The place where you select changes that will go into your
next commit.

============================================================ 3. INSTALL
GIT ============================================================

Download Git from the official Git website.

After installation, open Command Prompt, PowerShell, Git Bash, or the VS
Code terminal.

Check installation:

    git --version

Example output:

    git version 2.x.x

If you see a version, Git is installed.

============================================================ 4.
CONFIGURE GIT FOR THE FIRST TIME
============================================================

Tell Git your name:

    git config --global user.name "Your Name"

Tell Git your email:

    git config --global user.email "you@example.com"

Check your settings:

    git config --global --list

Example:

    git config --global user.name "Aditya"
    git config --global user.email "aditya@example.com"

IMPORTANT: The name and email are attached to your commits.

If you want your GitHub contributions to be associated with your GitHub
account, use an email address that GitHub recognizes for your account.

============================================================ 5. CREATE A
GITHUB ACCOUNT
============================================================

Go to GitHub and create an account.

After logging in, you can create repositories, upload code, collaborate
with other developers, review pull requests, manage issues, and more.

============================================================ 6. CREATE
YOUR FIRST GITHUB REPOSITORY
============================================================

On GitHub:

1.  Click the “+” button.
2.  Select “New repository”.
3.  Enter a repository name.

Example:

    ecommerce-backend

4.  Add an optional description.

Example:

    E-commerce backend built with Java and Spring Boot.

5.  Choose Public or Private.

Public: Anyone can see the repository.

Private: Only people you give access to can see it.

6.  You can add a README.
7.  You can add a .gitignore.
8.  Create the repository.

============================================================ 7. WHAT IS
A README? ============================================================

README.md is normally the first document people see in your repository.

It should explain your project.

Example:

    # E-commerce Backend

    Backend API for an e-commerce application.

    ## Technologies

    - Java
    - Spring Boot
    - PostgreSQL
    - JPA/Hibernate

    ## How to run

    1. Clone the repository.
    2. Configure the database.
    3. Run the application.

README files use Markdown.

Common Markdown:

    # Main heading
    ## Smaller heading
    **bold**
    *italic*

Code:

    ```java
    System.out.println("Hello");
    ```

============================================================ 8. WHAT IS
.gitignore? ============================================================

.gitignore tells Git which files/folders it should NOT track.

This is extremely important.

For a Java/Spring Boot project, you normally don’t want to commit:

-   compiled files
-   IDE files
-   build folders
-   local environment files
-   secrets
-   logs

Example:

    target/
    .idea/
    *.class
    .env

A .gitignore file can prevent accidental uploads of unnecessary or
sensitive files.

IMPORTANT: Do NOT put passwords, API keys, database credentials, private
keys, or other secrets into GitHub.

============================================================ 9. CREATE A
LOCAL GIT REPOSITORY
============================================================

Suppose you have:

    ecommerce-backend/

Open that folder in the terminal:

    cd ecommerce-backend

Initialize Git:

    git init

Now Git starts tracking the project.

Check status:

    git status

============================================================ 10. YOUR
FIRST COMMIT
============================================================

Git normally follows this process:

Files | v Working directory | | git add v Staging area | | git commit v
Local Git history | | git push v GitHub

Step 1: Check what changed:

    git status

Step 2: Add files to staging:

    git add .

The “.” means all changes in the current directory.

You can also add one file:

    git add README.md

Step 3: Create a commit:

    git commit -m "Initial commit"

The message should explain what the commit does.

============================================================ 11. CONNECT
YOUR LOCAL PROJECT TO GITHUB
============================================================

If you already created an empty GitHub repository, copy its repository
URL.

Example:

    https://github.com/USERNAME/ecommerce-backend.git

Add it as a remote:

    git remote add origin https://github.com/USERNAME/ecommerce-backend.git

Check it:

    git remote -v

You should see the GitHub repository URL.

============================================================ 12. PUSH
YOUR PROJECT TO GITHUB
============================================================

Rename your current branch to main:

    git branch -M main

Push:

    git push -u origin main

The “-u” connects your local main branch with the remote main branch.

After the first push, you can usually simply use:

    git push

============================================================ 13. THE
BASIC DAILY WORKFLOW
============================================================

Most days, you will do something like this:

1.  Get the latest code:

    git pull

2.  Make your changes.

Example: You create a new Product API.

3.  Check your changes:

    git status

4.  Review the changes:

    git diff

5.  Stage them:

    git add .

6.  Commit:

    git commit -m “Add product API”

7.  Push:

    git push

Simple version:

    git pull
    [write code]
    git add .
    git commit -m "Describe change"
    git push

============================================================ 14. git
status ============================================================

Command:

    git status

This is one of the most useful Git commands.

It tells you:

-   Which branch you are on
-   Which files changed
-   Which files are staged
-   Which files are untracked

Example:

    modified: src/Product.java
    untracked: src/ProductController.java

Meaning:

Product.java was changed. ProductController.java is a new file Git does
not track yet.

============================================================ 15. git add
============================================================

Add one file:

    git add Product.java

Add several files:

    git add Product.java ProductController.java

Add everything:

    git add .

Remove a file from staging without deleting it:

    git restore --staged Product.java

============================================================ 16. git
commit ============================================================

A commit is a checkpoint.

Example:

    git commit -m "Add product entity"

Good commit messages:

    Add login API
    Fix product validation
    Add order service
    Update README
    Fix authentication bug

Avoid messages like:

    changes
    update
    done
    final
    test

============================================================ 17. git log
============================================================

See commit history:

    git log

A shorter version:

    git log --oneline

Example:

    a82f123 Add product API
    31b9e20 Add database configuration
    8f1d2aa Initial commit

Each commit has a unique ID called a commit hash.

============================================================ 18. git
diff ============================================================

See changes that have NOT been staged:

    git diff

See staged changes:

    git diff --staged

This is useful before committing.

============================================================ 19. git
push ============================================================

Push local commits to GitHub:

    git push

Or:

    git push origin main

Push another branch:

    git push -u origin feature/product-api

============================================================ 20. git
pull ============================================================

Get the latest changes from GitHub:

    git pull

Think:

GitHub has new code | v git pull | v Your computer gets the changes

============================================================ 21. git
fetch ============================================================

Fetch downloads information about remote changes but does not
automatically merge them into your current branch.

    git fetch

This is useful when you want to inspect what changed before integrating
it.

A common difference:

    git fetch
    = download remote information

    git pull
    = fetch + integrate changes

============================================================ 22. CLONING
A REPOSITORY
============================================================

If a project already exists on GitHub, use clone.

Example:

    git clone https://github.com/USERNAME/ecommerce-backend.git

Then:

    cd ecommerce-backend

Open in VS Code:

    code .

Now you have a local copy of the repository.

============================================================ 23.
CONNECTING GITHUB TO VS CODE
============================================================

Method 1: Clone from VS Code

1.  Open VS Code.
2.  Press Ctrl + Shift + P.
3.  Search “Git: Clone”.
4.  Enter/select the GitHub repository.
5.  Choose a local folder.
6.  Open the cloned project.

Method 2: Use terminal:

    git clone https://github.com/USERNAME/ecommerce-backend.git
    cd ecommerce-backend
    code .

VS Code has built-in Git support, so you can use the Source Control
panel without typing every command.

============================================================ 24. VS CODE
SOURCE CONTROL
============================================================

In VS Code, open the Source Control panel.

You can see:

-   Changed files
-   Staged files
-   Untracked files

You can stage files using the “+” button.

You can write a commit message.

Then click Commit.

After committing, use Sync/Push to send the commit to GitHub.

It is still useful to understand the terminal commands because real
development teams often use both VS Code UI and Git commands.

============================================================ 25.
BRANCHES ============================================================

A branch lets you work on a feature without directly changing the main
branch.

Imagine:

    main
     |
     |------ project
     |
     +---- feature/login
     |
     +---- feature/products

The main branch should normally contain stable code.

Create a branch:

    git branch feature/login

Switch to it:

    git switch feature/login

Create and switch in one command:

    git switch -c feature/login

Older Git versions also commonly use:

    git checkout -b feature/login

============================================================ 26. WHY USE
BRANCHES? ============================================================

Suppose the main project works perfectly.

You want to build login.

Instead of doing this directly on main:

    main
     |
     +-- login code
     +-- broken code
     +-- unfinished code

Create:

    feature/login

Now:

    main ---------------- stable
          \
           feature/login --- your work

When the feature is complete and reviewed, merge it.

============================================================ 27. SEE
YOUR BRANCH ============================================================

List branches:

    git branch

The current branch usually has an asterisk.

Example:

    * feature/login
      main

Switch branches:

    git switch main

Switch back:

    git switch feature/login

============================================================ 28. MERGING
============================================================

Suppose you finished your login feature.

First switch to main:

    git switch main

Get the latest main:

    git pull

Merge your feature:

    git merge feature/login

Now the feature is integrated into main.

Then push:

    git push

============================================================ 29. PULL
REQUESTS ============================================================

In professional development, you often DON’T merge your branch directly
into main.

Instead:

1.  Create a feature branch.
2.  Write your code.
3.  Commit.
4.  Push the branch to GitHub.
5.  Open a Pull Request.
6.  Team members review the code.
7.  Fix requested changes.
8.  PR gets approved.
9.  PR is merged.

Example:

    main
      |
      +---- feature/product-api

Push:

    git push -u origin feature/product-api

Then GitHub can show:

    feature/product-api -> main

This is a Pull Request.

============================================================ 30. WHAT IS
A PULL REQUEST?
============================================================

A Pull Request is basically saying:

“I wrote this code. Please review it and merge it into the main
project.”

A PR can contain:

-   Description
-   Changed files
-   Comments
-   Review requests
-   Automated tests
-   Approvals
-   Checks

PRs are one of the most important parts of team development.

============================================================ 31. CODE
REVIEW ============================================================

During a code review, teammates may check:

-   Is the code correct?
-   Is it readable?
-   Are there security problems?
-   Are tests included?
-   Is the architecture reasonable?
-   Are unnecessary changes included?

A reviewer may write:

    "Please add validation for the email field."

You make the change, commit it, and push again.

The PR automatically updates.

============================================================ 32. MERGE
CONFLICTS ============================================================

A conflict happens when Git cannot automatically decide which change
should win.

Example:

Developer A changes:

    String name = "Aditya";

Developer B changes the same line to:

    String name = "Rahul";

Git may report a conflict.

You might see:

    <<<<<<< HEAD
    String name = "Aditya";
    =======
    String name = "Rahul";
    >>>>>>> feature/name-change

You must decide what the final code should be.

For example:

    String name = "Aditya";

Then remove the conflict markers.

After fixing:

    git add .
    git commit -m "Resolve merge conflict"

============================================================ 33. HOW TO
AVOID CONFLICTS
============================================================

You cannot eliminate conflicts completely, but you can reduce them.

Before starting work:

    git switch main
    git pull

Then create your branch:

    git switch -c feature/my-feature

Also:

-   Keep branches reasonably short-lived.
-   Pull/rebase regularly according to your team’s workflow.
-   Avoid changing unrelated files.
-   Communicate with teammates.

============================================================ 34. git
restore ============================================================

If you changed a file but want to discard its unstaged changes:

    git restore filename

Example:

    git restore Product.java

WARNING: This can permanently discard your local changes.

Be careful.

============================================================ 35. UNSTAGE
A FILE ============================================================

If you accidentally staged a file:

    git restore --staged filename

Example:

    git restore --staged application.properties

============================================================ 36.
DELETING FILES
============================================================

Delete a file and stage the deletion:

    git rm filename

Example:

    git rm old-code.java

Then commit:

    git commit -m "Remove old code"

============================================================ 37.
RENAMING FILES
============================================================

You can use:

    git mv old-name.java new-name.java

Then:

    git commit -m "Rename product service"

============================================================ 38.
.gitignore EXAMPLE FOR SPRING BOOT
============================================================

A basic example:

    target/
    .idea/
    *.iml
    .vscode/
    .env
    *.log

The exact .gitignore should depend on your project and tools.

Never blindly copy a random .gitignore without understanding whether it
ignores something your project actually needs.

============================================================ 39.
ENVIRONMENT VARIABLES AND SECRETS
============================================================

NEVER commit this:

    DB_PASSWORD=mySecretPassword
    JWT_SECRET=mySecretKey
    API_KEY=123456

Instead, keep secrets outside Git.

For example, use environment variables:

    DB_USERNAME
    DB_PASSWORD
    JWT_SECRET

And make sure local secret files are ignored where appropriate.

If you accidentally commit a secret:

1.  Revoke/rotate the secret immediately.
2.  Remove it from the project.
3.  Understand that deleting it from the latest commit does not
    necessarily remove it from Git history.
4.  Follow your organization’s secret-removal procedure.

============================================================ 40. REMOTE
COMMANDS ============================================================

See remotes:

    git remote -v

Add a remote:

    git remote add origin URL

Change remote URL:

    git remote set-url origin URL

Remove a remote:

    git remote remove origin

============================================================ 41. ORIGIN
AND UPSTREAM
============================================================

“origin” usually means your main remote repository.

Example:

    git push origin main

“upstream” is often used when you fork another project and want a remote
pointing to the original project.

Example:

    origin   = your GitHub fork
    upstream = original project

============================================================ 42. FORKING
============================================================

A fork is your own GitHub copy of someone else’s repository.

Example:

Original:

    github.com/company/project

You fork it.

Your copy:

    github.com/your-account/project

You can modify your fork without directly changing the original project.

Forks are commonly used for open-source contributions.

============================================================ 43. GITHUB
ISSUES ============================================================

Issues are used to track work, bugs, ideas, and tasks.

Example:

    Issue #25
    Title: Product API returns 500 error

Description:

    GET /api/products/10 returns 500 when the product does not exist.

A developer can fix it and reference the issue in a commit or PR.

============================================================ 44. GITHUB
LABELS ============================================================

Labels help organize issues and PRs.

Examples:

    bug
    feature
    documentation
    urgent
    good first issue

Teams can create their own labels.

============================================================ 45. GITHUB
PROJECTS ============================================================

GitHub Projects can be used for project management.

You can create cards such as:

    TODO
    IN PROGRESS
    REVIEW
    DONE

Example:

    TODO:
    - Create Product entity
    - Create Product API

    IN PROGRESS:
    - Add authentication

    DONE:
    - Database connection

============================================================ 46. TAGS
============================================================

Tags can mark important versions.

Example:

    v1.0.0
    v1.1.0
    v2.0.0

Create a tag:

    git tag v1.0.0

Push it:

    git push origin v1.0.0

Tags are useful for releases.

============================================================ 47.
RELEASES ============================================================

GitHub Releases can be used to publish a version of your project.

Example:

    Version 1.0.0

    Features:
    - User registration
    - Login
    - Product management

Releases are especially useful for libraries and applications.

============================================================ 48. GIT
RESET ============================================================

Reset changes Git history or staging depending on how it is used.

Example:

    git reset HEAD~1

This moves your branch back one commit.

Be careful with reset, especially with commits already pushed to a
shared repository.

For beginners, prefer safer commands such as:

    git restore
    git revert

============================================================ 49. GIT
REVERT ============================================================

Revert creates a NEW commit that undoes an earlier commit.

Example:

    git revert abc1234

This is generally safer for shared branches because it does not rewrite
the existing shared history.

============================================================ 50. RESET
VS REVERT ============================================================

Reset:

    Moves branch history.

Revert:

    Creates a new commit that reverses an old commit.

Simple rule:

If the commit is already shared with other people, prefer revert unless
your team specifically tells you to rewrite history.

============================================================ 51. AMEND
============================================================

If you just made a commit and forgot something, you can amend it.

Example:

    git add .
    git commit --amend

This changes the previous commit instead of creating another one.

Be careful when amending commits that have already been pushed/shared.

============================================================ 52. STASH
============================================================

Sometimes you are working on something but need to switch branches
without committing unfinished code.

Use:

    git stash

Your uncommitted changes are temporarily stored.

Then switch branch:

    git switch main

Later return to your branch:

    git switch feature/login

Restore the stashed changes:

    git stash pop

List stashes:

    git stash list

============================================================ 53. GIT
REBASE ============================================================

Rebase can move your branch’s commits onto a newer base.

Example:

    main:    A---B---C
                  \
    feature:       D---E

After rebase onto latest main:

    main:    A---B---C
                       \
    feature:            D'---E'

Rebase can create a cleaner history, but it rewrites commit history.

Important rule:

Do not casually rebase shared branches unless you understand the
consequences and your team allows it.

============================================================ 54. GITHUB
COLLABORATION
============================================================

A team might work like this:

    main
      |
      +-- feature/login
      +-- feature/products
      +-- feature/orders

Developer 1: feature/login

Developer 2: feature/products

Developer 3: feature/orders

Each developer opens a PR.

After review:

    feature/login ------\
    feature/products -----> main
    feature/orders ------/

============================================================ 55.
PROTECTED BRANCHES
============================================================

Teams often protect main.

For example, GitHub can require:

-   Pull Requests
-   Reviews
-   Passing tests
-   No direct pushes

This prevents accidental changes to production code.

============================================================ 56. GITHUB
ACTIONS ============================================================

GitHub Actions can automatically run tasks when something happens in
your repository.

Example:

Developer pushes code | v GitHub Actions | +–> Compile +–> Run tests +–>
Check code +–> Build application +–> Deploy

A workflow is usually stored under:

    .github/workflows/

============================================================ 57. CI/CD
IN SIMPLE LANGUAGE
============================================================

CI = Continuous Integration

Whenever developers push code, automated checks can run.

Example:

    git push
       |
       v
    Run tests
       |
       v
    Build project

CD = Continuous Delivery/Deployment

After checks pass, software can be prepared or deployed automatically.

Example:

    GitHub
       |
       v
    Tests pass
       |
       v
    Build Docker image
       |
       v
    Deploy application

============================================================ 58. GITHUB
ACTIONS EXAMPLE
============================================================

A workflow might conceptually do:

    on push:
        checkout code
        install Java
        run tests
        build application

The exact workflow depends on your project.

============================================================ 59. SSH VS
HTTPS ============================================================

You can connect Git to GitHub using HTTPS or SSH.

HTTPS example:

    https://github.com/USERNAME/project.git

SSH example:

    git@github.com:USERNAME/project.git

SSH requires creating an SSH key and adding its public key to GitHub.

SSH can be convenient for frequent Git usage.

Do NOT share your private SSH key.

============================================================ 60. GITHUB
AUTHENTICATION
============================================================

When GitHub authentication asks for credentials, modern GitHub usage
generally does not mean entering your normal GitHub password into Git.

Depending on your setup, you may use:

-   GitHub CLI
-   Git Credential Manager
-   SSH keys
-   A personal access token where appropriate

Never share authentication tokens.

============================================================ 61. GITHUB
CLI ============================================================

GitHub provides a command-line tool called GitHub CLI.

It can help you work with GitHub from the terminal.

Common commands include:

    gh auth login

    gh repo clone OWNER/REPOSITORY

    gh pr create

    gh pr list

You still need to understand Git itself.

============================================================ 62. GIT
ALIASES ============================================================

You can create shortcuts.

Example:

    git config --global alias.st status

Now:

    git st

means:

    git status

Aliases are optional.

============================================================ 63. COMMON
GIT COMMAND CHEAT SHEET
============================================================

Check Git version:

    git --version

Configure name:

    git config --global user.name "Your Name"

Configure email:

    git config --global user.email "you@example.com"

Initialize:

    git init

Clone:

    git clone URL

Status:

    git status

Stage:

    git add .

Commit:

    git commit -m "message"

History:

    git log --oneline

Changes:

    git diff

Push:

    git push

Pull:

    git pull

Fetch:

    git fetch

Branches:

    git branch

Create/switch branch:

    git switch -c feature/name

Switch branch:

    git switch main

Merge:

    git merge feature/name

Stash:

    git stash

Restore stash:

    git stash pop

Undo shared commit safely:

    git revert COMMIT_ID

See remote:

    git remote -v

============================================================ 64.
COMPLETE EXAMPLE: START A NEW PROJECT
============================================================

Suppose you created a Spring Boot project locally.

Project:

    ecommerce-backend/

Open terminal:

    cd ecommerce-backend

Initialize Git:

    git init

Check status:

    git status

Create/add a .gitignore.

Then:

    git add .

Commit:

    git commit -m "Initial Spring Boot project"

Create an empty GitHub repository called:

    ecommerce-backend

Connect it:

    git remote add origin https://github.com/USERNAME/ecommerce-backend.git

Set main:

    git branch -M main

Push:

    git push -u origin main

Done.

Your local project is now connected to GitHub.

============================================================ 65.
COMPLETE EXAMPLE: ADD A FEATURE
============================================================

You want to add a Product API.

Start:

    git switch main
    git pull

Create feature branch:

    git switch -c feature/product-api

Write code.

Check:

    git status

Review:

    git diff

Stage:

    git add .

Commit:

    git commit -m "Add product API"

Push:

    git push -u origin feature/product-api

Open GitHub.

Create a Pull Request:

    feature/product-api -> main

Get review.

Fix requested changes.

Commit and push again:

    git add .
    git commit -m "Add product validation"
    git push

After approval, merge the PR.

============================================================ 66.
COMPLETE TEAM WORKFLOW
============================================================

A professional workflow can look like:

    1. git switch main
    2. git pull
    3. git switch -c feature/login
    4. Write code
    5. Run tests
    6. git status
    7. git diff
    8. git add .
    9. git commit -m "Add login API"
    10. git push -u origin feature/login
    11. Open Pull Request
    12. Code review
    13. Fix comments
    14. Tests pass
    15. Merge PR
    16. Delete feature branch if appropriate

============================================================ 67. WHAT
SHOULD YOU COMMIT?
============================================================

Usually commit:

-   Source code
-   Tests
-   README
-   Configuration templates
-   Database migration files
-   Documentation
-   Build configuration

Usually don’t commit:

-   Passwords
-   API keys
-   Private keys
-   Personal secrets
-   Huge generated build folders
-   Temporary files
-   IDE-specific files when unnecessary
-   Local environment files containing secrets

============================================================ 68. WHAT IF
YOU COMMIT THE WRONG FILE?
============================================================

If you staged it but haven’t committed:

    git restore --staged filename

If you committed locally but haven’t pushed, you have several options
depending on what you want to change.

If the commit has already been pushed, don’t randomly rewrite history.
Usually create another commit or use git revert.

If a secret was committed, treat it as exposed and rotate it
immediately.

============================================================ 69. WHAT IF
git push IS REJECTED?
============================================================

A common reason:

Someone else pushed changes before you.

You may see a message saying the remote contains work you do not have.

Usually:

    git pull

Resolve conflicts if necessary.

Then:

    git push

If your team uses rebase, they may instead instruct you to use:

    git pull --rebase

Do not blindly use force push.

============================================================ 70. FORCE
PUSH ============================================================

Force push can overwrite remote history.

Example:

    git push --force

This is dangerous on shared branches.

A safer variant in many situations is:

    git push --force-with-lease

Even then, understand why you need it before using it.

NEVER force push to main unless your team explicitly requires it.

============================================================ 71.
DETACHED HEAD
============================================================

You may see:

    HEAD detached at abc1234

This means you checked out a specific commit instead of working on a
normal branch.

You can inspect the code safely.

If you want to keep new work, create a branch:

    git switch -c my-new-branch

============================================================ 72. GIT
HISTORY IN SIMPLE TERMS
============================================================

Imagine:

    A -- B -- C -- D

Each letter is a commit.

A: Initial project.

B: Added database.

C: Added product API.

D: Added authentication.

Git remembers this history.

A branch is essentially a movable pointer to commits.

============================================================ 73. MERGE
VS REBASE ============================================================

Merge:

    Combines histories.

    A---B---C
         \
          D---E
               \
                M

Rebase:

    Replays your commits on top of a newer base.

    A---B---C---D'---E'

Both can be useful.

For beginners: Learn merge first. Learn rebase after you understand
branches and commits.

============================================================ 74. GITHUB
PROFILE ============================================================

Your GitHub profile can act as part of your developer portfolio.

Good profile:

-   Clear username
-   Profile README if useful
-   Good projects
-   Good README files
-   Meaningful commit history
-   Clean repositories
-   Documentation
-   Screenshots where useful
-   Setup instructions

For job applications, recruiters may look at your projects.

============================================================ 75. HOW TO
MAKE A GOOD PROJECT README
============================================================

Include:

    # Project Name

    ## Description
    What does the project do?

    ## Features
    - User registration
    - Login
    - Product management

    ## Tech Stack
    - Java
    - Spring Boot
    - PostgreSQL

    ## Requirements
    - Java 21
    - PostgreSQL

    ## Installation
    Explain how to run it.

    ## API
    Explain important endpoints.

    ## Environment Variables
    Explain variable NAMES, not actual secret values.

    ## Screenshots
    Optional.

    ## Future Improvements
    Optional.

============================================================ 76. GOOD
COMMIT PRACTICES
============================================================

A good commit should generally represent one logical change.

Good:

    Add user registration API
    Add product validation
    Fix order total calculation
    Add JWT authentication

Less useful:

    Update everything
    Changes
    Final code
    Work

============================================================ 77. SMALL
COMMITS VS HUGE COMMITS
============================================================

Instead of:

    "Added entire application"

Prefer logical commits:

    Add project structure
    Add database configuration
    Add product entity
    Add product repository
    Add product service
    Add product controller
    Add product validation
    Add product tests

This makes the history easier to understand and review.

============================================================ 78. GIT
TAGGING VERSION EXAMPLE
============================================================

Suppose your application is ready for its first release:

    git tag v1.0.0
    git push origin v1.0.0

Later:

    v1.1.0

Major releases might be:

    v2.0.0

============================================================ 79.
SEMANTIC VERSIONING
============================================================

A common version format is:

    MAJOR.MINOR.PATCH

Example:

    2.4.1

MAJOR: Breaking changes.

MINOR: New backward-compatible features.

PATCH: Bug fixes.

The exact release policy depends on the project.

============================================================ 80. GIT FOR
YOUR SPRING BOOT PROJECT
============================================================

For the backend project we are building, a good repository might look
like:

    ecommerce-backend/
    |
    +-- src/
    +-- pom.xml
    +-- README.md
    +-- .gitignore
    +-- docker-compose.yml
    +-- .github/
        +-- workflows/

We might have branches:

    main
    develop
    feature/authentication
    feature/products
    feature/orders

The exact branching strategy depends on the team.

============================================================ 81. GIT FOR
A REACT PROJECT
============================================================

A React project can also use Git.

Example:

    ecommerce-frontend/

You can use exactly the same basic commands:

    git init
    git add .
    git commit -m "Initial React project"
    git remote add origin URL
    git push -u origin main

Make sure your .gitignore excludes appropriate generated and local
files.

============================================================ 82.
FULL-STACK PROJECT WITH TWO REPOSITORIES
============================================================

You can have:

    ecommerce-frontend
        |
        React

    ecommerce-backend
        |
        Java + Spring Boot

Each can have its own GitHub repository.

Example:

    GitHub
      |
      +-- ecommerce-frontend
      |
      +-- ecommerce-backend

============================================================ 83. OR ONE
FULL-STACK REPOSITORY
============================================================

You can also use one repository:

    ecommerce/
      |
      +-- frontend/
      |     +-- React
      |
      +-- backend/
            +-- Spring Boot

Both approaches are valid.

The choice depends on your team and deployment structure.

============================================================ 84. COMMON
MISTAKES BEGINNERS MAKE
============================================================

1.  Forgetting to git pull before starting team work.

2.  Committing passwords.

3.  Working directly on main.

4.  Using huge commit messages or meaningless messages.

5.  Running commands without understanding them.

6.  Using force push carelessly.

7.  Ignoring merge conflicts.

8.  Committing generated files.

9.  Not checking git status.

10. Not reviewing code before committing.

11. Making one giant commit containing unrelated changes.

12. Assuming GitHub and Git are the same thing.

============================================================ 85. THE
MOST IMPORTANT COMMANDS TO MEMORIZE
============================================================

You don’t need to memorize every Git command.

Start with these:

    git status
    git add .
    git commit -m "message"
    git push
    git pull
    git clone URL
    git branch
    git switch branch
    git switch -c branch
    git merge branch
    git log --oneline
    git diff

============================================================ 86. THE
GOLDEN RULE ============================================================

Before doing something risky, understand what it will do.

Especially be careful with:

    git reset
    git rebase
    git push --force
    git push --force-with-lease
    deleting branches
    rewriting history

============================================================ 87. A
SIMPLE MENTAL MODEL
============================================================

Remember these four stages:

    1. WORK
       You edit files.

    2. STAGE
       git add

    3. COMMIT
       git commit

    4. SHARE
       git push

Example:

    Write code
       |
       v
    git status
       |
       v
    git add .
       |
       v
    git commit -m "Add login API"
       |
       v
    git push
       |
       v
    GitHub

============================================================ 88.
BEGINNER PRACTICE EXERCISE
============================================================

Create a folder:

    github-practice

Inside it create:

    README.md

Put:

    # GitHub Practice

Then:

    git init
    git add .
    git commit -m "Initial commit"

Create a GitHub repository.

Connect:

    git remote add origin YOUR_REPOSITORY_URL

Push:

    git branch -M main
    git push -u origin main

Now edit README.md.

Add:

    ## Features

    - Learning Git
    - Learning GitHub

Then:

    git status
    git diff
    git add README.md
    git commit -m "Update README"
    git push

Then open GitHub and check the changes.

============================================================ 89.
PRACTICE BRANCH EXERCISE
============================================================

Create a branch:

    git switch -c feature/readme-update

Edit README.md.

Commit:

    git add .
    git commit -m "Improve README"

Push:

    git push -u origin feature/readme-update

Open GitHub.

Create a Pull Request.

Review it.

Merge it.

Then locally:

    git switch main
    git pull

You have now practiced a basic professional workflow.

============================================================ 90. QUICK
REFERENCE: WHAT COMMAND SHOULD I USE?
============================================================

I want to see changes: git status

I want to see exact changes: git diff

I want to stage one file: git add filename

I want to stage everything: git add .

I want to save a checkpoint: git commit -m “message”

I want to send commits to GitHub: git push

I want to get the latest shared changes: git pull

I want to download a GitHub repository: git clone URL

I want to create a branch: git switch -c feature/name

I want to change branches: git switch branch-name

I want to combine a branch: git merge branch-name

I want to see history: git log –oneline

I accidentally staged a file: git restore –staged filename

I want to temporarily save unfinished changes: git stash

I want to undo a shared commit safely: git revert COMMIT_ID

============================================================ 91. FINAL
LEARNING PATH
============================================================

Learn Git in this order:

    1. What Git is
    2. git init
    3. git status
    4. git add
    5. git commit
    6. git log
    7. GitHub repositories
    8. git remote
    9. git push
    10. git clone
    11. git pull
    12. Branches
    13. Pull Requests
    14. Merge conflicts
    15. .gitignore
    16. Revert
    17. Stash
    18. Rebase
    19. GitHub Actions
    20. Team workflows

============================================================ 92. THE ONE
WORKFLOW TO REMEMBER
============================================================

For normal development:

    git switch main
    git pull

    git switch -c feature/my-feature

    [write code]

    git status
    git diff

    git add .
    git commit -m "Add my feature"

    git push -u origin feature/my-feature

    [Open Pull Request on GitHub]

    [Review + fix comments + merge]

    git switch main
    git pull

============================================================ END
============================================================

The goal is not to memorize hundreds of Git commands.

Understand this:

    Git = tracks your code history
    GitHub = hosts/shares your Git repositories
    Branch = separate line of work
    Commit = checkpoint
    Push = send your commits to GitHub
    Pull = get changes from GitHub
    Pull Request = ask the team to review and merge your changes

Once these concepts are comfortable, Git becomes much easier to use.
