Create Custom  objects and Fields (if not present)
Check if CareBenefitVerifyRequest__c and CoverageBenefit__c exist. If not:

-------------------------Step-1--------------------------------------------

Create CareBenefitVerifyRequest__c object with fields:
Field Label

Care_Representative_Name__c
Name
CreatedById
Date_of_Birth__c
Diagnosis_Code__c
External_Request_ID__c
Gender__c
Insurance__c(Member Plan)
LastModifiedById
OwnerId
Patient__c(account)
Patient_FirstName__c
Patient_LastName__c
Procedure_Code__c	
Provider__c (Account)
Provider_FirstName__c
Provider_LastName__c
Service_Date__c
Service_Type__c
Status__c
Status_Reason__c

 
Create CoverageBenefit__c object with:

Field Label
CareBenefitVerifyRequest__c
Coverage_Status__c
Coverage_Type__c
Name
CreatedById
LastModifiedById
Linked_Requests__c(CareBenefitVerifyRequest)
OwnerId
Status__c
Status_Reason__c

----------------------Step-2--------------------------------------------

Create Named Credentials(In classic version)

Go to Setup → Named Credentials

Click New Named Credential

Label: CareBenefitAPI

URL: https://infinitusmockbvendpoint-rji9z4.5sc6y6-2.usa-e2.cloudhub.io

Identity Type: Named Principal

Authentication Protocol: Password Authentication

Username: test_user

Password: test_password

Allow Callouts: ✅

Save.

----------------------------step-3-------------------------------------------
Apex Code Development

✅ 4. Create Apex Wrapper Class

📌 Developer Console → File → New → Apex Class → CareBenefitRequestWrapper


--------------------------------------------------------------------------------------------------------

Create Apex Class for Sending Request

📌 Developer Console → New → CareBenefitService
------------------------------------------------------------------------------------------------------------
 Create Trigger to assign it to queaue Request
 ----------------------------------------------------------------------------------------------------

 Create Trigger to Auto-send Request
 }

----------------------------------------------------------------------------------------------------
 REST API Endpoint to Receive Callback
 -----------------------------------------------------------------------------------------------------------
test class
----------------------------------------STEP-4--------------------------------------------------------
Use Workbench (Salesforce tool)
Steps:
Open: https://workbench.developerforce.com

Login with your Developer Org

Go to: Utilities → REST Explorer

Select POST method

Enter URL:

/services/apexrest/care-benefit-verification-results

Enter Request Body:

{
  "externalId": "12345",
  "status": "Acknowledged",
  "statusReason": "Approved by Payer"
}
