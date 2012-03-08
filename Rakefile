# encoding: utf-8

task :default => :server

desc 'Build site with Jekyll'
task :build do # {{{
  jekyll('--rdiscount')
end # }}}

desc 'Start server with --auto'
task :server do # {{{
  jekyll('--server 4000 --auto --rdiscount --pygments')
end # }}}

desc 'Build and deploy'
task :deploy => :build do # {{{
  sh 'rsync --checksum -rtzh --progress --delete _site/ sun:/var/www/notes.remiprevost.com/'
  sh 'say -v zarvox "deploy is now complete."'
end # }}}

def jekyll(opts = '') # {{{
  sh 'rm -rf _site/*'
  sh '~/Dropbox/Bin/jekyll ' + opts
end # }}}

desc "Create a new post"
task :new do # {{{
  content = <<HERE
---
layout: post
titre: "Titre de la note"
---
HERE

  print "Entrer le slug de la note: "
  slug = STDIN.gets.chomp
  file = "_posts/#{Time.now.strftime("%y-%m-%d")}-#{slug}.mkd"
  sh "echo '#{content}' >> #{file}"
  sh "open '#{file}'"

end # }}}
