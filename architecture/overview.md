# Overview of the Yacs Architecture

## Welcome!

This page explains the Yacs data architecture.

## Pipeline
The most interesting part of Yacs is what we call the **pipeline**.
The pipeline is what solves the essential problem for a univeristy-agnostic course scheduler and browser: ingesting data.
In order to work at any univeristy, we must be able to ingest academic data from any source, in any form.
This is accomplished in part by separating the pipeline, which ingests data, from the core application, which serves Yacs' users.

## Sources
Academic data may come from many different kinds of **sources**.
This includes course catalogs, custom websites, APIs, databases, XML files, PDFs, spreadsheets, you get the idea.
Every univeristy stores their academic data differently, often employing a mix of different solutions from different vendors.
We have found that these systems are often clunky, poorly understood, or undermaintained.

Nevertheless, Yacs must be able to adapt to connect to any source of data, so that users from any university can have the same awesome experience.
And it must be able to do so without requiring modification to the main codebase, so that Yacs can be easily used at any univeristy without needing to fork the project.

In addition, because universities often employ many different sources of data, Yacs must be able to ingest and combine data from several sources in an intelligent, configurable way.

## Adapters
To achieve the goals above, the Yacs pipeline 

## Amalgamator

## Core
