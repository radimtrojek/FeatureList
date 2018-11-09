# BD-01: Roles, Right, Authenticated user mngmt (business domain)

## BFR-01001: Rights & Roles mngt (Business feature)
This feature provides protection against unauthorized access to Back-office applications functions and data. In general it follows Role-Based-Authorization approach.
* **Improvements:**
	* introduce more types of roles - Business access role and Administration access role so that business functions and system administration functions can be controlled separately.

### BFU-0100101: Create role (Business function of feature)
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|Done|1|Roles|

It allows user to create new role(s) and setup up access rights according to organization security policy. 

### BFU-0100102: Remove role
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|Done|1|Roles|

It allows user to remove role regardless it is assigned to user in system or not. Once role is removed all affected users lost included access  permissions. 

### BFU-0100102: Setup permissions
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|Done|1|Roles|

It allows user to add access permissions to a role. Every added permission can be configured whether protected function is allowed or forbidden.
* **Improvements:**
	* Business oriented access rights
        * Use domains instead of MW apps (Loan, Task, Onboarding)
        * Manage role together with rights from person perspective
            * possibility to see
                * roles
                * Source of right (list of roles, direct assignment)
	* access rights removal	- Main menu in BO app is not driven by this permission

### BFU-0100103: Role Assignment
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|Done|1|Roles, Operators|

It allows user to assign or unassign a role(s) to/from a user. 
* **Improvements:**
	* Bulk assignments
	* List of role assignments per user

### BFU-0100104: Individual permissions
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|in analysis|-|Roles, Operators|OP|It waits to RR refactor|

It allows user to assign/unassign access permission directly to a user (role is omitted). This setup has impact on access rights evaluation process

### BFU-0100105: Rights parametrisation
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|inDevelopment|0.1|System|OP|It waits to RR refactor|

It provides parametrisation function which can be used by others system modules or applications to configure their permissions for their operations.
* **Improvements:**
	* introduce parametrisation according to ADR (translations and so on)

### BFU-0100106: Business access role
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|NEW|-|Role|OP|It waits to RR refactor|

Role in the system which allows to manage / use business functions but not admin functions. It is possible to manage business type of access roles.

### BFU-0100107: System administrator role
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|NEW|-|Role|OP|It waits to RR refactor|

Role in the system which allows to manage use admin functions but not business functions. It is possible to create "business user" but not to manage business type of access roles.

### BFU-0100108: Initial admin setup
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|NEW|-|Installer|OP|It waits to RR refactor|

It allows system administrator to setup initial admin credentials during system deployment. Initial admin gets system administrator role by design.


## BFR-01002: Rights Evaluation
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|NEW|1|System|OP|It waits to RR refactor|

This feature allows system to determine whether user can access given function. In general the approach is what is not allowed is forbidden. What is explicitly forbidden is forbidden even if it is allowed from different assigned role.
* **Improvements:**
	* Not to transmit whole user access right configuration in every request and built single place for evaluation in real-time.
	* Zero role assignment scenario is not solved

## BFR-01003: Authenticated users mngt
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|NEW|-|System|OP, CUS|It waits to RR refactor|

### BFU-0100301: Check access token
It allows system to check whether request was issued by authenticated user or simply whether an access token is still valid.

### BFU-0100302: Invalidate access token
It allows system to invalidate access token when token is expired or user makes logout.

### BFU-0100303: Prolong access token
It allows system to prolong access token when user is active so that she can smoothly use application.

### BFU-0100304: Issue access token
It allows system to issue access token when user is authenticated (logged in).

## BFR-01004: Segments rights
* This will be solved by [FO application](https://uu04c4.axshare.com/#g=1&p=00_login_page) concept.


## BFR-01005: Sensitive data rights
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|NEW|-|System|OP|-|

### BFU-0100501: Sensitive data paramerisation
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|NEW|-|System|OP|-|

It allows user to configure what party data are sensitive or not.

### BFU-0100502: Sensitive data protection
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|NEW|-|System|OP|-|

It enable possibility to evaluate sensitive data and protect it against misuse.

### BFU-0100503: Show sensitive data
|Status|Version|Supported applications|Consumers|Note|
|------|------|-----------|-------------|---------------------|
|NEW|-|System|OP|-|

It allow to request and show protected sensitive data based on defined authorization.
