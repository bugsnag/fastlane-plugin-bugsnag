source 'https://rubygems.org'

gemspec

# Any :development dependencies are ignored for license auditing purposes
group :development do
end

# Any :test dependencies are ignored for license auditing purposes
group :test do
  if RUBY_PLATFORM =~ /darwin/
    gem 'bugsnag-maze-runner', '~>10.0'
  end
end


plugins_path = File.join(File.dirname(__FILE__), 'fastlane', 'Pluginfile')
eval_gemfile(plugins_path) if File.exist?(plugins_path)
