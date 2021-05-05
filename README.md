# Yarn 2 with many dependencies

This project highlights a behaviour where yarn2 can create a yarn.lock which breaks yaml conventions if a project has a sufficiently large number of dependencies.

### To Replicate

1. Pull this repo and run `yarn` (not strictly necessary but may aswell)
2. Run `yarn parse` to run the script that will attempt to parse the yaml according to the standard.

#### Expected behaviour 

Yaml is able to be parsed as it fits the specification. Script prints success message.

#### Observed Behaviour 

Throws an error stating there is a key that is too long to be parsed. 

### Reasoning

A key is generated by yarn that is longer than 1024 characters long which is against yaml spec as seen here https://yaml.org/spec/1.2/spec.html - search for example 7.20 or the number 1024 for relevant info.
