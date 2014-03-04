# encoding: utf-8
require 'bundler/gem_tasks'
require 'yard'
require 'rake/testtask'
require 'cucumber'
require 'cucumber/rake/task'

Rake::TestTask.new(:test) do |test|
  test.libs << 'lib' << 'test'
  test.pattern = 'test/**/test_*.rb'
  test.verbose = true
end

Cucumber::Rake::Task.new(:features) do |t|
  t.cucumber_opts = "--format pretty"
end

YARD::Rake::YardocTask.new do |t|
  %x(mkdir ~/.yard) unless File.exists? File.expand_path('~/.yard')
  %x(yard config load_plugins true)

  t.files = %w[lib/**/*.rb features/**/*.feature features/**/*.rb - README.md]
  t.options = %w(-M kramdown --output-dir /Users/tiagonobre/Downloads/jira-rest/jira-rest.wiki)
end

task :default => :features

task :default => :test