# Service Map

## Welcome!

Yacs uses services called adapters to pull data from a university's systems, and transform that data into a form Yacs can ingest.
Each data source has a corresponding adapter, which, when combined, provide a complete picture of a university's academic data.
It is very easy to create new adapters - you can find some examples in [the adapters section of the Yacs repository][yacs-adapters].
They can be written in any language, and must simply respond to a set of HTTP endpoints.

## Basic Concept
Here's a diagram illustrating the basic concept of Yacs and adapters:

<!-- ![alt-text](../_media/adaptersfig1.png) -->
========  
DIAGRAM GOES HERE  
========  
<!-- TODO: Make diagram -->

When Yacs needs information that isn't stored in its database, it sends an HTTP request to the adapter that is responsible for that information. Then that adapter works its magic, and sends the information back in JSON format. This document is going to focus on the [`yaml-rpi`][yaml-rpi-adapter] adapter and use its code in examples.

## Data Source
The first thing your adapter needs is a place to get data from. In the `yaml-rpi` adapter, that place is a file called `schools-and-subjects.yml`.

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

Now that we have a place to get information from, we need to load it into the adapter. We do so with this line:

```ruby

ENV['YAML_SOURCE'] ||= 'schools-and-subjects.yml'

```

Here, `ENV` is just a container for the environment variables in Ruby, and `'YAML_SOURCE'` is the name of the environment variable. We're setting its value to the name of the file, `'schools-and-subjects.yml'`, and essentially that 'loads' it into the adapter.

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

Notice that objects are surrounded by `{curly brackets}`, and both attributes and values are surrounded by `"double quotes"`. Each attribute-value pair is specified by a single line, with a colon separating attributes and values, and attribute-value pairs are separated by a comma. Note that spacing is irrelevant to the formatting of the document except in strings -- anything between double quotes must be on a single line.

In the `yaml-rpi` adapter, this is done through


## HTTP Protocol


## Implementation Agnostic

[yacs-adapters]: https://github.com/YACS-RCOS/yacs/tree/master/adapters
[yaml-rpi-adapter]: https://github.com/YACS-RCOS/yacs/tree/master/adapters/yaml-rpi
[json-api]: http://jsonapi.org/format/
