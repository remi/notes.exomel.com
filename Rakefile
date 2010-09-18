# Adopted from Scott Kyle and Tate Johnson’s Rakefiles
# http://github.com/appden/appden.github.com/blob/master/Rakefile
# http://github.com/tatey/tatey.com/blob/master/Rakefile

task :default => :server

desc 'Build site with Jekyll'
task :build do
  jekyll('--rdiscount')
end

desc 'Start server with --auto'
task :server do
  jekyll('--server 4000 --auto --rdiscount --pygments')
end

desc 'Build and deploy'
task :deploy => :build do
  sh 'rsync --checksum -rtzh --progress --delete _site/ sun:/var/www/notes.remiprevost.com/'
  sh 'say -v zarvox "deploy is now complete."'
end

def jekyll(opts = '')
  sh 'rm -rf _site/*'
  sh 'jekyll ' + opts
end
