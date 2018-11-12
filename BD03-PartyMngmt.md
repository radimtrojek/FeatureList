# BD-03: Party mngt
Management of persons which can be individuals or organisations (companies). Be aware that not every party is also user account. These parties can be customers, partners (Valuers, Notaries), Operators, Disponents or any kind of person somehow related to a business.

## BFR-03001: Party basic data mngt
This feature provides management of basic party data like name, DOB, Marital status, Country of residence and so on.  
Every party can be labeled by the system process with configured labels. Labels are used to give party their role in business e.g. Lead, Customer, Borrower, Investor, Valuer, Operator and so on.   

* **Improvements:**
	* enhance management of organisation party type

### BFU-0300101: Create individual
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|Done|1|SVC, OnBoarding|OP, CUS|

It allows user to create new party of individual and setup its basic party attributes. To create new party in system at least one basic party attribute has to be provided.  
TODO(List of individual attributes)

### BFU-0300102: Create organisation
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|Done|1|SVC, OnBoarding|OP, CUS|

It allows user to create new party of organisation and setup its basic party attributes which is name of an organisation.

* **Improvements:**
	* Cover organisation structure and relationship between parties.

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
Primary contact is default contact for every processes in system. Once first contact of given type is created then customer always has to have primary contact. Primary contact is only one contact of given type. 

### BFU-0300201: Create contact
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|Done|1|SVC, OnBoarding, IB|OP, CUS|

It allows user to create new contact. Based on type of the cont
act proper validations are processed so that system keeps only valid contact e.g. email address.  
Once first contact is created of given type it is marked as primary.  
**Phone number:**  
For phone number system uses sophisticated validation which validates whether number correlates with int. code.  
To keep phone number int. code is required. It is not required to provide int. code separately it can be included in phone number and system parses it out.

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

* **Improvements:**
	* contact history

## BFR-03003: Address mngt
This feature provides management of party's addresses. System also provides possibility to label address which allows user or others system processes to give an address role in business e.g. address can be labeled "Card-delivery".
For every type of address at least one address has to be primary.
Address is composed of numbers address fields to offer world-wide coverage. To follow country / region specific address formats an address format can be configured per group of countries.

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

### BFU-0300308: Update address
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|Done|1|SVC, IB|OP, CUS

It allows user to update existing address of given party.  
Once first address is created it is marked as primary.  

* **Improvements:**
	* Smart update which ensures that update is only for fix incorrectness in address not adding new address.

### BFU-0300304: Capture proof of address document
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|DONE|1|Jumio, Onboarding|OP,CUS|Jumio only

It allows to capture POA document in order to verify that given party has relation with provided address. It has to be document where party name and address has to be stated together like Bank statement, Utility bill and so on.  
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
|InProgress|1|SVC, Trulioo, Onboarding|OP|Trulioo only, address approval FR in CIF

It allows user or system to verify an existence of address and to cleanse not-structured address. Address verification can be done by system process based on 3rd party service check or by operator itself. System differentiates between system verification status and operator verification status.

**Address cleansing:**  
Function is able to make structured address based on address in address-line 1-n format.

* **Improvements:**
	* introduce Trulioo independent process.
	* introduce logic for manually added address or POA

### BFU-0300304: Waive address verification and cleansing
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|inDevelopment|1|Jumio, Onboarding|OP|

It allows operator to overcome address verification and cleansing issue(s) by waiving result of the process. Operator can correct extracted data and verify it manually.  
System differentiates between system verification status and operator verification status.

### BFU-0300305: Request for new POA doc
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|inDevelopment|0|Jumio, Onboarding|OP, CUS|

It allows operator to request new POA document capture in case that address verification and cleansing or KYC went wrong.  
Requested user is requested for upload and see operator message with instruction what was wrong.

* **Improvements:**
	* Address and POA history
	
### BFU-0300309: Parametrize POA document types
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|inDevelopment|0|Jumio, Onboarding|OP, CUS|

It allows to configure what types of POA documents can be capture. It needs to be also configured in 3rd party service.

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

* **Improvements:**
	* address history

### BFU-0300306: Parametrize address format
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|Done|1|SVC, IB|OP, CUS|

It allows user to configure address formats per country groups.


### BFU-0300308: Address localisation
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|Done|1|SVC|OP|Google maps

It allows user to see location of address on map.


## BFR-03004: Party identifier mngt
This feature allows to manage and use different types of party identifiers. It can be any of identifier government burro identifiers, external register or system identifiers.

### BFU-0300401: Parametrize identifier
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|Done|1|SVC|OP|

This function allow user to configure types of party identifiers. It is basically key-value record-keeping.

### BFU-0300402: Manage identifiers
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|inAnasysis|0.1|SVC|OP|

This function allow user to set an identifier value by system processes.

**Improvements:**

* GUI for managing identifier
* Implement specific types of validation for world wide used identifiers.
* Implement available list per country 
* Identifier data sensitivity protection

## BFR-03006: ID document mngt
This feature covers functionality of management party's ID documents e.g. ID cards, Passports, Driver's license, Residency permit and so on. Every party can have one or more ID documents.  
ID document is composed of ID document data like ID number, expiration date, issue date, Country of issue so on and binary attachments with scan of the document and user's selfie.  
This document also works as proof of identity and carries verification status of document and of identity verification.

### BFU-0300601: Capture proof of identity document
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|DONE|1|Jumio, Onboarding|OP,CUS|Jumio only

It allows to capture POI document and user's selfie in order to verify user's identity. 
Function also supports automatic document extraction which is able to extract person data like DOB, Name as well as ID document data like number and expiration date and so on.

* **Improvements:**
	* introduce 3rd party independent process - upload POI, Extract POI, Process person and ID document data

### BFU-0300602: Verify user's identity
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|DONE|1|Jumio, Onboarding|OP,CUS|Jumio only

As precondition to identity check ID document has to be verified as well in order to avoid false identity check if ID document is, for example, fake. In order to verify user's identity person picture from verified ID document is used and compared with taken selfie. A result of identity verification is kept together with ID document.

* **Improvements:**
	* introduce 3rd party independent process

### BFU-0300603: Waive user's identity check
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|inDevelopment|0|Jumio, Onboarding|OP|

It allows operator to overcome identity verification issue by waiving result of identity verification process. Operator can correct extracted data and compare pictures manually.  
System differentiates between system verification status and operator verification status.

### BFU-0300604: Update proof of identity document
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|NEW|1|Jumio, Onboarding|OP|

It allows user to update POI document data and attachments in order to do some correctness. 

### BFU-0300607: ID documents overview
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|DONE|0.1|Jumio, Onboarding|OP|

It allows user to see POI document data.

* **Improvements:**
	* ID documents history
	* add attachments view
	* Labels - Stolen, expired ...

### BFU-0300608: ID documents expiration check
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|NEW|1|Jumio, Onboarding|OP|

It allows user to solve issue with expired POI document. System watcher.

### BFU-0300606: Request for new POI doc
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|inDevelopment|0|Jumio, Onboarding|OP, CUS|

It allows operator to request new POI document capture as well as identity verification in case that identity verification went wrong.  
Requested user is requested for upload and see operator message with instruction what was wrong.

* **Improvements:**
	* ID documents history
	
### BFU-0300605: Parametrize POI document types
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|DONE|0.1|Jumio, Onboarding|OP|

It allows to configure what type of POI document is managed.

## BFR-03013: KYC
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|inDevelopment|-|Trulioo, Onboarding|OP|Trulioo

It allows to run KYC check for given person. KYC is verification of person by 3rd party resources (not owned by person). As result system expect simple decision in form of Match / NoMatch. Processed KYC check are registered in person risk profile TODO(add link)

* **Improvements:**
	* introduce 3rd party independent process (upload protocol)

### BFU-0300605: Process KYC
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|inDevelopment|-|Trulioo, Onboarding|OP|Trulioo

KYC check starts with composing request based on defined set of person's data like Name, DOB, address. Result is checked in order to follow once any issue happens.

* **Improvements:**
	* Regular KYC

### BFU-0300605: Waive KYC

|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|inDevelopment|-|Trulioo, Onboarding|OP|Trulioo

It allows operator to overcome KYC issue by waiving result of KYC process. 
System differentiates between system verification status and operator verification status.


## BFR-03013: Person AML
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|NEW|-|Onboarding|OP|

It allows to run AML check for given person. Goal of AML check is to check within 3rd party resources whether person is risky from money laundering perspective as well as politically exposed person (PEP). As result system expect simple decision in form of Match / NoMatch. Processed AML check are registered in person risk profile TODO(add link)

### BFU-0300605: Process Person AML

KYC check starts with composing request based on defined set of person's data like Name, DOB, address. Result is checked in order to follow once any issue happens.

* **Improvements:**
	* Regular person AML

## BFR-03009: Risk profile mngt
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|InDevelopment|-|Onboarding, Risk profile|OP|

This feature provides management of party risk information. Most important is overall party risk level which is determined based on bank policy and results of defined risk check and another party related data.

### BFU-0300901: Parametrize risk checks
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|InAnalysis|-|Onboarding, Risk profile|OP|

It allows to configure types of risk check to register in customer risk profile. For every risk type a result value and type, provider and risk check country can be configured.  
One built-in check type is overall risk which result is enumeration of three values. Medium, Low, High (It can be changed).  
Overall risk determination bank policy is always coded based of bank specific policy and plugged in. 

### BFU-0300902: Add risk check
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|InDevelopment|-|Onboarding, Risk profile|OP|

System process which carries on risk checks (AML, KYC, PEP ..) register processed check into Risk profile with a risk check result, risk check protocol (binary document from 3rd party service), Reference to external process in 3rd party service, provide - 3rd party service / operator name (if overridden by operator)

### BFU-0300903: Override overall risk level
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|InAnalysis|-|Onboarding, Risk profile|OP|

System allows user to to overcome overall risk level in case that operator requires to change outcome which is determined by bank policy. 

### BFU-0300904: Risk check overview
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
| InAnalysis|0|isk profile |OP|

It allows user to see list of processed risk checks, risk check provider, protocol and result. Risk check history.

## BFR-03012: Search customer
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|DONE|1|SVC|OP,CUS|

This feature provides full-text search between defined customer data. Search result can be filtered based on party labels.

* **Improvements:**
	* Search over DOB returns different format of DOB
	* Elastic search as common search function across business domains

### BFU-0301201: Configure customer search
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|DONE|1|SVC|OP,CUS|

It allows to configure what customer data will be searchable and what labels can be used in filter.

## BFR-03005: Party relations mngt
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|New|-|Onboarding, SVC|OP|

This feature covers functionality of relations between different parties and its history. Mainly to set-up family relationships, business relationships and controlled vs controlling relations.   
Relations could be with or without direction. 
Business relations which connect two parties (like, Owner-Disponent or Investor-advisor) over some product or service are not in scope of this business domain.

### BFU-03005001: Add / Remove party relation
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|New|-|Onboarding, SVC|OP|

It allows system or user to manage party relations. One party can have more relations. 

### BFU-03005001: Parametrize party relations type
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|New|-|Onboarding, SVC|OP|

It allows to configure what types of relationship can be used.

**Improvements:**

* To be analysed and implemented 
* FE configuration


## BFR-03007: Party segmentation
Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|New|-|Onboarding, SVC|OP|

It allows user or system processes to set party segments. One party can have one or more segments. 

### BFU-03007001: Add / Remove segment
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|New|-|Onboarding, SVC|OP|

It allows system or user to manage party segments. One party can have more segments. 

### BFU-03007002: Parametrize party relations type
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|New|-|Onboarding, SVC|OP|

It allows to configure what types of segments can be used.

## BFR-03008: Party deduplication mngt
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|New|-|SVC|OP|

This feature mitigate duplicated parties in the system. It could happen that given party is on-boarded more times but goal is to have only one record for given party.

### BFU-0300801: Detect duplicites
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|New|-|SVC|OP|

It allows user to detect duplicities based on pre-defined rules, within party portfolio and start mitigation process.  

### BFU-0300802: Merge duplicity
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|New|-|SVC|OP, system|

It allows user to merge duplicity based on pre-defined rules or user decision.   
Process has to ensure that all relationships (products, transactions) already built in system is updated.

### BFU-0300803: Split duplicity
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|New|-|SVC|OP, system|

It allows user to split duplicity based on pre-defined rules or user decision.  
Process has to ensure that this duplicity will never more be detected by system.

### BFU-0300704: Parametrize deduplication

It allows to configure rules for duplicity detection like attributes to compare and rate for findings.  
It allows to configure rules for automatic merge and split.

## BFR-03010: Consent mngt
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|New|-|SVC, Onboarding|OP, CUS|

System supports various type of users consents for user data processing. There are more types of consents which differs based on lawful basis organisation uses.These could be Consents, Contracts + Terms & conditions, Legitimate interests. 
System allows granted consents management.  
System allows to configure what consents and when should be accepted with what content.
System provides overview of granted consents and history.


## BFR-03011: Party document mngt
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|New|-|SVC, Onboarding|OP, CUS|

System supports overview of party documents especially for documents which are not related to supported business feature e.f. Death certificate, Divorce certificate and so on. 

### BFU-0301101: Party document overview
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|New|-|SVC|OP, CUS|

It allows user to see list of documents and open all its attachments. Document detail contains information about when and by who document was uploaded.

### BFU-0301102: Upload party document
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|New|-|SVC|OP, CUS|

It allows user to upload new document and fill in basic metadata.

### BFU-0301103: Remove party document
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|New|-|SVC|OP, CUS|

It allows user to remove uploaded document. 

### BFU-0301104: Parametrize document types
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|New|-|SVC|OP, CUS|

It allows user tor system to configure what types of documents can be uploaded manually.

## BFR-03011: Party offboarding
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|New|-|SVC|OP, CUS|

It allows to off-board party data when relationship with bank is terminated. The process depends on state of party's lifecycle.  
TODO(User account deactivation function)  
Party is labeled as off-boarded and Party data is removed when all conditions are met.

## BFR-03013: Parametrize tenant
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|New|-|System|OP|

It allows to configure organisation (financial institution) data - address, Name, CIO so on, which can be used in various processes e.g. notifications 

## BFR-03014: Employments and Incomes
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|DONE|1|SVC|OP, CUS|

This feature provides ability to keep party sources of incomes.


### BFU-0301401: Create source of income
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|Done|1|SVC, OnBoarding|OP, CUS|

It allows user to create new source of income of given type and category with business validity and amount - it depends on bank policy whether gross or new amount will be stored.
TODO(List of attributes)

### BFU-0301402: Manage source of income
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|New|-|SVC|OP|

### BFU-0301403: Source of income overview
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|New|-|SVC|OP|

 ... + history


