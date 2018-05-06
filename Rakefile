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

task :ship do
  rsync = %x(sudo rsync -avz -e "ssh -o StrictHostKeyChecking=no -o UserKnownHostsFile=/dev/null" --delete --progress $HOME/code/rioos/ruby/docs.rioos.xyz/_site/ 198.211.117.129:/var/www/rio.digital/html/abcd/)
  puts rsync
  puts "✔ Shipped"
end
