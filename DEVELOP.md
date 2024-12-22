# Getting started with developing Natron's website

Natron's website uses Jekyll, a static site generator. It usually saves us a lot of time reduces our trouble, but we know it can be confusing to many newer developers and get *them* in lots of trouble. So, here is a reliable means of developing Natron's website for Mac users, Windows users, and GNU/Linux users!

If you're an absolute beginner, we recommend taking a look at the [terminal cheat sheet](https://terminalcheatsheet.com/) as well as the [Atlassian tutorials on version control and git](https://www.atlassian.com/git/tutorials/what-is-version-control) before continuing. In addition, it may be helpful to look through the [Jekyll setup guide](https://jekyllrb.com/docs/step-by-step/01-setup/).

If you run into any issues, look at the FAQ and [Development Gotchas](#development-gotchas) section at the bottom of this guide.

## Installing prerequisites for development

### Prerequisites for all operating systems

Before doing anything, check that you have a reliable internet connection. Additionally, Windows users should run all the listed commands in **powershell**, not the command prompt.

Make sure you have `git` installed. If you are using macOS or GNU/Linux, you likely already have it installed; Windows users can download and run the installer from [its official download page](https://git-scm.com/download/). Check that you have `git` correctly installed by running this on Mac/Linux:

```bash
if type git &> /dev/null; then echo Git installed!; else echo Git not installed.; fi
```

Or this on Windows:

```powershell
where git; if %errorlevel% neq 0 echo git is not installed.
```

Now, head to correct instructions for your operating system:

- [GNU/Linux](#gnu/linux-instructions)
- [Windows](#windows-instructions)
- [macOS](#macos-instructions)

### GNU/Linux Instructions

First, you want to install `rbenv` simply because many packaged versions of ruby (which is the programming language Jekyll is written in) have lots of other things "dragged in" - we don't want that. We also highly recommend that any already-installed versions of ruby or Jekyll be removed. Check if you have one with the command `command -v /usr/bin/ruby` - if it returns a result, then you have a system ruby installation. This guide presumes that you've already uninstalled any system ruby installation before starting the guide.

To install `rbenv`:

- On Ubuntu/Debian-based distros run `sudo apt-get install rbenv`
- On Arch-based distros (assuming you've setup the AUR) run `yay -S rbenv`
- On CentOS-based distros run `sudo dnf install rbenv`
- On Red Hat, run `sudo yum install rbenv`

After installation, open a new terminal. If you run the command `rbenv init`, you should see an instruction to paste `eval "$(rbenv init -)"`  into your `.bashrc` or `.zshrc`. Do that, and then restart your shell (or just open a new terminal window).

Next, we want to install ruby itself. Interestingly, `rbenv` doesn't actually do the installing of ruby itself, we need the `ruby-build` plugin before we can actually install it. So, run:

```bash
mkdir -p "$(rbenv root)"/plugins
git clone https://github.com/rbenv/ruby-build.git "$(rbenv root)"/plugins/ruby-build
exec $SHELL # reloads your shell, zsh/bash/fish/etc.
```

To make sure everything is working right, run:

```bash
curl -fsSL https://github.com/rbenv/rbenv-installer/raw/main/bin/rbenv-doctor | bash
```

You should have all the checks pass - great! Now we start doing the install. Run `rbenv install 3.3.3` - `rbenv` will begin downloading and install ruby for you. Note - it will take a while! 3-5 minutes is to be expected, up to 10 minutes for some installs is possible. Grab a snack and a coffee while you're at it.

Next, run `rbenv versions`. You should see 3.3.3 as the listed version. We want to make this our default version of ruby, so run `rbenv global 3.3.3`. This sets our specific version of ruby to be accessible system-wide. Don't worry, you can easily use a different version of Ruby with `rbenv` if you're developing a different ruby project. As before, run `exec $SHELL` to reload your shell. You should now have the `ruby` command available to you.

We can now begin installing Jekyll. We first install `bundler`, the package manger that installs Jekyll, with `gem install bundler`. Then, clone a copy of the Natron website repository to your computer, like this:

```bash
git clone https://github.com/NatronGitHub/NatronGitHub.github.io && cd NatronGitHub.github.io
```

If you would like to troubleshoot Jekyll, run `bundle exec jekyll doctor` which will identify any issues that might have arose.

Finally, you can run bundler which automatically installs Jekyll as well as starts a development server:

```bash
DISABLE_WHITELIST=true # allows plugings to run
bundle install && bundle exec jekyll serve
```

You're done! See the beautiful website in front of your eyes.

If you want a better development experience, you can run an auto-reloading server like so:

```bash
bundle exec jekyll serve --livereload
```

And Jekyll can auto-build the site for you every time you make a change:

```bash
bundle exec jekyll build --watch
```

## Windows Instructions

Getting Jekyll on Windows is a more lengthy process. First, install [rbenv for Windows](https://github.com/ccmywish/rbenv-for-windows). To do so, open a Powershell terminal, and then run:

```powershell
$env:RBENV_ROOT = "$HOME\Ruby-on-Windows"
iwr -useb "https://github.com/ccmywish/rbenv-for-windows/raw/main/tools/install.ps1" | iex
```

If either command doesn't run correctly, you may lack the ability to run Powershell scripts. To solve this, open an _administrator_ Powershell terminal, and run:

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

Then opening another terminal and re-running the installation command for `rbenv` should work. The powershell profile must then be modified to activate rbenv. To do so, run `notepad $PROFILE`, and in the resulting notepad window add in the following lines:

```powershell
# rbenv for Windows
$env:RBENV_ROOT = "$HOME\Ruby-on-Windows"

# init rbenv
& "$env:RBENV_ROOT\rbenv\bin\rbenv.ps1" init
```

`rbenv` also requires that the free 7-zip file archiver is installed. If not, then [head to the 7-zip website](https://www.7-zip.org/). Then run `notepad $profile` and add the following line:

```powershell
# Add 7zip to PATH
$env:Path += ';C:\Program Files\7-Zip'
```

Test by running `7z`, if it simply shows a bunch of options (it is quite verbose!) but no "executable not found"-style error, you may proceed with the rest of these steps.

Now (assuming you either have installed 7-zip or have followed the steps to install it) open another powershell terminal, and rbenv should automatically start downloading the Ruby toolchain. If it does not, run:

```powershell
rbenv install 3.3.3
rbenv global 3.3.3
```

To check that these commands succeeded, run `rbenv global` and it should output something like `3.3.3-1`.

Note that if it prompts between installing the lite version or the full version, choose the **full version**. Once this is installed, run:

```powershell
gem install bundler
```

Then, clone the repository with Git:

```powershell
git clone https://github.com/NatronGitHub/NatronGitHub.github.io && cd NatronGitHub.github.io
```

And install the dependencies for Jekyll (which might take quite a while, you can let it run in the background):

```powershell
bundle install
```

For reasons we are not entirely aware, this command may fail even when rbenv is installed to a directory that does not require elevated (administrator) permissions. As a temporary fix, open an administrator powershell, and then re-run `bundle install`, which should allow it to work. Finally, to launch the website server, run:

```powershell
$env:DISABLE_WHITELIST=1 # to load the jekyll plugins we use
bundle exec jekyll serve
```

### macOS Instructions

First, you want to get [Homebrew](https://brew.sh/), which is a package manager for macOS that installs development tools and libraries.

Follow the same steps as in the GNU/Linux guide, with the one difference being that you want to use Homebrew to install `rbenv`, by running `brew install rbenv`. The remainder of the steps should be exactly the same as on GNU/Linux.

## Contributing guide

Our development workflow uses Git, which tracks development changes so that we can easily synchronize work by multiple developers, locate any change in history, and not worry about losing work. Git relies on the concept of _branches_ and _commits_. A commit is any change: it can be anything from editing an existing file, creating a new file, to deleting a file. Commits happen on _branches_, which are like paths for commits. A quick reference to Git's many, many commands, as well as links to resources for beginners, can be found [here](https://learnxinyminutes.com/docs/git/). We host our Git repository and collaborate on [GitHub](https://github.com/), and a starting guide for GitHub can be found [here](https://docs.github.com/en/get-started/start-your-journey).

It is *strongly encouraged* to create a new branch for any new additions, via `git checkout -b my-new-branch-name`, as this will avoid [many issues](https://stackoverflow.com/questions/64369860/github-no-file-changes-but-many-commits-when-comparing-branches). Open a [pull request](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests) once you are finished making your changes and have pushed them to GitHub.

### Important contributing information

You are welcome to make pull requests (PRs) to contribute your changes to the website! We will give your PR a review, and as long as there are no issues, your changes will be accepted and added to the website. 

However, please take note that you **do not overwrite** the `Gemfile.lock`. It is easy for this to happen if you use a version of Ruby, `bundler`, or Jekyll that is different from the official versions given in this guide. The `Gemfile.lock` is important for making sure that the GitHub action builds can take place in a carefully-controlled environment, and as such, should not be modified lightly. In certain cases, such as when changing Jekyll or Ruby versions, it may be changed, but otherwise, please do not submit a commit that has overwritten it, and check that you did not accidentally commit any locally-different `Gemfile.lock`.

## Development Gotchas

Due to the nature of our development setup, there are lots of hidden surprises that may happen, and they are documented here.

- I got the error `Invalid syntax for include tag. File contains invalid characters or sequences.`
    - This is because the correct syntax is `{% include component.html param="value" %}`, with the include html path **not surrounded by quotes** (i.e. not `"component.html"`)
- My site variables are not being updated!
    - Reload the development server, open a new terminal if necessary, as Jekyll's development server does not seem to reload config files
- I am getting some variation of the error `"<command> not found"` or `"<command> is not recognized as a file, script, or operable command"`
	- Try opening a new terminal window and navigating to the natron website folder again. This reloads the shell and allows it to find any newly-installed developer tools and components

## FAQ

- Why did you use Jekyll? Why not Hugo/Next.js/Gatsby?
    - This is because Jekyll is native to GitHub, and we originally wanted to use GitHub pages' native Jekyll support, though we ended up switching to GitHub actions to reduce dependencies and use a more recent version of Jekyll
- Why is the Git repo so big?
    - We include images, brand assets and third-party binary files necessary for Natron that are not available anymore, the Jekyll site itself is relatively small
