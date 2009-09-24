SCRIPTS_DIR = "#{ENV['HOME']}/Library/Scripts"
APPLICATIONS = ["Adium", "Chax", "Emacs", "Finder", "Firefox", "Mailplane",
                "PandoraJam", "Safari", "Skitch", "Terminal", "Tweetie"]

def compile(file, source)
  sh "arch -i386 osacompile -d -o '#{file}' -e '#{source}'"
end

def hide_extension(file)
  sh "test -e /usr/bin/setfile && /usr/bin/setfile -a E '#{file}'"
end

def install_scripts(directory)
  source_dir  = directory
  install_dir = "#{SCRIPTS_DIR}/#{directory}"

  mkdir_p install_dir
  cp Dir["#{source_dir}/*.scpt"], install_dir
  Dir["#{install_dir}/*.scpt"].each {|f| hide_extension f }
end

desc "Install Launch task"
task :install => :compile do
  install_scripts 'Launch'
end

desc "Compile Launch AppleScripts"
task :compile  # built up directory

directory  'Launch'
APPLICATIONS.each do |app|
  f = "Launch/#{app}.scpt"
  file f => 'Launch' do
    compile f, <<-END
      do shell script "open -a \\"#{app}\\""
    END
  end
  file :compile => f
end

desc "Remove generated files"
task :clean do
  rm_rf ["Launch"]
end
