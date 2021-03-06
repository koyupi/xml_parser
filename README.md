# XmlParser

Welcome to your new gem! In this directory, you'll find the files you need to be able to package up your Ruby library into a gem. Put your Ruby code in the file `lib/xml_parser`. To experiment with that code, run `bin/console` for an interactive prompt.

Parse Xml Document and String.
From String, and File.

## Installation

Add this line to your application's Gemfile:

```ruby
gem 'xml_parser'
```

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install xml_parser

## Usage

```ruby
# normalize
str = XmlParser::Text.normalize("a > b; < c")
str = XmlParser::Text.multi_normalize(["a > b; < c", "a > b; < c"])
# unnormalize
str = XmlParser::Text.unnormalize("a &gt; b; &lt; c")
str = XmlParser::Text.multi_unnormalize(["a &gt; b; &lt; c", "a &gt; b; &lt; c"])

# read xml
doc = XmlParser::Document.new("<sample><elm>sample xml</elm></sample>")
# you can read from file.
doc = XmlParser::Document.from_file("/var/sample.xml")
match_values = doc.xpath_map("/sample/test/@name") { |elm|
  puts elm
}

# parse xml from yaml file.
# initialize from yaml string, use XmlParser::Document.from_yml method.
# only yaml of the hash form is dealing.
doc = XmlParser::Document.from_yml_file("/var/home/hoge.yml", "root_element_name", "default_attr_name")

# parse xml from hash
doc = XmlParser::Document.from_hash({a: "v1", b: "v2"}, "root_element_name", "default_attr_name")
```

## Development

After checking out the repo, run `bin/setup` to install dependencies. Then, run `rake spec` to run the tests. You can also run `bin/console` for an interactive prompt that will allow you to experiment.

To install this gem onto your local machine, run `bundle exec rake install`. To release a new version, update the version number in `version.rb`, and then run `bundle exec rake release`, which will create a git tag for the version, push git commits and tags, and push the `.gem` file to [rubygems.org](https://rubygems.org).

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/koyupi/xml_parser. This project is intended to be a safe, welcoming space for collaboration, and contributors are expected to adhere to the [Contributor Covenant](contributor-covenant.org) code of conduct.


## License

The gem is available as open source under the terms of the [MIT License](http://opensource.org/licenses/MIT).

