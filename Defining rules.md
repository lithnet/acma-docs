# Defining Business Rules
The power of ACMA comes with its ability to modify or create information in response to changes in incoming data. The [[ACMA editor]] is the tool used to configure the application with your business rules.

The ACMA editor stores business rules in a configuration file. This allows very easy lifecycle management of your configuration through a DEV->QA->PROD cycle.

Once your business rules have been defined and documented, you can start implementing them as constructors and events within the configuration file.

Careful planning needs to go into designing the ACMA configuration. There are a few important things to remember

- ACMA is an event-based system. For ACMA to perform an action, the conditions under which it needs to do so need to be well defined. Sometimes it is also important to consider what conditions the action should *not* be performed under.
- ACMA executes in a sequential top-down order, as shown in the ACMA editor. Changes made by one constructor will only be visible to the constructors that run *after* it. The execution engine passes over each constructor only once.

Unit testing is probably the most important thing to plan for within ACMA. Each constructor should have a set of unit tests that cover all the scenario that constructor should and should not execute. 
The relationship between attributes and constructors can become quite complex with a large number of rules. Properly designed unit tests will ensure that a change to one constructor, does not impact another that was working fine before that change. 

The following pages detail the types of configuration objects within ACMA, and how to configure them appropriately.

- Configuration File

 * [[Transforms]]
 * [[Pre-Operation Events]]
 * [[Class Constructors]]
  * [[Attribute Constructors]]
  * [[Rules]]
  * [[Exit events]]

