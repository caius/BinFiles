BINDIR = "#{ENV["HOME"]}/bin"
SOURCE_FILES = Rake::FileList.new("**/*") do |fl|
  fl.exclude { |f| ! File.executable?(f) }
  fl.exclude { |f| `git ls-files "#{f}"`.empty? }
end

desc "Link all executables into ~/bin"
task :link => SOURCE_FILES.pathmap("#{BINDIR}/%p")

task :create_bin do
  mkdir_p BINDIR
end

SOURCE_FILES.pathmap("#{BINDIR}/%p").each do |destination|
  file destination => :create_bin do |t|
    sh "ln", "-sf", File.expand_path(t.name.pathmap("%f")), t.name
  end
end

task :default => :link
