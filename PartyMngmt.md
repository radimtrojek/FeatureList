# BD-03: Party mngt
Management of persons which can be individuals or organizations (companies). Be aware that not every party is also user account. These parties can be customers, partners (Valuers, Notaries), Operators, Disponents or any kind of person somehow related to a business.

## BFR-03001: Party basic data mngt
This feature provides management of basic party data like name, DOB, Marital status and so on.  
Every party can be labeled by the system process with configured labels. Labels are used to give party their role in business e.g. Lead, Customer, Valuer, Operator and so on.   

* **Improvements:**
	* enhance management of organisation party type

### BFU-0300101: Create individual
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|Done|1|SVC, OnBoarding|OP, CUS|

It allows user to create new party of individual and setup its basic party attributes. To create new party in system at least one basic party attribute has to be provided.  
TODO(List of intividual attributes)

### BFU-0300102: Create organisation
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|Done|1|SVC, OnBoarding|OP, CUS|

It allows user to create new party of organisation and setup its basic party attributes which is name of an organization.

* **Improvements:**
	* Cover organization structure and relationship between parties.

### BFU-0300103: Verify party
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|InProgress|1|SVC, OnBoarding|OP|

It allows user or 3rd party system to keep verification status of party basic data. For example based on identity check.


## BFR-03002: Contact mngt
Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|Done|1|SVC, OnBoarding, IB|OP, CUS|

This feature provides management of party's contact information. This contact can be various types, like email address, phone number, based on configuration. System also provides possibility to label contact which allows user or others system processes to give a contact role in business e.g. address can be labeled "Card-delivery".  
For every type of contact at least one contact has to be primary.  
**Primary:**  
Primary contact is default contact for every processes in system. Once first contact of given type is created then customer allways has to have primary contact. Primary contact is only one contact of given type. 

### BFU-0300201: Create contact
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|Done|1|SVC, OnBoarding, IB|OP, CUS|

It allows user to create new contact. Based on type of the cont
act proper validations are processed so that system keeps only valid contact e.g. email address.  
Once first contact is created of given type it is marked as primary.  
**Phone number:**  
For phone number system uses sophisticated validation which validates whether number corellates with int. code.  
To keep phone number int. code is required. It is not required to provide int. code separately it can be included in pnone number and system parses it out.

### BFU-0300202: Verify contact
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|Done|1|SVC, OnBoarding, IB|CUS|

It allows user to validate existence and party ownership of given contact information. 

### BFU-0300203: Make primary contact
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|Done|1|SVC, OnBoarding, IB|OP, CUS|

It allows user to set one existing contact as primary.

### BFU-0300204: Remove contact
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|Done|1|SVC, OnBoarding, IB|OP, CUS|

It allows user to remove existing not-primary contact information.

### BFU-0300205: Contact overview 
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|Done|1|SVC|

It allows user to see list of all set contacts.

## BFR-03003: Address mngt
This feature provides management of party's addresses. System also provides possibility to label address which allows user or others system processes to give an address role in business e.g. address can be labeled "Card-delivery".
For every type of address at least one address has to be primary.
Address is composed of numbers address fields to offer world-wide coveradge. To follow country / region specific address formats an address format can be configured per group of countries.

### BFU-0300301: Create address
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|Done|1|SVC, IB|OP, CUS

It allows user to create new address of given party.  Validations are processed so that required address fields is available.
Once first address is created it is marked as primary.  

* **Improvements:**
	* to configure required fields per address format

### BFU-0300302: Make primary address
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|Done|1|SVC, IB|OP, CUS

It allows user to set one existing address as primary.


### BFU-0300304: Capture proof of address document
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|DONE|1|Jumio,Onboarding|OP,CUS|Jumio only

It allows to capture POA document in order to verify that given party has relation with provided address. It has to be document where party name and address has to be stated togather like Bank statement, Utility bill and so on.  
Function also supports automatic address extraction which is able to extract some data exactly - City, Postcode and some in block - Streetname, House number, House name etc. as address line 1-n format. 

* **Improvements:**
	* introduce 3rd party independent process - upload POA, Extract POA, Create address from POA.

### BFU-0300307: Create address from POA
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|NEW|1|SVC, Jumio, Onboarding|OP,CUS|

It allows user to convert Proof of address document to new address. Function creates new address based on extracted data from POA document. Extracted data can be either ready or extracted just before creation.

### BFU-0300303: Verify and cleanse address
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|InProgress|1|SVC, Trulioo, Onboarding|OP|Troolio only, address approval FR in CIF

It allows user or system to verify an existence of address and to cleanse not-structured address. Address verification can be done by system process based on 3rd party service check or by operator itself. System differentiates between system verification status and operator verification status.

**Address cleansing:**  
Function is able to make structured address based on address in address-line 1-n format.

* **Improvements:**
	* introduce Trulioo independent process.

### BFU-0300305: Remove address
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|Done|1|SVC, IB|OP, CUS|

It allows user to remove existing not-primary address.

### BFU-0300307: Address overview
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|Done|1|SVC, IB|OP, CUS|

It allows user to see list of all party addresses together with related POA document.

### BFU-0300306: Parametrize address format
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|Done|1|SVC, IB|OP, CUS|

It allows user to configure address formats per country groups.


### BFU-0300308: Address localization
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|Done|1|SVC|OP|Google maps

It allows user to see location of address on map.


## BFR-03004: Party identifier mngt
This feature allows to manage and use different types of party identifiers - used mainly in contacts with government and regulatory institutions. These identifiers are usually under stronger access control (GDPR).

### BFU-0300401: Configure identifier types
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|Done|1|SVC|OP|
This function allow user to set list of party identifiers.

### BFU-0300402: Manage identifiers
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|Done|1|SVC|OP|
This function allow user to set value of concrete identifier or remove it from party.

**Improvements:**

* FE configuration
* Implement specific types of validation for world wide used identifiers.
* Implement available list per country 

## BFR-03005: Party relations mngt
This feature covers functionality of relations between different parties and its history. Mainly to set-up family relationships, business relationships and controlled vs controlling relations. 

Relations could be with or without direction. 

### BFU-0300500X:
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|New|


**Improvements:**

* To be analysed and implemented 
* FE configuration

## BFR-03006: ID document mngt


## BFR-03007: Party segmentation
Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|Analysis|
It allows user to set-up different types of relations between parties. 

## BFR-03008: Party deduplication mngt
### BFU-0300801: Merge duplicit parites
### BFU-0300802: Check duplicity parties
### BFU-0300803: Find duplicity parties




## BFR-03009: Risk profile mngt

## BFR-03010: Consent mngt

## BFR-03011: Customer document mngt

## BFR-03012: Labels
