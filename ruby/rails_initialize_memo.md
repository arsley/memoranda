# Rails init memo

## Installation

```
# skip bundle, skip mailer
$ rails new -B -M
```

## gems

```
gem 'slim-rails'
gem 'scssc-rails' # needs generator...?

group :development do
  gem 'pry-byebug'
end

group :test do
  gem 'rspec-rails'
  gem 'factory_bot_rails'
  gem 'faker'
end
```

## Bundle

```
# use bundler's bin/ instead of rails' generated bin/
$ bundle binstubs bundler --force
```

## RSpec

```
$ bin/rails g rspec:install
```

## Refs

- [Understanding binstubs](https://techracho.bpsinc.jp/hachi8833/2016_08_24/25037)
- [RSpec setting](https://qiita.com/akiko-pusu/items/0f15130509a88cf59a7d)
- [slim-rails](https://github.com/slim-template/slim-rails)
