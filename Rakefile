# Taken from http://blog.karlswedberg.com/Rakefile/
# Adapted from Scott Kyle's Rakefile
# http://github.com/appden/appden.github.com/blob/master/Rakefile

task :default => :server

desc 'Build CV to PDF with pandoc'
task :cv  => [:build] do
	sh 'pandoc _site/cv/cv.md -o _site/cv/cv.pdf'
end

desc 'Build site with Jekyll'
task :build do  
  sh 'jekyll build' 
end

desc 'Build and deploy'
task :deploy => [:build, :cv] do
  sh 'rsync -a --delete --delay-updates --progress -e "ssh -p 232" _site/ morgan@roderick.dk:/dana/data/www.roderick.dk/docs/'
end

def jekyll(opts = '')
  sh 'rm -rf _site'
  sh 'jekyll ' + opts
end