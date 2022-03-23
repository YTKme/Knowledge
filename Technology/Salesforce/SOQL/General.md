# Git

## User

```sql
-- Generic Active User
SELECT Id, FirstName, LastName, Name, Email, FederationIdentifier, IsActive, LastLoginDate, CreatedDate, Profile.UserLicense.Name, Profile.Name
FROM User
WHERE IsActive = true

-- Generic Active User (Not Login For 45 Days)
SELECT Id, FirstName, LastName, Name, Email, FederationIdentifier, IsActive, LastLoginDate, CreatedDate, Profile.UserLicense.Name, Profile.Name
FROM User
WHERE IsActive = true
    AND Profile.UserLicense.Name = 'Salesforce'
    AND LastLoginDate < LAST_N_DAYS:45

-- Production Active User
SELECT Id, Username, Email, FederationIdentifier, FirstName, LastName, Name, FullName__c, IsActive, LastLoginDate, CreatedDate, User_License__c, Profile.Name, isGenericUser__c
FROM User
WHERE IsActive = true

-- Production Active User (Not Login For 45 Days)
SELECT Id, Username, Email, FederationIdentifier, FirstName, LastName, Name, FullName__c, IsActive, LastLoginDate, CreatedDate, User_License__c, Profile.Name, isGenericUser__c
FROM User
WHERE IsActive = true
    AND User_License__c = 'Salesforce'
    AND LastLoginDate < LAST_N_DAYS:45
```

## Permission Set

```sql
SELECT p.Assignee.Name, p.Assignee.ID, p.Assignee.UserRole.name, p.PermissionSet.Label, p.PermissionSet.ID
FROM PermissionSetAssignment p
WHERE p.PermissionSet.IsOwnedByProfile = false
ORDER BY p.AssigneeId, p.PermissionSetId

-- User With Permission Set
SELECT Id, PermissionSetId, PermissionSet.Name, PermissionSet.ProfileId, PermissionSet.Profile.Name, AssigneeId, Assignee.Name, Assignee.Email, Assignee.Username
FROM PermissionSetAssignment
WHERE PermissionSet.Name = '<PermissionSetName>'
```

## Async Process Queue

```sql
-- 
SELECT Process__c, count(Id)
FROM Async_Process_Queue__c
WHERE CreatedDate = TODAY
GROUP BY Process__c
ORDER BY count(Id) DESC
```

## Schedule Apex

```sql
-- Schedule Apex Job With Owner
-- The `JobType` of `7` is Schedule Apex
-- https://developer.salesforce.com/docs/atlas.en-us.api.meta/api/sforce_api_objects_cronjobdetail.htm
SELECT CronJobDetail.Name, CronExpression, OwnerId
FROM CronTrigger 
WHERE CronJobDetail.JobType = '7'
    AND OwnerId='<OwnerID>'
```

```java
// All Scheduled Classes
List<CronTrigger> ct = [Select Id, CronJobDetail.Name FROM CronTrigger];
List<AsyncApexJob> aj = [SELECT ApexClass.Name, CronTriggerId FROM AsyncApexJob WHERE JobType IN ('ScheduledApex')];

for (CronTrigger c : ct) {
    for (AsyncApexJob a : aj) {
        if (c.Id == a.CronTriggerId) {
            System.debug(c.CronJobDetail.Name + ' = ' + a.ApexClass.Name);
            break;
        }
    }
}
```

## Integration Setting

```sql
-- Integration Setting Backup
SELECT Id, API_Key__c, Certificate__c, Enable_Logging__c, Endpoint_Server__c, Endpoint_URI__c, HTTP_Headers__c, HTTP_Method__c, ImsAudience__c, ImsClientId__c, ImsClientSecret__c, ImsIssuer__c, ImsScope__c, ImsSubject__c, Ims_Access_Token_Cache__c, Ims_Integration_Setting__c, LastModifiedById, LastModifiedDate, Name, Timeout__c, User_Name__c
FROM Integration_Setting__c
```