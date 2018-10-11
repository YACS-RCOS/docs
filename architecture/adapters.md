# Service Map

## Welcome!

Yacs uses services called adapters to pull data from a university's systems, and transform that data into a form Yacs can ingest.
Each data source has a corresponding adapter, which, when combined, provide a complete picture of a university's academic data.
It is very easy to create new adapters - you can find some examples in [the adapters section of the Yacs repository](https://github.com/YACS-RCOS/yacs/tree/master/adapters).
They can be written in any language, and must simply respond to a set of http endpoints.

## Basic Concept
Here's a diagram illustrating the basic concept of Yacs and adapters:

<!-- ![alt-text](../_media/adaptersfig1.png) -->
========  
DIAGRAM GOES HERE  
========  
<!-- TODO: Make diagram -->

When Yacs needs information that isn't stored in its database, it sends an HTTP request to the adapter that is responsible for that information. Then that adapter works its magic, and sends the information back in JSON format.

## HTTP Protocol

## JSON API and REST

## Implementation Agnostic
