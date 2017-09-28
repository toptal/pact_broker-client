require "bundler/gem_tasks"
require 'rspec/core/rake_task'
require 'conventional_changelog'

Dir.glob('lib/tasks/**/*.rake').each { |task| load "#{Dir.pwd}/#{task}" }
Dir.glob('tasks/**/*.rake').each { |task| load "#{Dir.pwd}/#{task}" }
RSpec::Core::RakeTask.new(:spec) do | task |
  task.rspec_opts = "--pattern spec/lib/**/*_spec.rb"
end

RSpec::Core::RakeTask.new('spec:providers') do | task |
  task.rspec_opts = "--pattern spec/service_providers/**/*_spec.rb"
end

task :default => [:spec, 'spec:providers']

task :generate_changelog do
  require 'pact_broker/client/version'
  ConventionalChangelog::Generator.new.generate! version: "v#{PactBroker::Client::VERSION}"
end
