# Getting started

## Tools

### IDE

In order to write code, you need an IDE. There are a few free IDEs available:

- [VSCode](https://code.visualstudio.com/)
- [Sublime Text](https://www.sublimetext.com)
- [Brackets](https://brackets.io/)

### Terminal

All operating systems should come with a CLI. A terminal will allow you to run commands and build software without an GUI.

Windows has [PowerShell](https://learn.microsoft.com/en-us/powershell/), Mac OS has [Terminal](https://support.apple.com/en-gb/guide/terminal/apd5265185d-f365-44cb-8b09-71a064a42125/mac) and Linux usually has a CLI such as [Ubuntu's command line](https://ubuntu.com/tutorials/command-line-for-beginners).

Some IDEs have terminal built in which leverage the CLI of the OS.

## Services

### GitHub

Our source code is stored on [GitHub](https://github.com/). You will need to [set up a GitHub account](https://github.com/join) in order to contribute to our projects.

Once you have an account, you need to be added to the [National Archives GitHub organisation](https://github.com/nationalarchives) as well as one of the [National Archives GitHub teams](https://github.com/orgs/nationalarchives/teams). Please ask your webmaster for access to this.

Read our [GitHub guidelines](/developer-handbook/third-party/github/) for a better idea of how we use GitHub.

### Docker

Most of our applications are built as containers using Docker. You will need to download and install [Docker Desktop](https://www.docker.com/) in order to build and run these containers.

Make sure that you download the correct version of Docker. If you have a newer Apple Mac then you may need the version of Docker that is specific to the Apple M-series chips.

Creating a [Docker account](https://hub.docker.com/signup) will give you a higher download limit. For anonymous users, the rate limit is set to 100 pulls per 6 hours per IP address but for authenticated users, it's 200 pulls per 6 hour period.

We have a set way of working and [standards for our containers](/developer-handbook/standards/containers/) to ensure security and consistency.
