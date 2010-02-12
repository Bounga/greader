begin
  require 'rubygems'
  require 'rake/gempackagetask'
rescue Exception
  nil
end

require 'rake/clean'
require 'rake/testtask'
require 'rake/rdoctask'

require './lib/greader'

desc 'Run tests'
task :default => :test

Rake::RDocTask.new do |rd|
    rd.title    = 'GReader'
    rd.options << '--line-numbers' << '--inline-source'
    rd.main = "README.rdoc"
    rd.rdoc_files.include("README.rdoc", "lib/**/*.rb")
end

spec = Gem::Specification.new do |s| 
  s.name = "GReader"
  s.version = Greader::VERSION
  s.author = "Nicolas Cavigneaux"
  s.email = "nico@bounga.org"
  s.homepage = "http://bitbucket.org/Bounga/greader/"
  s.platform = Gem::Platform::RUBY
  s.summary = "Google Reader API"
  s.description = "Google Reader API"
  s.files = FileList["{bin,lib}/**/*"].to_a
  s.require_path = "lib"
  s.autorequire = "greader"
  s.test_files = FileList["{test}/**/*test.rb"].to_a
  s.has_rdoc = true
  s.extra_rdoc_files = ["README"]
end

Rake::GemPackageTask.new(spec) do |pkg|
  pkg.need_zip = false
  pkg.need_tar_bz2 = false
end

Rake::TestTask.new(:test) do |t|
  t.libs << 'lib'
  t.test_files = FileList['test/**/*_test.rb']
  t.verbose = true
end