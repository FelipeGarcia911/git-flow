# Git Flow + Release-It + CommitMessage
Git Flow Configuration Example

# Documentation
- https://nvie.com/posts/a-successful-git-branching-model/
- https://github.com/release-it/release-it
- https://www.youtube.com/watch?v=BbdFfvZNWNw&ab_channel=Codity
- https://github.com/codityco/001-add-a-changelog-to-any-project

## Working Flow
These are the suggested working flow to work with Release-It

# Feature/Fix Working Steps
1. Create your feature(feat) or hotfix branch (fix) with develop as base branch (e.g: `git checkout develop && git checkout -b feat/my-feature-branch`)
2. Work on your branch and commit your changes with a message (e.g: 'feat: update some files', 'fix: resolve conflicts')
3. Create a MR/PR from your branch to develop and request some approvals
4. Merge your approved MR into develop

# Create a Staging Release
1. Go to develop branch and then create a release branch (e.g: `git checkout develop && git checkout -b release-31-01-2023`)
2. Start the release process with `yarn release` and follow the steps.
3. Go to GitHub and create an MR from the release branch against staging and request some approvals
4. Merge your approved MR into staging
5. Rebase develop with the latest changes in staging

# Create a Production Release - With NOT changes added after the last Staging Release
1. Go to the release branch created before (for the staging release)
2. Go to GitHub and create an MR from the release branch against production and request some approvals
3. Use `Rebase and Merge` strategy to add your approved MR into production.
4. Rebase staging with the latest changes in production
5. Rebase develop with the latest changes in staging

# Create a Production Release - With changes added after the last Staging Release
1. Go to staging branch and then create a release branch (e.g: `git checkout staging && git checkout -b release-31-01-2023`)
2. Start the release process with `yarn release` and follow the steps.
3. Bump the release version and the tag version. (It's due to we added some fixes or features after the staging release)
4. Go to GitHub and create an MR from the release branch against production and request some approvals
5. Use `Rebase and Merge` strategy to add your approved MR into production.
6. Rebase staging with the latest changes in production.
7. Rebase develop with the latest changes in staging.