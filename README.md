# Capistrano Unicorn Generators

This gem provides next capistrano tasks:

unicorn:setup -- create /etc/init.d/unicorn-YOUR_APP

And unicorn init script generator, that will create local copy of default script template for customization.

## Installation

Add this line to your application's Gemfile:

    gem 'capistrano-unicorn-generators'

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install capistrano-unicorn-generators

## Usage

### Setup

Add the library to your `Gemfile`:

```ruby
group :development do
  gem 'capistrano-unicorn-generators', :require => false
end
```

And load it into your deployment script `config/deploy.rb`:

```ruby
require 'capistrano-unicorn-generators'
```

Add unicorn restart task hook:

```ruby
after "deploy:setup", "unicorn:setup", "unicorn:reload"
```

### Test

## Configuration

## Available Tasks

To get a list of all capistrano tasks, run `cap -T`:

```
cap unicorn:setup		      # Install Unicorn init script (tested in Ubuntu only)
```

If you want to customize unicorn init script, just generate local template script before running `unicorn:setup`:
```
$ rails generate capistrano:unicorn:config
```
And then edit file `config/deploy/unicorn_init.erb` as you like.

## License

See LICENSE file for details.

## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Added some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request
