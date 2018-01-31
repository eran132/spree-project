# Add your own tasks in files placed in lib/tasks ending in .rake,
# for example lib/tasks/capistrano.rake, and they will automatically be available to Rake.

#require_relative 'config/application'
#
#Rails.application.load_tasks
#
require 'open3'


desc "Archive files"
task :archive do
  path = ENV['MYPATH']
  exclude_files = ENV['EXCLUDE']

  archive_name = path.pathmap("%n")
  build_dir = path + "/build"

  puts "===archiving==="
  puts "===excluding #{exclude_files}==="
  sh "tar cvzf #{archive_name}.tar.gz #{path} --exclude='#{exclude_files}'"

  puts "===removing previous version==="
  if Dir.exists?(build_dir)
    puts "===#{build_dir} exists==="
    rm_r "#{build_dir}"
  end

  puts "===creating #{build_dir}==="
    sh "mkdir #{build_dir}"

  puts "===moving tar.gz file to #{build_dir}==="
  sh "mv #{archive_name}.tar.gz #{build_dir}/"
end

