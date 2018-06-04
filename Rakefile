task :default => %w[clean]

task :clean do
  %x(jekyll clean)
  %x(JEKYLL_ENV=production bundle exec jekyll build)
  puts "✔ Built"
end

task :local => :clean do
  %x(sudo rsync -avz -e "ssh -o StrictHostKeyChecking=no -o UserKnownHostsFile=/dev/null" --delete --progress $HOME/code/rioos/ruby/docs.rioos.xyz/_site/ /usr/share/nginx/html/docs/)
  puts "✔ Local done"
end

task :ship => :clean do
  rsync = %x(sudo rsync -avz -e "ssh -o StrictHostKeyChecking=no -o UserKnownHostsFile=/dev/null" --delete --progress $HOME/code/rioos/ruby/docs.rioos.xyz/_site/ 159.65.224.176:/var/www/rio.digital/htdocs/docs/)
  puts rsync
  puts "✔ Shipped done"
end
