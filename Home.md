[[images/logo-ex-small.png]]
# ACMA
Lithnet ACMA is a codeless rules engine for Microsoft Forefront Identity Manager 2010 R2. ACMA provides a means for performing powerful rules-based construction of objects and attributes without the need to write custom code.

ACMA is implemented as an extensible management agent (ECMA2.2), built upon an SQL Server 2012 database, and comes with a powerful UI-based rules editor and PowerShell extensions.

### Getting started
The following pages will assist you in installing the ACMA components and defining your business rules

- [[Installing the software | Installation]]
- [[Configuring your schema | Configure Schema]]
- [[Configuring the MA]]
- [[Defining business rules | Defining rules]]

### ACMA Demo Lab 
The ACMA lab has been designed to assist with understanding ACMA concepts by demonstrating core functionality of ACMA using some sample business rules and data. A sample rules file and PowerShell scripts are included in the demo.

- [[Lab environment definition]]
- [[Setting up the lab environment]]
- [[Evaluating the business rules]]

### Reference
The following pages provide detailed reference material on the ACMA database and rules file

- Database Schema

 * [[Object Classes]]
  * [[Shadow Objects]]
 * [[Attributes]]
 * [[Attribute Bindings]]
  * [[Reference back-linking]]
 * [[Sequences]]
 * [[Constants]]

- Configuration File

 * [[Transforms]]
 * [[Pre-Operation Events]]
 * [[Class Constructors]]
  * [[Attribute Constructors]]
  * [[Rules]]
  * [[Exit events]]

- Extensibility

 * [[PowerShell]]
 * [[Extension exit events]]

- Unit Tests
- Concepts

 * [[Type Coercion Matrix | type coercion model]]
 * [[ACMA Declarative Language]]


