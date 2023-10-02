source ENV['GEM_SOURCE'] || 'https://rubygems.org'

def location_for(place, fake_version = nil)
  if place =~ %r{^(git[:@][^#]*)#(.*)}
    [fake_version, { git: Regexp.last_match(1), branch: Regexp.last_match(2), require: false }].compact
  elsif place =~ /^file:\/\/(.*)/
    ['>= 0', { path: File.expand_path(Regexp.last_match(1)), require: false }]
  else
    [place, { require: false }]
  end
end

# The development group is intended for developer tooling. CI will never install this.
group :development do
end

group :test do
  # Require the latest Puppet by default unless a specific version was requested
  # CI will typically set it to '~> 7.0' to get 7.x
  gem 'puppet', ENV['PUPPET_GEM_VERSION'] || '>= 0', require: false
  # Needed to build the test matrix based on metadata
  gem 'puppet_metadata', '~> 1.10',  require: false
  # Needed for the rake tasks
  gem 'puppetlabs_spec_helper', '>= 2.16.0', '< 5', require: false
  # Rubocop versions are also specific so it's recommended
  # to be precise. Can be turned off via a parameter
  gem 'rubocop', require: false

#  gem 'metadata-json-lint',                                         require: false
#  gem 'puppet-blacksmith',                                          require: false, git: 'https://github.com/voxpupuli/puppet-blacksmith.git'
#  gem 'puppet-lint',                                                require: false, git: 'https://github.com/rodjek/puppet-lint.git'
#  gem 'puppet-lint-absolute_classname-check',                       require: false
#  gem 'puppet-lint-classes_and_types_beginning_with_digits-check',  require: false
#  gem 'puppet-lint-leading_zero-check',                             require: false
#  gem 'puppet-lint-trailing_comma-check',                           require: false
#  gem 'puppet-lint-unquoted_string-check',                          require: false
#  gem 'puppet-lint-variable_contains_upcase',                       require: false
#  gem 'puppet-lint-version_comparison-check',                       require: false
#  gem 'puppet-strings',                                             require: false
#  gem 'puppet-syntax',                                              require: false
#  gem 'puppetlabs_spec_helper',                                     require: false
#  gem 'semantic_puppet',                                            require: false
#  gem 'rake',                                                       require: false
#  gem 'rspec',                                                      require: false
#  gem 'rspec-core',                                                 require: false
#  gem 'rspec-puppet',                                               require: false, git: 'https://github.com/puppetlabs/rspec-puppet.git'
#  gem 'rspec-puppet-facts',                                         require: false
#  gem 'rspec-puppet-utils',                                         require: false
#  gem 'rubocop',                                                    require: false
#  gem 'rubocop-rspec',                                              require: false
#  gem 'voxpupuli-release',                                          require: false, git: 'https://github.com/voxpupuli/voxpupuli-release-gem.git'
end

# The system_tests group is used in gha-puppet's beaker workflow.
# Consider using https://github.com/voxpupuli/voxpupuli-acceptance
group :system_tests do
  gem 'beaker', require: false
  gem 'beaker-docker', require: false
  gem 'beaker-rspec', require: false
end

# The release group is used in gha-puppet's release workflow
# Consider using https://github.com/voxpupuli/voxpupuli-release
group :release do
  gem 'puppet-blacksmith', '~> 6.0', require: false
end

# group :development do
#   gem 'guard-rake',   require: false
# end
# 
# if RUBY_VERSION >= '2.3.0'
#   group :acceptance do
#     gem 'beaker'
#     gem 'beaker-puppet_install_helper'
#     gem 'beaker-puppet'
#     gem 'beaker-docker'
#     gem 'beaker-rspec'
#   end
# end
# 
# if facterversion = ENV['FACTER_GEM_VERSION']
#   gem 'facter', facterversion.to_s, require: false, groups: [:test]
# else
#   gem 'facter', require: false, groups: [:test]
# end
# 
# puppetversion = ENV['PUPPET_VERSION'].nil? ? '~> 7' : ENV['PUPPET_VERSION'].to_s
# gem 'puppet', puppetversion, require: false, groups: [:test]

# vim:ft=ruby
