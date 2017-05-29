# ref. http://qiita.com/joker1007/items/4e1c5eb6e60f80e75376
require 'bundler/source/git/git_proxy'
module AddGradlewHookForEmbulkPlugin
  def copy_to(destination, submodules=false)
    super
    if destination.join("./gradlew").exist?
      system("./gradlew gem", chdir: destination.to_s)

      Dir[destination.expand_path.join("{,*,*/*}", "build", "gemspec").to_s].each do |gemspec|
        system("cp", gemspec, File.expand_path("../../plugin.gemspec", gemspec))
      end
    end
  end
end
Bundler::Source::Git::GitProxy.prepend(AddGradlewHookForEmbulkPlugin)

source 'https://rubygems.org'

gem 'embulk-parser-catch_data_exception', github: 'civitaspo/embulk-parser-catch_data_exception'
gem 'embulk-filter-jruby_call_dataerror', github: 'civitaspo/embulk-filter-jruby_call_dataerror'

