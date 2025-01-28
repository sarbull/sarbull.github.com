---
title:        "How to version my rails application"
author:       "sarbull"
---

## Step 1
Create your **app/.version** file.

**app/.version**
```
1.0.1
```
## Step 2
Create a rake task that reads that version and generates some ruby code that blends into your rails app.

**app/lib/tasks/create_version.rake**
```ruby
task :create_version do
  desc "Create version"
  version = File.read("#{Rails.root}/.version").split('.')
  version_file = "#{Rails.root}/config/initializers/version.rb"

  major = version[0]
  minor = version[1]
  patch = version[2]
  build = `git describe --always --tags`

  version_string = "module App
  class Application < Rails::Application
    VERSION = \"#{major.to_s}.#{minor.to_s}.#{patch.to_s}.#{build.strip}\"
  end
end"

  File.open(version_file, "w") {|f| f.print(version_string)}
end
```

## Step 3
Run the rake task accordingly to your deploy pipeline or manually but make sure you always commit it.


## Step 4
Check the generated file.

**app/config/initializers/version.rb**
```ruby
module App
  class Application < Rails::Application
    VERSION = "1.0.1.887f65e"
  end
end
```

## Step 5
Inlcude your generated version initializer into the main `application.rb` config file.

**app/config/application.rb**
```ruby
...
require_relative "initializers/version"
...
```

## Step 6
Print it wherever you need it, in the views or maybe in a controller.

```ruby
My version: <%= App::Application::VERSION %>
```
