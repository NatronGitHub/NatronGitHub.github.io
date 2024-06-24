# Getting started with developing Natron's website

Natron's website uses Jekyll, a static site generator. It usually saves us a lot of time reduces our trouble, but we know it can be confusing to many newer developers and get *them* in lots of trouble. So, here is a reliable means of developing Natron's website for Mac users, Windows users, and GNU/Linux users!

If you run into any issues, look at the FAQ and common build problems section at the bottom of this guide.

## Prerequisites for all operating systems

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

## GNU/Linux Instructions

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

Now open another powershell terminal, and rbenv should automatically start downloading the Ruby toolchain. If it does not, run:

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

## macOS Instructions

First, you want to get [Homebrew](https://brew.sh/), which is a package manager for macOS that installs development tools and libraries.

Instructions will be fleshed-out in time, but for now, follow the same steps as in the GNU/Linux guide, with the one difference being that you want to use Homebrew to install `rbenv`, by running `brew install rbenv`. The remainder of the steps should be exactly the same as on GNU/Linux.