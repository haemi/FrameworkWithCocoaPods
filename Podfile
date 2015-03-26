platform :ios, '7.0'
inhibit_all_warnings!

link_with 'SharedDataSource'

pod 'MagicalRecord', '2.2'

post_install do |installer|
  target = installer.project.targets.find{|t| t.to_s == "Pods-MagicalRecord"}
  target.build_configurations.each do |config|
    s = config.build_settings['GCC_PREPROCESSOR_DEFINITIONS']
    s = [ '$(inherited)' ] if s == nil;
    s.push('MR_ENABLE_ACTIVE_RECORD_LOGGING=0') if config.to_s == "Debug";
    config.build_settings['GCC_PREPROCESSOR_DEFINITIONS'] = s
  end
end
