# BD-02: Identity, Authentication&Authorization mngt


## BFR-02001: User identity mngt
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|DONE|1|System|OP, CUS|-|

System differentiates three types of use accounts customer, operator, partner. This allows us to protect data from unauthorized access to customer data by different customer account then owner's one.  
Main responsibility is to manage user identities and their authentications.  
Our approach is to allow more then one user account for one party which means that when customer is also operator at same time then two user are introduced for one party.

### BFU-0200101: Create user account
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|DONE|1|System|OP, CUS|-|

During party onboarding process the user account is created. We  call it user registration. To create user account at least user name needs to be defined. 

### BFU-0200102: Activate user account
During party onboarding process the user account is activated. When user account has enrolled enough credentials to be able to authenticate itself then onboarding process activate it.

### BFU-0200103: Lock user account
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|DONE|1|System|OP, CUS|-|

It allows system to lock user account when locking user account policy is breached. Number of attempt to authenticate can be parametrized.   

### BFU-0200107: Unlock user account
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|DONE|1|System|OP, CUS|-|

It allows system to unlock locked user account by renew forgotten password process**ONLY**. 
* **Improvements:**
	* Unlock user account by operator

### BFU-0200104: Block/Unblock user account
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|NEW|-|System|OP|-|

It allows user hard-block user account so that it is not possible to login until it is unblocked by operator. Temporary blockage.  
Once blocked access token has to be invalidated.

### BFU-0200105: Deactivate user account
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|NEW|-|System|OP, System|-|

It allows to deactivate active user account in case that customer or operator is offboarded. User account can be activated back within defined time interval.  
Once deactivated access token has to be invalidated.

### BFU-0200106: Manage user name
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|NEW|-|System|OP, CUS|-|

It allows user to update user name when she requires. It has implication to contact mngt in case when email is required as user name.

## BFR-02002: Operator mngt
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|DONE|1|System|OP|-|

Feature supports whole operator user account management. There are used function from different features like whole [User identity mngt](#BFR-02001:-User-identity-mngt) and [Role assignment](#BFR-02001:-User-identity-mngt). 

### BFU-0200202: Search operator
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|DONE|1|System|OP|-|

It allows to search current operator in system via using full-text search within Operator party data.
* **Improvements:**
	* Search also via operator user account data like user name, phone, email

### BFU-0200202: Manage operator data
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|DONE|1|System|OP|-|

It allows to update operator's full-name.
* **Improvements:**
	* Update also data like user name, phone, email. It has implication to enrolled authentication details.

### BFU-0200202: Operator onboarding
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|DONE|1|System|OP|-|

It allows to create and activate new operator. It can be configured from which step the process is configured by authentication scenario for createOperator operation.  
Now email address is used as user name.  
It is required that operator which is being created has to have at least one role assigned before first step is started.
* **Improvements**
	* Move configuration of the process from authetication acenarios to user activation.
	* Zero rights check 

### BFU-0200202: Deactivate operator
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|DONE|1|System|OP|-|
It allows to deactivate active user account in case that operator is offboarded.

* **Improvements**
	* Once deactivated access token has to be invalidated.
	* User account can be activated back within defined time interval.  

## BFR-02003: Authorization scenarios
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|DONE|1|System|OP,CUS|-|

It provides multi-step authentication and enables to use multi-factor authentication. Potentially every operation in system can be authorized by various steps and factors.  
* **Improvements**
	* Smart scenario determination. System offers user only scenarios of which authentication details can be used in accessing channel.

### BFU-0200301: Parametrize scenarios
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|inDevelopment|0.1|System|SYSTEM|Waiting for AA refactor| 

It allows configure which operation will be authorized by which scenarios. One operation can have more scenarios. It can be configured which authentication details are included in given scenario and what is an ordering of steps. 
* **Improvements**
	* introduce parametrisation according to ADR (translations and so on)

### BFU-0200305: Initiate & Process scenario
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|DONE|1|OP,CUS|SYSTEM|Waiting for AA refactor| 

When system determines that being processed operation needs to be authorized by some scenario(s) system determines what scenario(s) suits for the user.  
When user choses and starts a scenario system validates every step and once the scenario is finished an operation is allowed to be processed. 

## BFR-02006: User access

### BFU-0200303: Login
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|DONE|1|System|OP,CUS|Waiting for RR refactor| 

Login is operation which is special and always requires in its scenario authentication detail so that system can unique identify user. Once scenario is validated a access token is created.  
System supports account lock when parametrized number of attempt is exceeded.
* **Improvements**
	* Authenticated user management integration

### BFU-0200304: Logout
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|DONE|1|System|OP,CUS|Waiting for RR refactor| 

Login is special operation invalidates access token so that user requests is not processed anymore.
* **Improvements**
	* Authenticated user management integration

## BFR-02004: Authentication/Authorization details

|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|DONE|1|System|OP|Waiting for AA refactor|

There is two types of detail. Authentication type of a detail allows system to determine user identity of accessing person.  
Authorization type verifies that the person who claims to be identity owner is identity owner.
* **Improvements**
	* Auth. details overview in customer and BackOffice applications 

### BFU-0200401: Parametrize authentication details
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|NEW|-|System|OP|Waiting for AA refactor|

It allows to configure what auth. details can be configured and used.
* **Improvements**
	* introduce parametrisation according to ADR (translations and so on)


### BFU-0200402: Phone number
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|DONE|1|System|OP,CUS|Waiting for AA refactor|

It allows system to generate and validate OTP  which is send to user mobile number defined for auth. detail. It can be parametrized 
* how often user can repeat sending OTP.
* What OTP can be generated (Dictionary, Numbers, Characters) 
* Haw long is valid
* TODO - what else?

### BFU-0200402: Email link
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|DONE|1|System|OP,CUS|Waiting for AA refactor|

It allows system to generate and validate https link which is send to email address number defined for auth. detail.
It can be parametrized
* how often user can repeat sending a link.
* Haw long is valid
* TODO what else?


### BFU-0200403: Password 
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|DONE|1|System|OP, CUS|Waiting for AA refactor|

It allows system to keep and validate users passports in secured way (TODO-Method).
It can be parametrized
* how often user has to update password (TODO-check)
* Password policy is enforced by configured regular expression.
* TODO - what else?

### BFU-0200409: Change Password
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|DONE|1|System|OP, CUS|Waiting for AA refactor|

It allows to change password for authenticated users only.

### BFU-0200404: User name
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|DONE|1|System|OP, CUS|Waiting for AA refactor|

Authentication detail used for identification of user account. Email address is very often used as User name as it is easily remembered by users. It has to be unique over all user accounts.
* **Improvements**
	* introduce another user name which is not subject of change as email address is so that we can shere it with systems which are exclusively used for managing specific mainly biometric auth. details.

### BFU-0200405: OnDeviceBiomentric
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|DONE|1|System|OP, CUS|Waiting for AA refactor|

Auth. detail used for validation mobile device token which is generated by Leveris system during onboarding, stored in mobile device secured storage and taken from that based on ondevice fingerprint authentication during login. It is  valid only on combination with registered device ID.
* **Improvements**
	* introduce better security of of device token enrollment during onboarding. Now, attacker familiar with onboarding process can let system to generate his device token and then use for login into system. 

### BFU-0200407: Device
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|DONE|1|System|OP, CUS|Waiting for AA refactor|

Device ID is auth. detail which is in in pair with a device token device ID has to be unique in context of identity. During onDeviceBiomentric fingerprint authentication device ID is validated together with device token. 

### BFU-0200406: 4F Biometric
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|InDevelopent|1|System|OP, CUS|Waiting for AA refactor and partnership with Veridium|

Auth. detail which validate user's four fingers biometric which is very secure. Enrollment is done is onboarding process where biometric data are captured and stored.


### BFU-0200408: Voice Biomentric
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|inAnysis|1|System|OP, CUS|Waiting for AA refactor and partnership with Solgari|

Auth. detail which validate user's voice. Enrollment is done is onboarding process where biometric data are captured and stored.

### BFU-0200408: Passcode
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|inAnysis|1|System|OP, CUS|Waiting for AA refactor and partnership with Solgari|

Auth. detail which validate user's passcode. Enrollment is done during onboarding process when Passcode is set by user. It is  easy-to-remenber 4-6 digits long number which is used in multi-step authentication to authorize sensitive operations e.g. Send funds especially on mobile devices.

## BFR-02005: Device mngt
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|inAnysis|0.1|System, SVC|OP, CUS|-|

It allows user to keep and manage their mobile devices(s) used for accessing system services. First device is enrolled during onboarding process. Currently we can store only one device.
* **Improvements**
	* Devices overview in customer and BackOffice applications 

### BFU-0200501: Enroll device
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|inAnysis|0.1|System|OP, CUS|-|

It allows user to enroll device during onboarding process. Currently we can store only one device. System keep basic information about device so that user can recognize it. External device ID is expected as input parameter from device. Device is has to be unique in context of user identity.
* **Improvements**
	* introduce option to add more devices and solve an issue with lost phone

### BFU-0200502: Block device
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|NEW|-|Customer, SVC|OP, CUS|-|

It allows user to block device in case that is lost or stolen but there is a possibility that can be returned.

### BFU-0200503: Remove device
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|NEW|-|Customer, SVC|OP, CUS|-|

It allows user to remove device in case that is lost or stolen or not used anymore.

### BFU-0200504: Update device data
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|NEW|-|Customer, SVC|OP, CUS|-|

It allows user to update device name and so on.

### BFU-0200505: Parametrize devices
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|NEW|-|Customer, SVC|OP, CUS|-|

It allows configure what type of devices can be enrolled TODO(What else? Do we really need it?) to update device name and so on.

## BFR-02006: Shared devices
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|NEW|-|Customer, SVC|OP, CUS|-|

It allows more user to use one device if a device supports more users like iPad.
