# AWS Key Management Service, MSFT Key Vault, GCP KMS

Azure Key Vault helps solve the following problems:

1. Secrets Management - Azure Key Vault can be used to Securely store and tightly control access to tokens, passwords, certificates, API keys, and other secrets
1. Key Management - Azure Key Vault can be used as a Key Management solution. Azure Key Vault makes it easy to create and control the encryption keys used to encrypt your data.
1. Certificate Management - Azure Key Vault lets you easily provision, manage, and deploy public and private Transport Layer Security/Secure Sockets Layer (TLS/SSL) certificates for use with Azure and your internal connected resources.

Methods used to secure are 2:
1. `Standard` which uses software key
1. `Premium` which uses hardware key (more secure than software key)

## Why do we need this?
1. Removes the responsibility for the developer to manage and store keys of the application. Hence the application need not have the keys as part of code.
1. Application/Databases can securely access the keys/conn strings using URI. URI also allows applications to access diffrent version of keys from the vault.

## How the keys are accessed?

Application needs proper authentication by Azure AD and authorization from Azure IAM RBAC to access the keys.
Azure key vaults are FIPS(Federal Information Processing Standards) compliant.

Key vaults can also export the accesses to keys to an event hub or could be monitored in Azure Monitor Logs. You could restrict or delete logs when you dont need them.
Benefits also are for Data replication, failover etc

## Identity provider experience (Okta, PingFederate, OneLogin, ADFS, Azure AD, etc.)

### Azure AD

!()[./images/identities.png]

### How access management works in Azure AD

Azure AD helps you give access to your organization's resources by providing access rights to a single user or to an entire Azure AD group.
Using groups lets the resource owner (or Azure AD directory owner), assign a set of access permissions to all the members of the group, instead of 
having to provide the rights one-by-one. The resource or directory owner can also give management rights for the member list to someone else, 
such as a department manager or a Helpdesk administrator, letting that person add and remove members, as needed.

#### Ways to assign access right

1. Direct Assignment: Resource owner directly assigns a resource to user.
1. Group Assignment: Resource owner creates a group and all members of the group have access to the resource. Group members can be managed by both
Resource Owner and Group Owner.
1. Rule Based assignment: Resource owner creates a group and uses a rule to allow which users have access which resource. Ex: Create a dynamic group and have rule to access resource to all members of a specific group.
1. External authority: Uses an on premise AD to allow access.
