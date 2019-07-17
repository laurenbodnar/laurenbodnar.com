# Lauren Bodnar's blog: [laurenbodnar.com](https://laurenbodnar.com)
[![Netlify Status](https://api.netlify.com/api/v1/badges/261034c0-28cf-49d2-a433-ae181f6fc240/deploy-status)](https://app.netlify.com/sites/laurenbodnar/deploys)

----

![](.github/screenshot.jpeg)


---

## Tech Stack
 - [hexo.io](https://hexo.io/docs)
 - [frontmatter](https://jekyllrb.com/docs/front-matter/)
 - [JAMstack](https://jamstack.org)
 - [Markdown](https://guides.github.com/pdfs/markdown-cheatsheet-online.pdf)
 - [ejs](https://ejs.co/#docs)


## Commands

1. **Start development server** and open web browser: `npm start`
  - **New draft / post / page**

  ```shell
  hexo new [type] [post title]
  ```

  - **Add local image (as opposed to the internet)**

  ```shell
  hexo new [type] [post title]
  ```

  - **Deployment**: deployments happen automatically when a pull request is merged into master.

## Git Workflow

### Github pull-request guide

  1. __Issue__: Create an issue to describe your feature: [/issues/new](https://github.com/laurenbodnar/laurenbodnar.com/issues/new)

  2. __Branch__: Checkout a new branch in the terminal for your issue / feature:

   ```shell
   git checkout master && git pull
   git checkout -b 'features/feature-1'
   ```

  3. __Edit__ your files and do da coding. (If something comes up and you need to make other edits before this feature is finished, refer to the [Troubleshooting](#Troubleshooting) below)

  4. __Commit__ your changes in Atom, or via the terminal:

   ```shell
   git add . && git commit -m "this is a short description of what changed for issue #1"
   ```

  5. __Push__ your feature branch up to github

   ```shell
   git push -u origin features/feature-1 # 1st time
   git push # 2nd time on
   ```

  6. __Pull Request__: [Submit a pull request](https://github.com/laurenbodnar/laurenbodnar.com/compare)

  7. __Squash and merge__ your changes and then delete the feature branch. This merges into master. Netilfy deploys it. No need to run deploy.

  8. __Pull__ changes into your local master branch

#### Troubleshooting

  - Changes unrelated to current feature branch: sometimes you need to make edits to files that you don't want in your feature branch. Fix that by

    1. Committing your changes (see step 4 above), or stashing them:

        ```shell
        git add . && git stash
        ```

    2. Checkout master:

        ```shell
        git checkout master
        ```

    3. Follow steps 2-8 for your 2nd concurrent branch (let's call it `bugs/bug-1`)

    4. Once finished, you can checkout your unfinished feature and rebase those changes:

        ```shell
        git checkout 'features/feature-1'
        git stash pop # ONLY do this if you stashed your changes instead of committing them in step 1
        git rebase origin/master
        ```

      *NOTE: git stash pop will "pop" out the last stashed code and apply it. You can use git stash multiple times, and git stash pop them in the order they were added, or use git stash list and git stash apply --index stash@{2}*

      [Git stash documentation](https://git-scm.com/book/en/v1/Git-Tools-Stashing)

    5. Pick up where you left off (step 3)


### Simple feature-branch guide
This is a much simpler git workflow that doesn't include github issues.

  ```shell
  # 1) Checkout "develop" branch and fetch most recent changes from github's master branch
  git checkout develop && git rebase origin/master

  # 2) Create a new feature branch to track your changes
  git checkout -b random-feature-name

  # 3) Edit files
  touch test.txt

  # 4) Commit your changes
  git add .
  git commit -m "Created an empty file called test.txt"

  # 5) Merge your branch into develop
  git checkout develop && git merge random-feature-name

  # 6) Repeat steps 2-5 as many times as you like. When you're ready to "publish" your changes to the master branch, you can either push your develop branch to github and submit a merge request, or you can merge it into your local master via command line and then push master to github.

  git checkout master
  git merge develop
  git push
  ```

### Tips and Tricks

  - Git is **extremely** flexible. You can merge any branch into any other branch by checking out the destination branch (e.g. `master`) and running `git merge develop` (assuming `develop` is the source branch that you want merged into `master`).
  - **git merge [source-branch]** applies changes from other branch on top of current branch.
  - **git rebase [source-branch]** sets your commits aside, and applies the commits from `source-branch` and then applies your commits back on top of `source-branch`'s commits. Think of it as a way of syncing base foundation.
  - **Resolving conflicts**: the easiest way to resolve conflicts is to use Atom or [GitKraken](https://www.gitkraken.com/git-client)
  - Image size when making my own 1204px x 677px

## Cheatsheets

![markdown cheatsheet](https://media.cheatography.com/storage/thumb/mrgrauel_gitlab-flavored-markdown.750.jpg)
