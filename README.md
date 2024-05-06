# Gitea Mirror Manager

This script uses [Gitea's API](https://try.gitea.io/api/swagger) to manage remote push mirrors for local repositories.

I recently installed [Gitea](https://about.gitea.com/) and like to keep my [dotfiles](https://github.com/cn246-dotfiles) and some other projects synced between local, GitHub and GitLab.

After realizing that GitHub and GitLab's API Keys expire and I would have to update every mirror on a regular basis, someone mentioned that automating this may be a good idea.

Herein lies my attempt.


## Usage
The script uses Python's builtin modules so no external dependencies are required.

Note that I organize my repositories in Organizations (Gitea, GitHub) and Groups (GitLab) and this script manages the mirrors using that layout.

Create API keys in [Gitea](https://docs.gitea.com/development/api-usage), [GitHub](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens) and [GitLab](https://docs.gitlab.com/ee/user/profile/personal_access_tokens.html) - or wherever you want to push to.

Copy **settings.json.example** to **settings.json** and edit it accordingly.

Add any repositories you do not want to sync to the **gitea_ignore_sync** section.


## What it doesn't do

It may or may not work without Organization/Group repository structure.

It doesn't check if a mirror exists - It will delete any existing push mirrors and re-create them.

It doesn't check if the remote repository exists - It will create the remote mirrors but GitHub will have errors in the Web UI and GitLab will create a private repository if it does not exist.

It doesn't verify your API keys for GitHub or GitLab.

It doesn't check ignore repository group/orginazation. Currently, it just uses the repository name to ignore.

It doesn't handle Exceptions like it probably should.

These features may or may not be added in the future - time permitting.

I am always open to working with anyone to improve my code.


## What it does do

Exactly what I needed it to -- update GitHub/GitLab API keys on my push mirrors :)


## Links
- https://docs.gitea.com/next/usage/repo-mirror
- https://try.gitea.io/api/swagger
- https://docs.gitea.com/development/api-usage
- https://docs.python.org/3/library/urllib.request.html#module-urllib.request
- https://docs.python.org/3/howto/urllib2.html
