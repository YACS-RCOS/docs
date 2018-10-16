<!--
- ->
# Service Map

## Welcome!

Yacs uses services called adapters to pull data from a university's systems, and transform that data into a form Yacs can ingest.
Each data source has a corresponding adapter, which, when combined, provide a complete picture of a university's academic data.
It is very easy to create new adapters - you can find some examples in [the adapters section of the Yacs repository][yacs-adapters].
They can be written in any language, and must simply respond to a set of HTTP endpoints.

## Basic Concept
Here's a diagram illustrating the basic concept of Yacs and adapters:

<!-- ![alt-text](../_media/adaptersfig1.png) - ->
========  
DIAGRAM GOES HERE  
========  
<!-- TODO: Make diagram --><!--

- ->
When Yacs needs information that isn't stored in its database, it sends an HTTP request to the adapter that is responsible for that information. Then that adapter works its magic, and sends the information back in JSON format. This document is going to focus on the [`yaml-rpi`][yaml-rpi-adapter] adapter and use its code in examples. The document `app.rb` will also be edited for clarity to this:

``` ruby
require 'sinatra'
require 'sinatra/json'
require 'oj'
require 'yaml'

set :bind, '0.0.0.0'
set :port, 4600

ENV['YAML_SOURCE'] ||= 'schools-and-subjects.yml'

get "/:term_shortname" do
	file = open(ENV['YAML_SOURCE'])
	yaml_content = YAML.load(file)
	json yaml_content
end
```

## Data Source
The first thing your adapter needs is a place to get data from. In the `yaml-rpi` adapter, that place is a file called `schools-and-subjects.yml`:

```yml

schools:
  - longname: Humanities, Arts and Social Sciences
    subjects:
      - shortname: ARTS
        longname: Arts
      - shortname: COGS
        longname: Cognitive Science
      - shortname: STSH
        longname: Science and Technology Studies - Humanities
      - shortname: STSS
        longname: Science and Technology Studies - Social Sciences
      - shortname: COMM
        longname: Communication

```

Now that we have a place to get information from, we need to load it into the adapter. We do so with this line in `app.rb`:

``` ruby

# ...
require 'yaml'

ENV['YAML_SOURCE'] ||= 'schools-and-subjects.yml'

# ...
	file = open(ENV['YAML_SOURCE'])
	yaml_content = YAML.load(file)
	# ...
```

Here, `ENV` is just a container for the environment variables in Ruby, and `'YAML_SOURCE'` is the name of the environment variable. We're setting its value to the name of the file, `'schools-and-subjects.yml'`. Then, when the adapter is asked for information, it first opens a file at the location, then uses a function from the `'yaml'` package to convert the file's contents to a ruby object.

## JSON API and REST
Your adapter then needs to convert the data that it loaded into a format that Yacs can read - that's what the JSON API is for. This document will give a brief explanation of the API - a more in-depth explanation can be found [here][json-api].

The JSON API is based off of JavaScript Object Notation:

```JSON

{
	"attribute1": "value2",
	"numeric-attribute":"10",
	"object-attribute": {
		"attribute1": "object-value1",
	},
}

```

Objects are surrounded by `{curly brackets}`, and both attributes and values are surrounded by `"double quotes"`. Each attribute-value pair is specified by a single line, with a colon separating attributes and values, and attribute-value pairs are separated by a comma. Spacing is irrelevant to the formatting of the document except in strings -- anything between double quotes must be on a single line. Finally, there is no syntax for making comments.

In the `yaml-rpi` adapter, this is done through these lines in `app.rb`:

```ruby

require 'sinatra/json'
require 'oj'

# ...
	json yaml_content

```

`require 'sinatra/json'` and `require 'oj'` tell ruby to load the Sinatra package's JSON helper function and the Optimized JSON package respectively. Then when the adapter needs to convert the data in `yaml_content` to JSON, the `json` function from `'sinatra/json'` is called.


## HTTP Protocol

<!-- IDK what to do here, I don't really understand this part fully yet

- ->

```ruby

# ...
require 'sinatra'

set :bind, '0.0.0.0'
set :port, 4600

# ...

get "/:term_shortname" do
  # ...
end

```

## Implementation Agnostic
Notice that the only parts of the adapter that actually interact with YACS itself are format of the data (JSON) and the data transfer protocol (HTTP). Since both of these systems are implementation agnostic, you can write your adapter in whatever language you want! As long as it responds to HTTP requests with a JSON object, it's good to go!

[yacs-adapters]: https://github.com/YACS-RCOS/yacs/tree/master/adapters
[yaml-rpi-adapter]: https://github.com/YACS-RCOS/yacs/tree/master/adapters/yaml-rpi
[json-api]: http://jsonapi.org/format/
<!-- -->
