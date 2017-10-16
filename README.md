# RailsOpentracer

This gem instruments an application to be used with a tracing client. At this stage it is configured to be used with Zipkin only, but
this can be changed at a later stage.

## Installation

Add this line to your application's Gemfile:

```ruby
gem 'rails_opentracer'
```

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install rails_opentracer

Generate files required by gem:

    $ rails g rails_opentracer:install

Add the following to development.rb:

```ruby
config.middleware.use Tracer
```

## Usage

To run Zipkin locally, do:

  $ docker run -d -p 9411:9411 openzipkin/zipkin

You will need to set an environment variable with the Zipkin client URL. Locally this would be: `ENV['ZIPKIN_SERVICE_URL']='http://localhost:9411'`.

Whenever a request is made to another application, do:

```ruby
include RailsOpentracer
```

in the applicable controller, and then:

```ruby
with_span 'name of span' do
  faraday_get(URL)
end
```



## Development

After checking out the repo, run `bin/setup` to install dependencies. Then, run `rake test` to run the tests. You can also run `bin/console` for an interactive prompt that will allow you to experiment.

To install this gem onto your local machine, run `bundle exec rake install`. To release a new version, update the version number in `version.rb`, and then run `bundle exec rake release`, which will create a git tag for the version, push git commits and tags, and push the `.gem` file to [rubygems.org](https://rubygems.org).

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/[USERNAME]/rails_opentracer. This project is intended to be a safe, welcoming space for collaboration, and contributors are expected to adhere to the [Contributor Covenant](http://contributor-covenant.org) code of conduct.

## License

The gem is available as open source under the terms of the [MIT License](http://opensource.org/licenses/MIT).

## Code of Conduct

Everyone interacting in the RailsOpentracer project’s codebases, issue trackers, chat rooms and mailing lists is expected to follow the [code of conduct](https://github.com/[USERNAME]/rails_opentracer/blob/master/CODE_OF_CONDUCT.md).
