# frozen_string_literal: true

source "https://rubygems.org"

git_source(:github) {|repo_name| "https://github.com/NatronGitHub/NatronGitHub.github.io" }

gem "jekyll", "~> 3.9"
gem "kramdown-parser-gfm"
# Explicitly specify Jekyll plugins
group :jekyll_plugins do
    gem "jekyll-feed"
    gem "jekyll-redirect-from"
    gem "jekyll-relative-urls"
end

# For compatibility with ruby v3+
gem "webrick", "~> 1.7"
