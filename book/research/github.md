+++
# GitHub Integration

Since in this project we are merely creating a plugin for the already established ecosystem of TeachBooks, we had to adopt their reliance on GitHub. Thus, a substantial amount of resources was allocated to researching how to properly integrate our application with GitHub. This process was split in two parts — looking into the login procedure and learning about the GitHub API for Repository Access and Commits. These will be explained in [Login Procedure](#login-procedure) and [Repository Acces and Commits](#repository-access-and-commits) respectively.

## Login Procedure

The first thing that we needed to consider was whether to use  GitHub Apps or OAuth apps.{cite}`differencesBetweenOauthAndGitHubApps` At a first glance, the OAuth apps appeared to be the better option - they have more customizable permissions and can access specific endpoints.{cite}`decidingWhenToBuildGitHubApp` Both of these functionalities would aid the app’s workflow and security.&#x20;

Ultimately, however, we found a fatal flaw in the usage of GitHub Apps - in order to function securely they need a backend server. They rely on GitHub Secrets {cite}`aboutSecrets`, which we would have no secure way to store and process in our front-end only app. If exposed, this secret can let malicious third parties access everything the secret allows access to.&#x20;

Another issue with using GitHub Apps comes in the form of CORS - Cross Origin Resource Sharing. This is a security feature that blocks cross-origin requests from different domains unless  explicitly granted permission. The problem lies in the fact that due to security concerns GitHub does not grant the necessary permissions to unregistered domains, and since every book has its own domain, we cannot reliably get around this issue.&#x20;

In the end we were forced to work with OAuth apps, however that method also had drawbacks - the standard approach too requires a backend for reasons similar to GitHub Apps {cite}`authorisingOauthApps`. The way front-end only single-page apps usually deal with this issue is by using PKCE (Proof Key for Code Exchange).{cite}`singlePageApps` This feature essentially eliminates the dangers of not having a backend by only providing an access token to the user that requested it and nobody else. Unfortunately, GitHub does not support the use of  PKCE.

The only option we had left was to remove the automated token creation process altogether and instead only rely on users creating their tokens outside of the app and merely pasting them to get access. This approach hinders the user experience, but is the only secure way to authenticate.

## Repository Access and Commits

For the repository access and commit functionality we had to learn how the GitHub REST API{cite}`gitHubRestApiDoc` works and which endpoints to access. This part did not pose as serious a challenge as the previous one. All of the useful endpoints are in the API doc. The ones we have used are:

*   GET https://api.github.com/repos/{owner}/{repo} to fetch repository metadata (e.g., default branch).
*   GET https://api.github.com/repos/{owner}/{repo}/contents/{path}?ref={branch} to fetch file contents from a specific branch.
*   GET https://api.github.com/repos/{owner}/{repo}/branches?per-page=100 to list up to 100 branches.
*   GET https://api.github.com/repos/{owner}/{repo}/branches/{branch} to get commit/tree info for a branch.
*   POST https://api.github.com/repos/{owner}/{repo}/git/refs to create a new branch (ref).
*   POST https://api.github.com/repos/{owner}/{repo}/git/tree to create a new Git tree with files.
*   POST https://api.github.com/repos/{owner}/{repo}/git/commits to create a new commit object.
*   PATCH https://api.github.com/repos/{owner}/{repo}/git/refs/heads/{branch} to update an existing branch ref to point to a new commit.
