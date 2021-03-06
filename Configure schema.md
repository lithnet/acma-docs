# Configure the Schema
The ACMA schema is maintained in the ACMA database, and must be configured before you set up the MA. The ACMA schema is very similar to the FIM schema, consisting of [[object classes]], [[attributes]], and [[bindings | attribute bindings]]. ACMA supports the same attribute types as FIM, with the addition of a native DateTime attribute type, which imports and exports dates in the FIM service date format (ISO8601), but allows you to perform date comparisons and manipulations within ACMA itself.

The schema is modified using the [[ACMA Editor]] or the [[PowerShell]] cmdlets. 

The following pages detail what the elements of the ACMA schema are, and how they are configured.

- [[Object Classes]]

 * [[Shadow Objects]]

- [[Attributes]]
- [[Attribute Bindings]]

 * [[Reference back-linking]]
- [[Sequences]]
- [[Constants]]

Once you have defined the schema, you can move on to [[configuring the MA]]

