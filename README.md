# Natron's Website

![Repo Size](https://img.shields.io/github/repo-size/shrinks99/NatronGitHub.github.io)![GPL 2 License](https://img.shields.io/badge/license-GPL%202-green) ![W3C Validation](https://img.shields.io/w3c-validation/html?targetUrl=https%3A%2F%2Fwilkinson.graphics%2FNatronGitHub.github.io%2F)![Website Live](https://img.shields.io/website?url=https%3A%2F%2Fimg.shields.io%2Fw3c-validation%2Fhtml%3FtargetUrl%3Dhttps%253A%252F%252Fwilkinson.graphics%252FNatronGitHub.github.io%252F)![Last Commit Date](https://img.shields.io/github/last-commit/shrinks99/NatronGitHub.github.io)

## Development

We're open to any contributions! To contribute, make sure you have a decent grasp of these things (or have a willingness to learn them!):

* The command line
* Web design
* HTML/CSS and [SCSS](https://sass-lang.com/)
* Some prior experience with [Jekyll](https://jekyllrb.com/)

Note that if you're a beginner programmer and this is your first time working on an open-source project, we advise you to read [the detailed development guide](DEVELOP.md). The guide is also helpful if you encounter issues in the setup process. The process described below assumes a pre-existing knowledge of version control systems and Jekyll in general. If that's ok with you, follow these steps to quickly get started:

### Getting Dependencies

Make sure you have `git` already installed. This website also requires Jekyll, a static site generator we use to generate markup from templates. Installing Jekyll is generally a variation of these steps:

* Step 1: Install `rbenv` via `brew install rbenv` on macOS with [Homebrew](https://brew.sh/) installed, `sudo apt install rbenv` on Debian Linux distros, `yay -S rbenv` on Arch-based distros, or compiling manually from its sources at <https://github.com/rbenv/rbenv>. For Windows, follow the instructions for [rbenv for Windows](https://github.com/ccmywish/rbenv-for-windows), just **making sure** to substitute `$env:RBENV_ROOT = "$HOME\Ruby-on-Windows"` wherever it is mentioned.
* Step 2: Run `rbenv init` and open a new terminal (you may not _have_ to do this depending on your system and terminal setup, but it's recommended)
* Step 3: Run the command `rbenv install 3.3.3` and then `rbenv global 3.3.3` (other versions of Ruby _may_ work but are untested and may break things). This is *usually* not necessary on Windows (it auto-installs) but if the next step(s) don't work, run the aforementioned command and try again
	* Be aware that this may take a while (~5 min. depending on your internet connection)
	* On windows, this assumes you have 7-Zip installed and on your PATH. Read the [detailed developer guide](DEVELOP.md) otherwise. 
* Step 4: Now, open a **new** terminal again, and run `gem install bundler` - this gives you access to the `bundle` command which (confusingly) is what installs Jekyll!

## Building With Jekyll

Navigate to your directory of choice with `cd /path/of/choice`, then run this command to download the repo:

```bash
git clone https://github.com/Shrinks99/NatronGitHub.github.io && cd NatronGitHub.github.io
```

Build with Jekyll in three steps:

* `bundle install` to install all the dependencies - this may take quite a while! Windows users may need to run this in a Powershell session with **administrator permissions**
* `bundle exec jekyll build` to build the site
* `bundle exec jekyll serve --incremental` to start Jekyll at <http://localhost:4000>

Navigate to <http://localhost:4000> in the browser and get going!

## Development Guidelines

### Classes

Name classes that are page specific with the following format:

`pageprefex-previousclass-classname`

Example:

`index-featurecards-cardbody`

Globally styled containers don't need to be mentioned in these names.

### Indenting & Code Styling

Keep indenting clean and follow the existing standards of the files.

### Relative Links

Jekyll is a static site generator and relative file URLs don't really work unless you hardcode them which requires thinking and doesn't work for stuff like navigation.  To fix this there is a file called `baseurl.html` that tells Jekyll how to link things nicely and relatively!  Place `{% base %}` directly before any link that links to a resource inside the website and refer to this resource as a path straight from the home directly.  Think of it as automatically handling the `../`'s for you... because that's exactly what it's doing!  For more information see [this website](https://ricostacruz.com/til/relative-paths-in-jekyll).

### SVGs & Colors In General

All color variables are referenced as both P3 and an sRGB fallback.  Variables can be found and set in `_sass/_global.scss`.

SVGs can only have their colors set with variables if they exist in the DOM.  This matters most for SVGs set to our brand colors & 100% white.  If the SVG is not using these colors _it doesn't have to be embedded!_  Otherwise, it should be.

### Authoring an Update Post

After building and setting up the release through GitHub Releases...

1. Create a standard release graphic: Natron project file and instructions on how to do this are available in the releasegraphic folder in `/templates`.  Place the generated image in `/img/news/releases`.
2. Author an update post: Markdown template also available in `/templates`, be sure to change the relevant info in both the file name and the front matter section, most of the body text can be copied from the GitHub `CHANGELOG.md`, please include any extra information about the release before the "Major Changes" section.
3. Change the download links by setting the variables in `_config.yml`.
4. Publish to main!  Bonus points for testing the site locally first ;)

## Licensing

Websites are tricky, licensing is mixed.

- Our website _code_ is licensed under the [GPL V2](https://www.gnu.org/licenses/old-licenses/gpl-2.0-standalone.html)
- Our website _content_ is licensed under a [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) license
- [Inter](https://github.com/rsms/inter) (our primary font) is licensed under the [SIL Open Font License](https://github.com/rsms/inter/blob/master/LICENSE.txt).
- [BoxIcons](https://github.com/atisawd/boxicons) is licensed under [CC-BY 4.0](https://creativecommons.org/licenses/by/4.0/).
- [Sass MQ](https://github.com/sass-mq/sass-mq) is licensed under the [MIT License](https://github.com/sass-mq/sass-mq/blob/master/LICENSE.md).
