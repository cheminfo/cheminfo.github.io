---
layout: page
title: Contribution guide
permalink: /contribute/
---

# How can I contribute to the ELN?

All contributions are more than welcome! If you have a problem/found a bug you can [open an issue](https://docs.github.com/en/github/managing-your-work-on-github/creating-an-issue) on the [bug tracker](https://github.com/cheminfo/eln.epfl.ch/issues) or let us know in the [Slack workspace](https://elnepflchforum.slack.com/)).

# How can I make contributions to code and documentation?

For contributions to code and documentation you will need a GitHub accounts, you will fork a repository, make a new branch, edit the code, and then make a pull request. In the following, we will go through all these steps.

1. If you do not already have one, create a GitHub account: To create a GitHub account, follow the instructions [on the GitHub page](https://github.com/join).
2. If you do not already have Git installed on your machine, you'll need to install it.

   - On Windows you can go to [GIT-SCM](https://git-scm.com/download/win) and download the executable.
   - On Mac, the most convenient way is to use [Homebrew](https://brew.sh/). For this you'll need to [install homebrew](https://brew.sh/) and then run `brew install git` from the terminal
   - On Ubuntu (i.e., also Windows subsystem for Linux) you can just run `apt-get install git` from the terminal

3. We recommend that you install [VSCode](https://code.visualstudio.com/) and some plugins. We wrote a [blog post](https://cheminfo.github.io/eln.epfl.ch/tutorial/cheminfo_dev_setup/) describing how to set up the development environment and the first section discusses the VSCode setup.
4. Once you have your GitHub account and your coding setup ready, you can [fork](https://docs.github.com/en/enterprise-server@2.20/github/getting-started-with-github/fork-a-repo) the repository you want to make a contribution to. "Forking" just means that you make a copy of the repository. To do so, you just need to click on the fork button in the top right corner. For contributions to the documentation, you'll need to fork the [c6h6-documentation](https://github.com/cheminfo/c6h6-documentation) repository.
5. Clone the fork to your local computer and make a new branch.
6. Make changes to the code or documentation. And commit them. We have a [blog post](https://cheminfo.github.io/eln.epfl.ch/tutorial/cheminfo_docs/) describing how the documentation works.
7. Push the changes to the remote and make a pull request.

We go through steps 4--7 in a video tutorial in the [blog post](https://cheminfo.github.io/eln.epfl.ch/tutorial/cheminfo_docs/).
