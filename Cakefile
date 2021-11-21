require 'yaml'

project.name = 'DemoNewSwiftDriverBug'

application_for :ios, '9.0' do |target|
  target.name = 'DemoNewSwiftDriverBug'
  target.all_configurations.each do |config|
    config.product_bundle_identifier = 'com.igor.demonewswiftdriverbug'
  end
end

project.after_save do
  system "rm -rf \"#{project.name}.xcodeproj/xcshareddata/xcschemes\""
end
