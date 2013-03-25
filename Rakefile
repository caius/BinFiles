task :default => :install

task :install do
  Dir["**/*"].each do |file|
    next if file[/readme\.md/i] || file["Rakefile"]
    sh "ln", "-sf", "#{Dir.pwd}/#{file}", "#{ENV["HOME"]}/bin/#{file}"
  end
end
