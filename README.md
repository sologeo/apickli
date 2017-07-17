# apickli - REST API integration testing framework with cucumber.js

**Apickli** is a REST API integration testing framework based on cucumber.js.

It provides a gherkin framework and a collection of utility functions to make API testing easy and less time consuming.

**Apickli** is also available as an [NPM package](https://www.npmjs.com/package/apickli).

[Cucumber.js](https://github.com/cucumber/cucumber-js) is JavaScript & Node.js implementation of Behaviour Driven Development test framework - [Cucumber](http://cukes.info/). Cucumber.js is using [Gherkin](http://cukes.info/gherkin.html) language for describing the test scenarios in [BDD](http://en.wikipedia.org/wiki/Behavior-driven_development) manner.  

## Modifications

This version has been forked from apickli@1.7.4 to support schema validation against a response body path, namely to support validating Fhir resources within a [Fhir bundle](https://hl7.org/fhir/DSTU2/bundle.html). 

## Gherkin Expressions
The following gherkin expressions have been modified:

```
THEN:

	removed:
    	response body should be valid according to schema file (.*)
	
	added:
	response body should validate against schema file (.*)
	response body path (.*) should validate against schema file (.*)
```

Definition was changed from **should be valid** to **should validate against** to maintain consistency with the beginning of the step definitions ("response body" and "response body path").  This was due to amgiuous step definition errors when attempting to create the definition **response body path (.*) should be valid**:

```
     Multiple step definitions match:
       /^response body path (.*) should be ((?!of type).+)$/                     - target\test\integration\features\step_definitions\apickli-gherkin.js:208
       /^response body path (.*) should be valid according to schema file (.*)$/ - target\test\integration\features\step_definitions\apickli-gherkin.js:257
```

## Original

The original [apickli can be found here](https://github.com/apickli/apickli).
