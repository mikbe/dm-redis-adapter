require 'rubygems'
require 'rake/gempackagetask'
require 'rubygems/specification'
require 'date'
require 'spec/rake/spectask'

GEM = 'dm-redis-adapter'
GEM_NAME = 'dm-redis-adapter'
GEM_VERSION = '0.0.4'
AUTHORS = ['Dan Herrera']
EMAIL = "whoahbot@gmail.com"
HOMEPAGE = "http://github.com/whoahbot/dm-redis-adapter"
SUMMARY = "DataMapper adapter for the Redis key-value database"

spec = Gem::Specification.new do |s|
  s.name = GEM
  s.version = GEM_VERSION
  s.platform = Gem::Platform::RUBY
  s.has_rdoc = true
  s.extra_rdoc_files = ["MIT-LICENSE"]
  s.summary = SUMMARY
  s.description = s.summary
  s.authors = AUTHORS
  s.email = EMAIL
  s.homepage = HOMEPAGE
  s.add_dependency "rspec"
  s.add_dependency "dm-core", "0.10.0"
  s.add_dependency "redis",   "0.0.3.4"
  s.require_path = 'lib'
  s.autorequire = GEM
  s.files = %w(MIT-LICENSE README.textile Rakefile) + Dir.glob("{lib,spec}/**/*")
end

task :default => :spec

desc "Run specs"
Spec::Rake::SpecTask.new do |t|
  t.spec_files = FileList['spec/**/*_spec.rb']
  t.spec_opts = %w(-fs --color)
end

Rake::GemPackageTask.new(spec) do |pkg|
  pkg.gem_spec = spec
end

desc "install the gem locally"
task :install => [:package] do
  sh %{sudo gem install pkg/#{GEM}-#{GEM_VERSION}}
end

desc "create a gemspec file"
task :make_spec do
  File.open("#{GEM}.gemspec", "w") do |file|
    file.puts spec.to_ruby
  end
end