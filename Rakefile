require 'rake'

$LOAD_PATH.unshift('lib')

begin
  require 'jeweler'
  Jeweler::Tasks.new do |gem|
    gem.name = "cfbackup"
    gem.summary = "A simple ruby program intended to serve as a useful tool for automated backups to Mosso Cloud Files."
    gem.description = "A simple ruby program intended to serve as a useful tool for automated backups to Mosso Cloud Files."
    gem.email = "jon@jonsview.com"
    gem.homepage = "http://github.com/jmstacey/cfbackup"
    gem.authors = ["Jon Stacey"]
    
    # Dependencies
    gem.add_dependency('rackspace-cloudfiles', '>=1.3.0.3')

    # gem is a Gem::Specification... see http://www.rubygems.org/read/chapter/20 for additional settings
  end
rescue LoadError
  puts "Jeweler not available. Install it with: sudo gem install technicalpickles-jeweler -s http://gems.github.com"
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

task :default => :test

require 'rake/rdoctask'
Rake::RDocTask.new do |rdoc|
  if File.exist?('VERSION.yml')
    config = YAML.load(File.read('VERSION.yml'))
    version = "#{config[:major]}.#{config[:minor]}.#{config[:patch]}"
  else
    version = ""
  end

  rdoc.rdoc_dir = 'rdoc'
  rdoc.title = "cfbackup #{version}"
  rdoc.rdoc_files.include('README*')
  rdoc.rdoc_files.include('example_scripts/**')
  rdoc.rdoc_files.include('lib/**/*.rb')
end

