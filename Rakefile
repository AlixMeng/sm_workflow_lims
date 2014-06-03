require "sinatra/activerecord/rake"

namespace :db do
  task :load_config do
    require "./app"
  end
end

namespace :build do
  task :manifest do
    puts "Building manifest!"
    File.open('./app/manifest.rb','w') do |file|
      `git ls-files app | grep -e [\.]rb`.split.each do |req|
        next if req == 'app/manifest.rb'
        file.puts "require './#{req.gsub(/\.rb$/,'')}'"
        print '.'
      end
    end
    puts '.'
    puts 'Manifest Built:'
    puts `cat ./app/manifest.rb`
  end
end

# Rakefile
APP_FILE  = './app.rb'
APP_CLASS = 'SmWorkflowLims'

require 'sinatra/assetpack/rake'
