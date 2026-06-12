# Gems used to build the site. The GitHub Actions workflow installs these and runs
# `bundle exec jekyll build`. The same Gemfile drives local preview:
#   bundle exec jekyll serve --baseurl ""

source "https://rubygems.org"

gem "jekyll", "~> 4.3"
gem "minima", "~> 2.5"

# Plugins must be listed explicitly outside GitHub's legacy build, which is what
# turns the plain Markdown into a navigable site.
group :jekyll_plugins do
  gem "jekyll-relative-links"        # rewrite .md links to their built .html URLs
  gem "jekyll-optional-front-matter" # render Markdown that has no YAML front matter
  gem "jekyll-readme-index"          # serve README.md as the site homepage
  gem "jekyll-default-layout"        # apply the theme layout without per-file declarations
  gem "jekyll-titles-from-headings"  # derive each page <title> from its first heading
end
