require 'rubygems'
require 'rake/gempackagetask'
require 'rubygems/specification'
require 'date'
require 'merb-core/version'
require 'merb-core/tasks/merb_rake_helper'

NAME = "merb-ar-stack"
AUTHOR = "Merb Team"
EMAIL = "team@merbivore.com"
HOMEPAGE = "http://merbivore.com/"
SUMMARY = "(merb-core + merb-more + AR) == Merb ActiveRecord stack"

# For RubyForge release task
RUBY_FORGE_PROJECT  = "merb-ar-stack"
PROJECT_URL         = HOMEPAGE
PROJECT_SUMMARY     = SUMMARY
PROJECT_DESCRIPTION = SUMMARY

GEM_AUTHOR = AUTHOR
GEM_EMAIL  = EMAIL

GEM_NAME    = NAME
PKG_BUILD   = ENV['PKG_BUILD'] ? '.' + ENV['PKG_BUILD'] : ''
GEM_VERSION = Merb::VERSION  + PKG_BUILD

RELEASE_NAME    = "REL #{GEM_VERSION}"

gems = [
  ["merb-core", "~> #{GEM_VERSION}"],
  ["merb-more", "~> #{GEM_VERSION}"],
  ["activerecord", "~> 2.1.0"]
]

merb_spec = Gem::Specification.new do |s|
  s.rubyforge_project = 'merb-ar-stack'
  s.name         = NAME
  s.version      = GEM_VERSION
  s.platform     = Gem::Platform::RUBY
  s.author       = AUTHOR
  s.email        = EMAIL
  s.homepage     = HOMEPAGE
  s.summary      = SUMMARY
  s.description  = SUMMARY
  s.files        = %w(LICENSE README Rakefile Generators) + Dir.glob("{lib}/**/*")
  gems.each do |gem, version|
    s.add_dependency gem, version
  end
end

Rake::GemPackageTask.new(merb_spec) do |pkg|
  pkg.gem_spec = merb_spec
end

desc "Install the gem"
task :install do
  Merb::RakeHelper.install(GEM_NAME, :version => GEM_VERSION)
end

desc "Uninstall the gem"
task :uninstall do
  Merb::RakeHelper.uninstall(GEM_NAME, :version => GEM_VERSION)
end

desc "create a gemspec file"
task :make_spec do
  File.open("#{NAME}.gemspec", "w") do |file|
    file.puts spec.to_ruby
  end
end
