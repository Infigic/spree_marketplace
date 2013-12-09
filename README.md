SpreeMarketplace
================

[![Build Status](https://secure.travis-ci.org/jdutil/spree_marketplace.png)](http://travis-ci.org/jdutil/spree_marketplace)
[![Code Climate](https://codeclimate.com/github/jdutil/spree_marketplace.png)](https://codeclimate.com/github/jdutil/spree_marketplace)
[![Coverage Status](https://coveralls.io/repos/jdutil/spree_marketplace/badge.png?branch=master)](https://coveralls.io/r/jdutil/spree_marketplace)
[![Dependency Status](https://gemnasium.com/jdutil/spree_marketplace.png?travis)](https://gemnasium.com/jdutil/spree_marketplace)

Spree Marketplace uses the [Spree Drop Ship](https://github.com/jdutil/spree_drop_ship) extension in order to enable using Spree as a Marketplace.  Mainly all that really means is that this extension enables sending payments to your drop ship suppliers through [Stripe](https://stripe.com) with their payment service.

All the other main marketplace functionality - such as - vendors, product setup, shipment details etc... is all accomplished by [Spree Drop Ship](https://github.com/jdutil/spree_drop_ship).

Installation
------------

Add spree_marketplace to your Gemfile:

```ruby
gem 'spree_marketplace', github: 'jdutil/spree_marketplace'
```

Bundle your dependencies and run the installation generator:

```shell
bundle
bundle exec rails g spree_marketplace:install
```

Configuration
-------------

Once installed you must configure your [Stripe](https://stripe.com) API keys.  To do so you have two options:

1) Simply setup either as your payment processing method and spree_marketplace will use your payment methods api key.

2) Configure in an initializer by adding the following to the end of your `config/intializers/spree.rb`:

    SpreeMarketplace::Config[:stripe_publishable_key] = 'YourPublishableKey'
    SpreeMarketplace::Config[:stripe_secret_key] = 'YourSecretKey'

3) Currently you must implement your own payment code as this varies between applications, but once the TODO list is complete this will be an optional configuration likely in a rake task.

Testing
-------

Be sure to bundle your dependencies and then create a dummy test app for the specs to run against.

```shell
bundle
bundle exec rake test_app
bundle exec rspec spec
```

When testing your applications integration with this extension you may use it's factories.
Simply add this require statement to your spec_helper:

```ruby
require 'spree_marketplace/factories'
```

TODO
----

- On dso complete credit supplier bank account
- On order complete credit marketplace bank account w/commission
- On order complete credit marketplace bank account w/tax?

Copyright (c) 2013 [Jeff Dutil](https://github.com/jdutil), released under the New BSD License
