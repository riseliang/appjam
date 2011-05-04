require 'rubygems'
require 'bundler'

begin
  Bundler.setup(:default, :development)
rescue Bundler::BundlerError => e
  $stderr.puts e.message
  $stderr.puts "Run `bundle install` to install missing gems"
  exit e.status_code
end
require 'rake'
require './lib/appjam/version.rb'
require './lib/appjam/tasks.rb'

Appjam::Tasks.files.each  { |ext| load(ext) }

require 'jeweler'
Jeweler::Tasks.new do |gem|
  # gem is a Gem::Specification... see http://docs.rubygems.org/read/chapter/20 for more options
  gem.name = "appjam"
  gem.homepage = "http://github.com/eiffelqiu/appjam"
  gem.license = "MIT"
  gem.summary = %Q{an iphone app generator}
  gem.description = %Q{generate iphone app skeleton based on pure mvc framework}
  gem.email = "eiffelqiu@gmail.com"
  gem.authors = ["Eiffel Q"]
  gem.version = Appjam::Version::STRING
  gem.executables = ['appjam']
  gem.files = Dir.glob('lib/**/*.*')
  gem.add_dependency 'activesupport'
  gem.add_dependency 'grit'
  gem.add_dependency 'i18n'
end
Jeweler::RubygemsDotOrgTasks.new
Jeweler::GemcutterTasks.new

require 'rake/testtask'
Rake::TestTask.new(:test) do |test|
  test.libs << 'lib' << 'test'
  test.pattern = 'test/**/test_*.rb'
  test.verbose = true
end

require 'rcov/rcovtask'
Rcov::RcovTask.new do |test|
  test.libs << 'test'
  test.pattern = 'test/**/test_*.rb'
  test.verbose = true
end

task :default => :test

require 'rake/rdoctask'
Rake::RDocTask.new do |rdoc|
  version = File.exist?('VERSION') ? File.read('VERSION') : ""

  rdoc.rdoc_dir = 'rdoc'
  rdoc.title = "hello #{version}"
  rdoc.rdoc_files.include('README*')
  rdoc.rdoc_files.include('lib/**/*.rb')
end
