# Personal page/blog of akashin

## Installation

To render this website on Ubuntu 16.04 you need:

1. Install ruby-dev
```sh
# On Ubuntu
sudo apt-get install ruby-dev
# On OSX
brew install ruby
```

2. Install Jekyll gem
```sh
sudo gem install jekyll
```

3. Install tufte-jekyll requirements:
```sh
sudo gem install bundler
bundle install
bundle clean --force
```

4. Fire Jekyll to see the web page:
```sh
jekyll serve -w --port 7003
```

## Resources

The base template for the site was taken from [tufte-jekyll](https://github.com/clayh53/tufte-jekyll.git).
