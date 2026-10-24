source "https://rubygems.org"

# The live site is built by GitHub Pages' own builder, which ignores this file
# and uses fixed versions (Jekyll 3.10, minima 2.5, an allowlist of plugins).
# The "github-pages" gem pins those exact versions, so a local build matches
# the live site. Check https://pages.github.com/versions/ and bump this when
# GitHub does.
gem "github-pages", "~> 232", group: :jekyll_plugins

# Ruby 3 no longer bundles the web server that "jekyll serve" needs.
gem "webrick", "~> 1.8"

# Windows needs timezone data (GitHub's Linux builder has it built in).
platforms :windows do
  gem "tzinfo-data"
end
