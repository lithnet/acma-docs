# Creating the MA

- Install the Lithnet.Acma.MA.msi component
- Open the FIM Synchronization Service application
- On the *Management Agents* tab, click *Create* in the *Actions* pane
- Select *ACMA rules engine (Lithnet)* from the management agent type drop down list
- On the *Connectivity* tab, specify the SQL server and database name
- Specify the full path to the ACMAX configuration file. Ensure the FIM Synchronization Service account has read access to this location. ACMAX configuration files are created with the [[ACMA editor]]
- Specify the full path to the log file that ACMA will create. Ensure the FIM Synchronization Service account has read and write access to this location
- Follow the normal process of configuring your MA's object types, attributes, and flows. Note that the objectId attribute is mandatory and must be selected

It is recommended that you do not store the log or configuration file in the FIM extensions folder. Choose a dedicated location to hold your ACMA configuration and log files. 

