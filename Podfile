# Uncomment the next line if you're using Swift or would like to use dynamic frameworks
# use_frameworks!

platform :ios, '9.0'

def flutter_root
  generated_flutter_root = File.join('.dart_tool', 'flutter_gen')

  if not File.exist? generated_flutter_root
    raise 'Generated folder not found. Please run "flutter pub run build_runner build"'
  end

  return generated_flutter_root
end

target 'Runner' do
  # Flutter Pods
  pod 'Flutter', :path => '/Users/anasarif/Desktop/CareerFinderApp'
  pod 'FlutterPluginRegistrant', :path => '/Users/anasarif/Desktop/CareerFinderApp'

  # Generated files from Flutter
  add_root_paths_to_target('Runner')

  # Add your dependencies here

end

post_install do |installer|
  installer.pods_project.targets.each do |target|
    target.build_configurations.each do |config|
      config.build_settings['IPHONEOS_DEPLOYMENT_TARGET'] = '9.0'
    end
  end
end

def add_root_paths_to_target(target)
  Dir.glob(File.join(flutter_root, '**', '*')).each do |path|
    if File.directory?(path)
      relative_path = path.sub("#{flutter_root}/", '')
      absolute_path = File.absolute_path(path)
      pod target, :path => absolute_path, :glob => '**/*'
    end
  end
end
