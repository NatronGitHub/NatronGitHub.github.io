# NatronGitHub.github.io
Natron's New Website!

## Building for Development

## Development
This website uses Jekyll, get that [here](https://jekyllrb.com/).

`cd` to the git repo

`bundle install` to install all the dependencies

`bundle exec jekyll serve` to start Jekyll @ localhost:4000

Navigate to localhost:4000 in the browser and get going!

## Development Guidelines

### Classes

Name classes that are page specific with the following format:

`pageprefex-previousclass-classname`

Example:

`index-featurecards-cardbody`

### Tabs

Use em.  Keep indenting clean and follow the existing standards of the files.

### Relative Links

Jekyll is a static site generator and relative file URLs don't really work unless you hardcode them which requires thinking and doesn't work for stuff like navigation.  To fix this there is a file called `baseurl.html` that tells Jekyll how to link things nicely and relatively!  Place `{{base}}` directly before any link that links to a resource inside the website and refer to this resource as a path straight from the home directly.  Think of it as automatically handling the `../`'s for you... because that's exactly what it's doing!  For more information see [this website](https://ricostacruz.com/til/relative-paths-in-jekyll).

### SVGs & Colours In General

All colours are referenced as both P3 and an sRGB fallback.  Variables can be found and set in `_sass/_global.scss`.

SVGs can only have their colours set with variables if they exist in the DOM.  This matters most for SVGs set to our brand colours & 100% white.  If the SVG is not using these colours _it doesn't have to be embedded!_  Otherwise, it should be.