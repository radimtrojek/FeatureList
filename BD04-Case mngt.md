<span style="color:blue"> **!!!! TODO - instert links to BD03-PartyMngmt.md and BD02-Identity_Authentication_Authorization_mng as Case mngt uses their features a lot.** </span>

# BD-04: Case mngt
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|Done|1|OnBoarding|OP, CUS| 

Some more complex bank processes which are spread across business domains, long-running and differs per banks and countries insists system support to manage such processes. Example of such process is Party (customer) onboarding process.   
We call instance of the process in the system as case.  
Main goal of the case management is ability to configure type of cases and manage case flow. Basic unit of case is step which either user or system needs to process. Every step outcome has to fulfil defined success criteria to move forward.
Some steps are configured in main course of process some are waiting to be invoked based on events as parallel step to main course of the process.  
Case has also its own lifecycle which is inProgress, Done, Rejected, Canceled.

* **Improvements:**
	* 	parallel sub-processes e.g. KYC and AML is processed in same time and has to be finished successful in order to establish back account
	*  configure another type of case

## BFR-04001: New customer registration

### BFU-0400101: Start onboarding case step
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|Done|1|OnBoarding|OP, CUS| 

This allows user to start onboarding process. It is formulary step where user need to fill in some basic party data. Formulary is generic so collected fields can be configured.  
System creates party with label "Lead" and unverified primary contact (if collected), user identity (account) which is inactive with email address as user name and email address auth. detail. 

### BFU-0400102: Email verification step
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|Done|1|OnBoarding|OP, CUS| 

This allows user to verify existence and ownership of email address by sending verification link to collected email address. Email address can be re-send or update in case that verification link does not arrive.  
An output is verified email address.

* **Improvements:**
	* 	when email address is not available step is able to collect it from user itself


### BFU-0400103: Phone number verification step
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|Done|1|OnBoarding|OP, CUS| 

This allows user to verify existence and ownership of phone number by sending one time code to collected phone number. Phone number can be re-send or update in case that OTC does not arrive.
An output is verified phone number and auth. detail type of OTP.

### BFU-0400104: Residency country check
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|Done|1|OnBoarding|OP, CUS| 

This feature allows bank to check whether customer lives in a country where bank operates. It is important check as online and mobile services are accessible world-wide.
In case of not allowed country user can be informed about possible rollout and its data can be used for MIS. 

* **Improvements:**
	* more countries support which will have impact to ID document and POA document capturing.

### BFU-0400105: Security setup - Password
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|Done|1|OnBoarding|OP, CUS| 

This function customer to set password as auth. detail.

### BFU-0400106: Security setup - Passcode
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|NEW|-|OnBoarding|OP, CUS|

This function allows user to set passcode as auth. detail.

### BFU-0400107: Security setup - Fingerprint biometric
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|DONE|1|OnBoarding|OP, CUS|

This function allows system to establish an on-device biometric auth. detail.

### BFU-0400108: Security setup - Mobile device

|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|DONE|1|OnBoarding|OP, CUS|

This function allows system to establish an device as auth. detail

### BFU-0400109: Security setup - 4F

|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|DONE|1|OnBoarding|OP, CUS|

This function allows system to establish an 4F as auth. detail.

### BFU-0400110: Security setup - VOICE

|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|DONE|1|OnBoarding|OP, CUS|

This function allows system to establish an user's voice as auth. detail.


### BFU-0400111: Activate user account

|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|DONE|1|OnBoarding|OP, CUS|

This function allows system to activate user account so that user can login from this moment.

* **Improvements:**
	* 	user account cannot be activated until all auth. details for login scenario can be processed.
 
## BFR-03004: Due diligence

### BFU-0300401: Identity verification step
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|DONE|1|OnBoarding|OP, CUS|

In this step proof of identity (ID document) is captured as well as selfie of user and then identity check is performed.
As output from this step is ID document, extracted personal data and identity check result.

### BFU-0300402: Identity verification evaluation
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|DONE|1|OnBoarding|OP, CUS|

Once identity check is performed system evaluates whether an output is successful or not based on defined validation rules like all required data is extracted, ID document is valid.  
Extracted data updates party data.  
In case not-successful scenario task is created to solve and issue.

* **Improvements:**
	* parametrize validation rules

### BFU-0300403: Address extraction step

|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|DONE|1|OnBoarding|OP, CUS|

In this step proof of address is captured and address extraction is performed.
As output from this step is POA document, extracted address.

### BFU-0300404: Address extraction evaluation
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|DONE|1|OnBoarding|OP, CUS|

Once address extraction is performed system evaluates whether an output is successful or not based on defined validation rules like all required data is extracted, POA document is not too old.  
In case not-successful scenario task is created to solve and issue.  

During output processing system evaluates whether country of address is same as party residence country. In case that address country has not been extracted there is an configurable rule whether an issue is raised or address country is taken from party residence country.

* **Improvements:**
	* parametrize validation rules

### BFU-0300405: Address approval and cleansing step

|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|DONE|1|OnBoarding|OP, CUS|Trulioo

This step is submitted every time once POA is successfully extracted and case is in given status. Main goal of this step is to convert extracted data into well-formatted address and verify that address exists. 

* **Improvements:**
	* 3rd party independent process


### BFU-0300406: KYC
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|DONE|1|OnBoarding|OP, CUS|

KYC step is performed once all required data are collected. Until required data is available this step sleeps and waring for event announcing that some data arrived  

### BFU-0300407: AML
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|NEW|1|OnBoarding|OP, CUS|

KYC step is performed once all required data are collected. Until required data is available this step sleeps and waring for event announcing that some data arrived 
  
## BFR-03004: Product application

|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|DONE|1|OnBoarding|OP, CUS|

This step ensure that all configured financial product to offer is offered to customer and customer has option to apply for them.  
In case that there is only one product required to open after successful onboarding then it is processed automatically without waiting for customer input.

* **Improvements:** 
	* introduce validation that all required conditions was fulfilled before product application step is started. 


## BFR-03005: Reject case
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|NEW|1|OnBoarding|OP, CUS|

In case that during customer approval process operator decides not to onboard given party then case is rejected. Reject process ensure that personal data are cleared and user account is deactivated as well as rejected party is informed.


## BFR-03006: Cancel case
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|NEW|1|OnBoarding|OP, CUS|

In case that being on-boarded party decides not to continue with the onboarding. Cancel case process ensure that personal data are cleared and user account is deactivated as well as rejected party is informed.

## BFR-03007: Search case
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|DONE|1|OnBoarding|OP, CUS|

Search party feature is used to search cases. TODO (LINK)

* **Improvements:**
	* filtering per case type and status

## BFR-03008: Case log tool
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|DONE|0.1|OnBoarding|OP, CUS|

It allows every activity which related to case to report into case log so that operator can see how particular case is progressing over time.
Inserted data is completely up to every activity but structure is - Activity status, activity name, provider (Operator / 3rd party provider name), date-time.

### BFU-0300801: Create case-log record
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|Done|1|SVC, OnBoarding|OP, CUS|
It allows process to create record in case log

### BFU-0300802: Get case-log record list
Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|Done|1|OnBoarding|OP, CUS|

## BFR-03009: Onboarded party duplicity check
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|NEW|-|OnBoarding|OP, CUS|

### BFU-0300X02: User name duplicity check
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|NEW|-|OnBoarding|OP, CUS|

This duplicity check allows system to detect that party with same user name is onboarding. In this case user with same user name is informed via notification and onboarding party is not allowed to continue. 

### BFU-0300X02: ID duplicity check
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|NEW|-|OnBoarding|OP, CUS|

This duplicity check allows system to detect that party with same ID is onboarding. In this case issue in form of task is created and operator has to make a decision what how to proceed. Onboarding party is not allowed to continue. 

### BFU-0300X02: KYC duplicity check
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|NEW|-|OnBoarding|OP, CUS|

This duplicity check allows system to detect that party with same name and address is onboarding (After KYC data are verified) . In this case issue in form of task is created and operator has to make a decision what how to proceed. Onboarding party is not allowed to continue. 

## BFR-03010: Case task mngt
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|NEW|-|OnBoarding|OP, CUS|

It allows to show task which are only related to given case on case detail.

## BFR-03011: Case progress bar
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|NEW|-|OnBoarding|OP, CUS|

It allows to show in which step(s) and phase given case currently is and what was already processed.


## BFR-03012: Joint onboarding case

|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|NEW|-|SVC, OnBoarding|OP, CUS|

It allows to invite another party to onboard in case that joint financial products are offered.
System ensures that there will be no duplicity processes for same person.  
System has to ensure that joint product can opened until all conditions for all applicant is met.


## BFR-03013: SLA process mngt
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|NEW|-|SVC, OnBoarding|OP, CUS|

This feature allows to configure and show how long given step in case can take. It is important for customer to know how long some background or back office checks can take.
 
## BFR-03014: Case parametrisation

### BFU-0301402: Configure case steps
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|inDevelopment|0.1|SVC, OnBoarding|OP, CUS|

It allows to configure from which steps case is composed of.  
Some steps can be configured as add-hoc steps which starts based on some events which can happen during process.

* **Improvements:**
	* GUI
	* Channel steps - some step are channel free, some are channel specific
	* Sub-processes - alternative scenarios (Request for new document / data)
	* Ensure that given step is not started until required steps are not finished.

### BFU-0301402: Configure supported countries
|Status|Version|Supported applications|Consumers|Note|
|------|------:|-----------|-------------|---------------------|
|inDevelopment|1|SVC, OnBoarding|CUS|Only basic functionality

It allows to configure which residence countries party has to be from.
