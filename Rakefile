SCRIPTS_DIR = "#{ENV['HOME']}/Library/Scripts"
APPLICATIONS = ["Adium", "Chax", "Emacs", "Finder", "Firefox", "Mailplane",
                "PandoraJam", "Safari", "Terminal"]

def compile(file, source)
  sh "osacompile -d -o '#{file}' -e '#{source}'"
end

def hide_extension(file)
  sh "test -e /usr/bin/SetFile && /usr/bin/SetFile -a E '#{file}'"
end

def install_scripts(directory)
  source_dir  = directory
  install_dir = "#{SCRIPTS_DIR}/#{directory.capitalize}"

  mkdir_p install_dir
  cp Dir["#{source_dir}/*.scpt"], install_dir
  Dir["#{install_dir}/*.scpt"].each {|f| hide_extension f }
end

desc "Install Launch task"
task :install => :compile do
  install_scripts 'launch'
end

desc "Compile Launch AppleScripts"
task :compile  # built up directory

directory  'launch'
APPLICATIONS.each do |app|
  f = "launch/#{app}.scpt"
  file f => 'launch' do
    compile f, <<-END
      tell application "#{app}"
        activate
      end tell
    END
  end
  file :compile => f
end

desc "Remove generated files"
task :clean do
  rm_rf ["launch"]
end
