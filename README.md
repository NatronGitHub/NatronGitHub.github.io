# Natron's Redesigned Website

![Repo Size](https://img.shields.io/github/repo-size/shrinks99/NatronGitHub.github.io)![GPL 2 License](https://img.shields.io/badge/license-GPL%202-green) ![W3C Validation](https://img.shields.io/w3c-validation/html?targetUrl=https%3A%2F%2Fwilkinson.graphics%2FNatronGitHub.github.io%2F)![Website Live](https://img.shields.io/website?url=https%3A%2F%2Fimg.shields.io%2Fw3c-validation%2Fhtml%3FtargetUrl%3Dhttps%253A%252F%252Fwilkinson.graphics%252FNatronGitHub.github.io%252F)![Last Commit Date](https://img.shields.io/github/last-commit/shrinks99/NatronGitHub.github.io)

Natron's new website! See it live at <https://wilkinson.graphics/NatronGitHub.github.io/>.

## Development

We're open to any contributions! To contribute, make sure you have a decent grasp of these things:

* The command line
* Web design
* HTML/CSS and SCSS
* Some prior experience with Jekyll

Follow these steps to quickly get started:

### Getting Dependencies

Firstly, make sure you have `git` installed. If you are using macOS or GNU/Linux, you likely already have it installed; Windows users can download and run the installer from [its official download page](https://git-scm.com/download/). Check that you have `git` correctly installed by running this on Mac/Linux:

```bash
if type git &> /dev/null; then echo Git installed!; else echo Git not installed.; fi
```

Or this on Windows:

```powershell
where git; if %errorlevel% neq 0 echo git is not installed.
```

This website also requires Jekyll, a static site generator we use to generate markup from templates. Installing Jekyll should be quick and easy:

* Step 1: Install `rbenv` via `brew install rbenv` on Macs, `sudo apt install rbenv` on Debian Linux distros, `yay -S rbenv` on Arch-based distros, or compiling manually from its sources at <https://github.com/rbenv/rbenv>
* Step 2: Run `rbenv init` and open a new terminal
* Step 3: Run the command `rbenv install 2.6.3 && rbenv global 2.6.3`
* Step 4: Now, open a new terminal again, and run `gem install bundler && bundler install bundler` - this gives you access to the `bundle` command which (confusingly) is what installs Jekyll!

## Building With Jekyll

Now, get the sources of the website:

```bash
git clone https://github.com/Shrinks99/NatronGitHub.github.io && cd NatronGitHub.github.io
```

Build with Jekyll in two steps:

* `bundle install` to install all the dependencies
* `bundle exec jekyll serve` to start Jekyll at <http://localhost:4000>

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

Jekyll is a static site generator and relative file URLs don't really work unless you hardcode them which requires thinking and doesn't work for stuff like navigation.  To fix this there is a file called `baseurl.html` that tells Jekyll how to link things nicely and relatively!  Place `{{base}}` directly before any link that links to a resource inside the website and refer to this resource as a path straight from the home directly.  Think of it as automatically handling the `../`'s for you... because that's exactly what it's doing!  For more information see [this website](https://ricostacruz.com/til/relative-paths-in-jekyll).

### SVGs & Colours In General

All colour variables are referenced as both P3 and an sRGB fallback.  Variables can be found and set in `_sass/_global.scss`.

SVGs can only have their colours set with variables if they exist in the DOM.  This matters most for SVGs set to our brand colours & 100% white.  If the SVG is not using these colours _it doesn't have to be embedded!_  Otherwise, it should be.

## Licensing

Websites are tricky, licensing is mixed.

- Our website _code_ is licensed under the [GPL V2](https://www.gnu.org/licenses/old-licenses/gpl-2.0-standalone.html)
- Our website _content_ is licensed under something to be determined!
- [Inter](https://github.com/rsms/inter) (our primary font) is licensed under the [SIL Open Font License](https://github.com/rsms/inter/blob/master/LICENSE.txt).
- [BoxIcons](https://github.com/atisawd/boxicons) is licensed under [CC-BY 4.0](https://creativecommons.org/licenses/by/4.0/).
- [Sass MQ](https://github.com/sass-mq/sass-mq) is licensed under the [MIT License](https://github.com/sass-mq/sass-mq/blob/master/LICENSE.md).
