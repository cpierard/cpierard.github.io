source "https://rubygems.org"

# Use the GitHub Pages gem to manage compatibility
gem "github-pages", "~> 232", group: :jekyll_plugins
gem "jekyll-theme-basically-basic" # <--- Put it here

# Add any extra plugins you want here
group :jekyll_plugins do
  gem "jekyll-feed", "~> 0.12"
  gem "jekyll-leaflet"
  gem "jekyll-remote-theme" # This allows you to use almost any theme on GitHub
end

# Keep these for system compatibility
install_if -> { RUBY_PLATFORM =~ %r!mingw|mswin|java! } do
  gem "tzinfo", "~> 1.2"
  gem "tzinfo-data"
end
gem "wdm", "~> 0.1.1", :install_if => Gem.win_platform?

gem "bigdecimal", "~> 4.1"

gem "webrick", "~> 1.9"
gem "logger", "~> 1.7"
