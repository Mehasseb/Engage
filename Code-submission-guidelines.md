# Code Submission Guidelines

We've enacted standards for commits and pull requests to effectively manage the project over
time. We expect all code contributed to follow these standards. If your code doesn't follow them, we
will kindly ask you to resubmit it in the correct format.

- [Submitting a pull request](#submitting-a-pull-request)
- [Merging a pull request](#merging-a-pull-request)




## Submitting a pull request

We want to keep our commit log clean by avoiding merge messages in branches. Before submitting a pull request, make sure your branch is up to date with the develop branch by either:

- Pulling from develop before creating your branch
- Doing a rebase from origin/develop (will require a force push **on your branch**)

To rebase from origin/develop if we've pushed changes since you created your branch:

```sh
git checkout your-branch
git fetch
git rebase origin/develop
git push origin head -f
```
## Merging a pull request

If a pull request has many commits (especially if they don't follow our [commit policy](#git-commits)), you'll want to squash them into one clean commit.

In the Github UI, you can use the new [Squash and Merge](https://github.com/blog/2141-squash-your-commits) feature to make this easy. If there are merge conflicts preventing this, either ask the committer to rebase from develop following the [PR submission steps above](#submitting-a-pull-request), or use the manual method below.

To apply a pull request manually, make sure your local develop branch is up to date. Then, create a new branch for that pull request.

Create a temporary, local branch:

```sh
git checkout -b temp-feature-branch
```

Run the following commands to apply all commits from that pull request on top of your branch's local history:

```console
curl -L https://github.com/dequelabs/axe-core/pull/205.patch | git am -3
```

If the merge succeeds, use `git diff origin/develop` to review all the changes that will happen post-merge.
