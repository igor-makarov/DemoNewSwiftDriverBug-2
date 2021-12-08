require 'yaml'
require 'fileutils'

project.name = 'DemoNewSwiftDriverBug'

targets = (1..100).map do |i|
  target do |t|
    FileUtils.rm_rf("Target#{i}")
    FileUtils.mkdir_p("Target#{i}")
    (1..50).each do |j|
      File.open("Target#{i}/SwiftSource#{j}.swift", 'w') do |f|
        f.puts 'import Foundation'
      end
    end
    t.name = "Target#{i}"
    t.type = :framework
    t.platform = :ios
    t.deployment_target = '11.0'
    t.all_configurations.each do |configuration|
      configuration.settings['INFOPLIST_FILE'] = 'DemoNewSwiftDriverBug/Supporting Files/DepInfoPlist.plist'
    end
  end
end

application_for :ios, '11.0' do |target|
  target.name = 'DemoNewSwiftDriverBug'
  target.linked_targets = targets
  File.open('DemoNewSwiftDriverBug/ImportTargets.swift', 'w') do |f|
    f.puts 'import Foundation'
    targets.each do |t|
      f.puts "import #{t.name}"
    end
  end

  target.all_configurations.each do |config|
    config.product_bundle_identifier = 'com.igor.demonewswiftdriverbug'
  end
end

project.after_save do
  system "rm -rf \"#{project.name}.xcodeproj/xcshareddata/xcschemes\""
end
