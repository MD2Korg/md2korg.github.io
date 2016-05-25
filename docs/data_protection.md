# Protection of Sensitive Information
The MD2K platform is designed to encrypt all data both at rest and in transport.  mCerebrum provides inter-app data protections to prevent unauthorized services from retrieving information from Data Kit without appropriate security credentials.  Data Kit ensures that all data persisted on the phone is stored in on an encrypted storage device in a  SQLite database.  This database can only be read upon providing an correct passphrase on the phone that encrypted the storage medium.  This prevents the removal of the data from the smartphone without utilizing built-in Android functionality.

Cerebral Cortex provides an encrypted API for data transport from mCerebrum to our cloud services.  This API follows standard industry practices and utilizes HTTPS with NGINX handling the SSL certificates for the internal services and can be easily adapted to the AWS architecture. Data is deidentified as much as possible before being stored within the Cerebral Cortex system.