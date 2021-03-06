require 'rubygems'
require 'rake'

begin
  require 'jeweler'
  Jeweler::Tasks.new do |gem|
    gem.name = "deactivatable"
    gem.summary = %Q{Adds methods and scopes to ActiveRecord objects to allow deactivation instead of deletion.}
    gem.description = %Q{Deactivatable provides methods and a default_scope to allow ActiveRecord objects to be deactivated instead of deleted.
      This is useful if an object needs to be removed from general use, but it's data needs to be retained.
      Additionally, Deactivatable provides the ability to specify dependencies which also need to be deactivated.
      Deactivation is determined by populating a deactivated_at field with the date time at which deactivation happened.
    }
    gem.email = "greg_fitz@yahoo.com"
    gem.homepage = "http://github.com/gregfitz23/deactivatable"
    gem.authors = ["Greg Fitzgerald"]
    gem.add_dependency "active_record", ">= 3.1"
    gem.add_development_dependency "thoughtbot-shoulda"

    # gem is a Gem::Specification... see http://www.rubygems.org/read/chapter/20 for additional settings
  end
rescue LoadError
  puts "Jeweler (or a dependency) not available. Install it with: sudo gem install jeweler"
end

require 'rake/testtask'
Rake::TestTask.new(:test) do |test|
  test.libs << 'lib' << 'test'
  test.pattern = 'test/**/*_test.rb'
  test.verbose = true
end

begin
  require 'rcov/rcovtask'
  Rcov::RcovTask.new do |test|
    test.libs << 'test'
    test.pattern = 'test/**/*_test.rb'
    test.verbose = true
  end
rescue LoadError
  task :rcov do
    abort "RCov is not available. In order to run rcov, you must: sudo gem install spicycode-rcov"
  end
end

task :test => :check_dependencies

task :default => :test

require 'rake/rdoctask'
Rake::RDocTask.new do |rdoc|
  if File.exist?('VERSION')
    version = File.read('VERSION')
  else
    version = ""
  end

  rdoc.rdoc_dir = 'rdoc'
  rdoc.title = "deactivatable #{version}"
  rdoc.rdoc_files.include('README*')
  rdoc.rdoc_files.include('lib/**/*.rb')
end
