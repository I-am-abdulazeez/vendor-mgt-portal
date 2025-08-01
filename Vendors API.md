# Vendor Registration API : call the APIs using POST only

## Base URL

http://bctest.arm.com.ng:7248/BCAPI/ODataV4/

## POST /VendorAPIHandler/Getvendors 

http://bctest.arm.com.ng:7248/BCAPI/ODataV4/VendorAPIHandler_GetVendors

## POST /VendorAPIHandler/Createvendor 

http://bctest.arm.com.ng:7248/BCAPI/ODataV4/VendorAPIHandler_CreateVendor

## POST /VendorAPIHandler/GetVendorInfo

http://bctest.arm.com.ng:7248/BCAPI/ODataV4/VendorAPIHandler_GetVendorInfo



### JSON Array Parameters
*Note: These parameters require JSON arrays to be converted to JSON strings before API call*

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `directorsJson` | string | Yes | JSON string of directors array with Role, NameofDirector, Position, PhoneNo, Email, DateOfBirth, PercentageOfShareholdings, NumberOfShareholdings |
| `guarantorsJson` | string | No | JSON string of guarantors array with Name, Address, PhoneNo, Email, HomeAddress |
| `bankDetailsJson` | string | Yes | JSON string of bank details array with BankName, BankAccountNumber, AccountType, BeneficiaryName, etc. |
| `clientReferencesJson` | string | No | JSON string of client references array with companyName, startDate, endDate, location, contractValue, clientName, clientPosition, clientContact |




## Usage Example

username: APIUSER

password: Astr0b0y@2025

Company : ARMIMT-Test

Authentication: Basic Auth
### CreateVendor
```parameters
{
  "vendorNo": "V0019",
  "vendorName": "BrightLink Tech Ltd",
  "vendorRegType": 3,
  "vendorClassificationType": 3,
  "address": "23 Glover Rd",
  "address2": "Suite 4A",
  "city": "Ikoyi",
  "countryRegionCode": "NG",
  "phoneNo": "+2348098765432",
  "mobilePhoneNo": "+2347012345678",
  "email": "info@brightlink.com",
  "rcNumber": "RC789654",
  "tin": "98765432100",
  "payerId": "98765432100",
  "vatRegistrationNo": "VAT9988776",
  "objection": true,
  "objectionReason": "Just testing to see",
  "numberOfEmployees": 45,
  "incorporationDate": "2016-03-15",
  "armContactDept": "Digital Team",
  "referenceDocument": "https://short.io/id.png",
  "idCardUrl": "https://short.io/id.png",
  "locationEvidenceUrl": "https://short.io/loc.pdf",
  "hasNigerianCompany": true,

  "directorsJson": "[{\"Role\":\"2\",\"NameofDirector\":\"Shade\",\"Position\":\"Manager\",\"PhoneNo\":\"0902635255\",\"Email\":\"shade@gmail.com\",\"DateOfBirth\":\"1999-12-04\",\"PercentageOfShareholdings\":20,\"NumberOfShareholdings\":5}, {\"Role\":\"2\",\"NameofDirector\":\"Shade\",\"Position\":\"Manager\",\"PhoneNo\":\"0902635255\",\"Email\":\"shade@gmail.com\",\"DateOfBirth\":\"1999-12-04\",\"PercentageOfShareholdings\":20,\"NumberOfShareholdings\":5}]",

  "guarantorsJson": "[{\"Name\":\"Qudus\",\"Address\":\"Euba\",\"PhoneNo\":\"0909090908\",\"Email\":\"qudus@email.com\",\"HomeAddress\":\"Lagos\"}]",

  "bankDetailsJson": "[{\"BankName\":\"Kuda\",\"BankAccountNumber\":\"2014780039\",\"AccountType\":\"1\",\"BeneficiaryName\":\"Aliu\",\"BeneficiaryBank\":\"GTBank\",\"BeneficiaryBankAddress\":\"Lagos\",\"BeneficiaryAccountNumber\":\"0153306207\",\"BeneficiaryAddress\":\"Lagos\",\"BICRoutingNumber\":\"225635\",\"IBANNoAndBIC\":\"TR2435\",\"SortCode\":\"5474635\",\"IntermediaryBank1\":\"Wema\",\"IntermediaryBankBIC\":\"BC00001\"}]",

  "clientReferencesJson": "[{\"companyName\":\"ARM Pensions\",\"startDate\":\"2018-01-15\",\"endDate\":\"2020-12-20\",\"location\":\"Lagos\",\"contractValue\":15000000,\"clientName\":\"Ada Okoro\",\"clientPosition\":\"Proc. Officer\",\"clientContact\":\"08031234567\"},{\"companyName\":\"ARM Pensions\",\"startDate\":\"2018-01-15\",\"endDate\":\"2020-12-20\",\"location\":\"Lagos\",\"contractValue\":15000000,\"clientName\":\"Ada Okoro\",\"clientPosition\":\"Proc. Officer\",\"clientContact\":\"08031234567\"}]", 
  

  "hasPendingLegalActions": false,
  "foundGuiltyMisconduct": false,
  "inReceivership": false,
  "inArrearsTaxes": false,
  "relatedToARM": true,
  "relationshipDetails": "Provided IT services to ARM",
  "declarantName": "Shade Adebayo",
  "signature": "https://short.io/sig.png",

  "identificationDocuments": "https://short.io/idoc.pdf",
  "utilityBill": "https://short.io/ubill.pdf",
  "cacStatusReport": "https://short.io/cac.pdf",
  "companyRegistration": "https://short.io/reg.pdf",
  "taxIdentification": "https://short.io/tin.pdf",
  "complianceDocuments": "https://short.io/comp.pdf",
  "businessRegistration": "https://short.io/breg.pdf",
  "memorandumArticles": "https://short.io/memo.pdf",
  "partnershipAgreement": "https://short.io/part.pdf",
  "taxExemption": "https://short.io/taxex.pdf",
  "trustDeed": "https://short.io/trust.pdf",
  "establishmentDocuments": "https://short.io/estab.pdf",
  "authorizationDocuments": "https://short.io/auth.pdf",

  "providingApiServices": true,
  "requireSystemAccess": true,
  "developingSoftware": true,
  "securityFormCompleted": true,
  "additionalSecurityFormCompleted": false,
  "meetsNDPCriteria": true,
  "ndpcCertificate": "https://short.io/ndpc.pdf"
}
```

### GetVendorInfo
```
{
  "vendorNo": "V0025"
}
```

## Responses

### Success Response

**Status Code:** `200 OK`

```json
{
    "@odata.context": "http://bctest.test.com:7248/BCAPI/ODataV4/$metadata#Edm.String",
    "value": "V0017:"
}
```

### Error Response

**Status Codes:** `400 Bad Request`, `500 Internal Server Error`

```json
{
    "error": {
        "code": "string",
        "message": "string"
    }
}
```
