# OmniAuth Nest Strategy

Strategy to authenticate with Nest via OAuth2 in OmniAuth

For more details, read the [Nest authorization documentation][auth-docs].

## Install

Add this to your `Gemfile`:

``` ruby
gem 'omniauth-nest'
```

then

``` sh
bundle install
```

## Example

1. Clone this repo and `cd` into it
2. `bundle install` (Required [bundler gem](http://bundler.io/))
3. `cd examples`
4. Log in to the [Nest Developer portal][portal] to get your OAuth credentials and to set your redirect URI.  
   Set your OAuth client ID and client secret as environment variables:
``` sh
export NEST_ID='Your OAuth client ID here'
export NEST_SECRET='Your OAuth client secret here'
```
5. Set redirect URI to http://localhost:9292/auth/nest/callback
6. `bundle exec rackup`
7. Open http://localhost:9292 in your browser and follow the links


## Usage

In Rails add the following to `config/initializers/omniauth.rb`

``` ruby
use OmniAuth::Builder do
  provider :nest, ENV['NEST_ID'], ENV['NEST_SECRET']
end
```

This will enable the route `/auth/nest` which will start the OAuth2 flow. See `examples/config.ru` for a fully working example.

NOTE: The Nest OAuth2 service only returns authorization tokens for the Nest API, not user identification.

## Contributing

Contributions are always welcome and highly encouraged.

See [CONTRIBUTING](CONTRIBUTING.md) for more information on how to get started.

## License

Apache 2.0 - See [LICENSE](LICENSE) for more information.

[portal]: https://console.developers.nest.com
[auth-docs]: https://developer.nest.com/documentation/cloud/authorization-overview
