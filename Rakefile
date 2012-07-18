dir = ENV['RBX']

task :default => :sync

task :sync do
  if !dir or !File.directory?(dir)
    puts "Please set the RBX variable"
    fail
  end

  Dir.mkdir "public" unless File.directory? "public"

  sh "rsync -r #{dir}/web/_site/ public/"

  version = Dir.chdir(dir) { `git log --pretty=oneline -1`[0..7] }
  sh "git commit -m 'Updated website to Rubinius #{version}.' -a"
end
