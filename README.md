[original Readme of Slate](https://github.com/slatedocs/slate#readme)

[original Installation Guide (short version below)](https://github.com/slatedocs/slate/wiki/Using-Slate-Natively)

The documentation from the build folder is hosted on https://jschoedl.eu.pythonanywhere.com/docs/neseps.
## Installation for Native Usage

### Installing Dependencies on Linux

Install Ruby, NodeJS, and tools for compiling native ruby gems:

**On Ubuntu 18.04+**

```bash
sudo apt install ruby ruby-dev build-essential libffi-dev zlib1g-dev liblzma-dev nodejs patch
```

**On Fedora 31+**

```bash
sudo dnf install @development-tools redhat-rpm-config ruby ruby-devel libffi-devel zlib-devel xz-devel patch nodejs
```


Then, update RubyGems and install bundler:

```bash
sudo gem update --system
sudo gem install bundler
```

### Installing Dependencies on macOS

First, install [homebrew](https://brew.sh/), then install xcode command line tools:

```bash
xcode-select --install
```

Agree to the Xcode license:

```bash
sudo xcodebuild -license
```

Install nodejs runtime:

```bash
brew install node
```

Update RubyGems and install bundler:

```bash
gem update --system
gem install bundler
```

## Getting Set Up

1. `git clone https://github.com/jschoedl/neseps-docs.git`
2. `cd neseps-docs`
3. `bundle install`

Note: if the above fails on installing nokogiri and using macOS see
[here](https://github.com/sparklemotion/nokogiri.org/blob/master/docs/tutorials/installing_nokogiri.md#macos)
for some helpful tips on things that might help.

## Running / deploying

Development server on http://localhost:4567:

```bash
bundle exec middleman server
```

Building html files:

```bash
bundle exec middleman build
```
