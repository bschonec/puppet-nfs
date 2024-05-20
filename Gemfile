source 'https://rubygems.org'

# The development group is intended for developer tooling. CI will never install this.
group :development do
end

# The test group is used for static validations and unit tests in gha-puppet's
# basic and beaker gha-puppet workflows.
group :test do
  # Require the latest Puppet by default unless a specific version was requested
  # CI will typically set it to '~> 7.0' to get 7.x
  gem 'puppet', ENV.fetch('PUPPET_GEM_VERSION', '>= 0'), require: false
  # Needed to build the test matrix based on metadata
  gem 'puppet_metadata', '~> 3.2',  require: false
  # metagem that pulls in all further requirements
  gem 'voxpupuli-test', '~> 7.0', require: false
end

# The system_tests group is used in gha-puppet's beaker workflow.
group :system_tests do
  gem 'voxpupuli-acceptance', '~> 2.1', require: false
end

# The release group is used in gha-puppet's release workflow
group :release do
  gem 'voxpupuli-release', '~> 3.0', '>= 3.0.1'
end
