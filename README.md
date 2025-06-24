# Vendor Management System - Structure

## Overview
This document outlines the data structures and workflow for the Vendor Management System. The system handles vendor registration through a multi-step process with approval workflows.

## Core Data Types

VendorRegType

```typescript 
type VendorRegType =
  | "International Vendor"
  | "Local Vendor (Limited)"
  | "Local Vendor (Non-Limited)"
  | "Trust"
  | "Non-Profit Organization"
  | "Unskilled Vendor"
  | "Government";
```
VendorClassificationType

``` typescript
type VendorClassificationType =
  | "International Vendor"
  | "Sole Proprietorship"
  | "Partnership"
  | "Limited Liability Company"
  | "Corporation"
  | "Government Agency"
  | "Trust"
  | "Non-Profit Organization"
  | "Unskilled Vendor";
```

### VendorFormData Structure
The main form data is organized into 6 steps:

| Step | Section | Description |
|------|---------|-------------|
| 1 | Company Information | Basic company details, directors, guarantors |
| 2 | Banking Information | Account details and beneficiary information |
| 3 | Document Upload | Required compliance and registration documents |
| 4 | Client References | Previous work history and references |
| 5 | Declarations | Legal and compliance declarations |
| 6 | Security & Compliance | API services and security requirements |

### Step 1: Company Information

| Field | Type | Description |
|-------|------|-------------|
| companyName | string | Company name |
| vendorRegType | VendorRegType | Registration type |
| vendorClassification | VendorClassificationType | Vendor classification |
| address | string | Primary address |
| address2 | string | Secondary address |
| city | string | City |
| country | string | Country |
| state | string | State/Province |
| phoneNo | string | Phone number |
| mobilePhoneNo | string | Mobile phone |
| email | string | Email address |
| rcNumber | string | Registration number |
| tin | string | Tax identification number |
| vatRegistrationNo | string | VAT registration |
| payerId | string | Payer ID |
| numberOfEmployees | number | Employee count |
| incorporationDate | string | Date of incorporation |
| armContactDepartment | string | ARM contact department |
| hasNigerianCompany | boolean | Has Nigerian company |
| directors | Director[] | Company directors |
| guarantors | Guarantor[] | Company guarantors |
| idCard | FileData[] | ID card uploads |
| locationEvidence | FileData[] | Location evidence |

### Step 2: Banking Information

**Note**: Banking information is stored as an array of bank account objects to support multiple accounts.

| Field | Type | Description |
|-------|------|-------------|
| bankAccounts | BankAccount[] | Array of bank account information |

#### BankAccount Object Structure

| Field | Type | Description |
|-------|------|-------------|
| bankName | string | Bank name |
| bankAccountNumber | string | Account number |
| accountType | "Savings" \| "Current"| Account type |
| beneficiaryName | string | Beneficiary name |
| beneficiaryBank | string | Beneficiary bank |
| beneficiaryBankAddress | string | Bank address |
| beneficiaryAccountNumber | string | Beneficiary account |
| beneficiaryAddress | string | Beneficiary address |
| bicRoutingNumber | string | BIC/Routing number |
| ibanNoAndBic | string | IBAN and BIC |
| sortCode | string | Sort code |
| intermediaryBank1 | string | Intermediary bank |
| intermediaryBankBic | string | Intermediary BIC |
| OnboardingSource | string | Onboarding source |

### Step 3: Document Uploads
For Uploads, multiple is allowed. (This already has a SharePoint API, so I will return an array of URLs)

| Field | Type | Description |
|-------|------|-------------|
| identificationDocuments | FileData[] | ID documents |
| utilityBill | FileData[] | Utility bills |
| cacStatusReport | FileData[] | CAC status report |
| companyRegistration | FileData[] | Company registration |
| taxIdentification | FileData[] | Tax identification |
| complianceDocuments | FileData[] | Compliance documents |
| businessRegistration | FileData[] | Business registration |
| memorandumArticles | FileData[] | Memorandum & articles |
| partnershipAgreement | FileData[] | Partnership agreement |
| taxExemption | FileData[] | Tax exemption |
| trustDeed | FileData[] | Trust deed |
| establishmentDocuments | FileData[] | Establishment documents |
| authorizationDocuments | FileData[] | Authorization documents |

### Step 4: Client References

| Field | Type | Description |
|-------|------|-------------|
| clientReferences | ClientReference[] | Client reference list |
| objection | boolean | Has objection |
| objectionReason | string | Objection reason |
| referenceDocuments | FileData[] | Reference documents |

### Step 5: Declarations

| Field | Type | Description |
|-------|------|-------------|
| hasPendingLegalActions | boolean | Pending legal actions |
| foundGuiltyMisconduct | boolean | Found guilty of misconduct |
| inReceivership | boolean | In receivership |
| inArrearsTaxes | boolean | In arrears with taxes |
| relatedToARM | boolean | Related to ARM |
| relationshipDetails | string | Relationship details |
| declarantName | string | Declarant name |
| signature | FileData[] | Signature upload |

### Step 6: Security & Compliance

| Field | Type | Description |
|-------|------|-------------|
| providingApiServices | boolean | Providing API services |
| requireSystemAccess | boolean | Requires system access |
| developingSoftware | boolean | Developing software |
| securityFormCompleted | boolean | Security form completed |
| additionalSecurityFormCompleted | boolean | Additional security form |
| meetsNDPCriteria | boolean | Meets NDP criteria |
| ndpcCertificate | FileData[] | NDPC certificate |

## Supporting Data Types

### BankAccount
| Field | Type | Description |
|-------|------|-------------|
| bankName | string | Bank name |
| bankAccountNumber | string | Account number |
| accountType | "Savings" \| "Current" \| "Checking" | Account type |
| beneficiaryName | string | Beneficiary name |
| beneficiaryBank | string | Beneficiary bank |
| beneficiaryBankAddress | string | Bank address |
| beneficiaryAccountNumber | string | Beneficiary account |
| beneficiaryAddress | string | Beneficiary address |
| bicRoutingNumber | string | BIC/Routing number |
| ibanNoAndBic | string | IBAN and BIC |
| sortCode | string | Sort code |
| intermediaryBank1 | string | Intermediary bank |
| intermediaryBankBic | string | Intermediary BIC |
| OnboardingSource | string | Onboarding source |

### Director
| Field | Type | Description |
|-------|------|-------------|
| role | "Director" \| "Shareholder" | Role type |
| name | string | Full name |
| position | string | Position |
| phone | string | Phone number |
| email | string | Email address |
| dob | string | Date of birth |
| percentageOfShareholdings | number | Shareholding percentage |
| numberOfShareholdings | number | Number of shares |

### ClientReference
| Field | Type | Description |
|-------|------|-------------|
| companyName | string | Client company name |
| startDate | string | Project start date |
| endDate | string | Project end date |
| location | string | Project location |
| contractValue | number | Contract value |
| clientName | string | Client contact name |
| clientPosition | string | Client position |
| clientContact | string | Client contact info |

### Guarantor
| Field | Type | Description |
|-------|------|-------------|
| name | string | Full name |
| address | string | Address |
| phone | string | Phone number |
| email | string | Email address |
| homeAddress | string | Home address |

## Workflow Management

### Submission Entity
| Field | Type | Description |
|-------|------|-------------|
| id | string | Unique submission ID |
| email | string | Submitter email |
| formData | VendorFormData | Complete form data |
| status | Status | Current status |
| currentReviewer | Reviewer \| null | Current reviewer |
| reviewHistory | ReviewAction[] | Review history |
| comments | Comment[] | Review comments |
| rejectionReasons | RejectionReason[] | Rejection reasons |
| submittedAt | string | Submission timestamp |
| lastUpdated | string | Last update timestamp |
| requiresInfoSec | boolean | Requires InfoSec review |
| isFinalized | boolean | Finalization status |
| bcSyncStatus | BCStatusSync | BC sync status |
| bcSyncError | BCError \| string | BC sync error |
| bcSyncAttempts | number | BC sync attempts |
| lastBcSyncAttempt | string | Last sync attempt |

### Enums and Status Types

#### Status Flow
```
Submitted → ProcurementReview → InfoSecReview → ComplianceReview → Approved → Onboarded
     ↓              ↓                ↓               ↓            ↓
  Rejected ←────────┴────────────────┴───────────────┴────────────┘
```

#### Status Types
- **Submitted**: Initial submission
- **ProcurementReview**: Under procurement review
- **InfoSecReview**: Under information security review
- **ComplianceReview**: Under compliance review
- **Approved**: Approved for onboarding
- **Rejected**: Rejected at any stage
- **Onboarded**: Successfully onboarded

#### Reviewer Types
- **Procurement**: Procurement officer
- **InfoSec**: Information Security officer
- **Compliance**: Compliance officer

#### Admin Actions
- **approve**: Approve submission
- **reject**: Reject submission
- **comment**: Add comment

#### BC Sync Status
- **pending**: Sync pending
- **success**: Sync successful
- **failed**: Sync failed
- **onboarded**: Successfully onboarded
- **onboard_failed**: Onboarding failed

## Validation Rules

## Dynamic Field Validation Rules

Since field requirements vary based on vendor type and classification, here are the detailed validation rules:

### Step 1 - Basic Required Fields (All Vendor Types)
- `companyName`, `vendorRegType`, `vendorClassification`, `address`, `country`, `state`, `phoneNo`, `email`

### Step 1 - Vendor Type Specific Requirements

#### International Vendor
- `vendorClassification` must be "International Vendor"
- `tin` required only if `hasNigerianCompany` is true

#### Local Vendor (Limited)
- `vendorClassification` must be "Limited Liability Company" or "Corporation"
- `tin` and `vatRegistrationNo` required

#### Local Vendor (Non-Limited)
- `vendorClassification` must be "Sole Proprietorship" or "Partnership"
- **Partnership**: `tin` and `vatRegistrationNo` required
- **Sole Proprietorship**: `payerId` required

#### Trust
- `vendorClassification` must be "Trust"
- `tin` required

#### Unskilled Vendor
- `vendorClassification` must be "Unskilled Vendor"
- No additional requirements

#### Non-Profit Organization / Government
- `vendorClassification` must match vendor type
- No additional tax requirements

### Step 3 - Required Documents by Vendor Type

| Vendor Type | Required Documents |
|-------------|-------------------|
| **All Types** | `identificationDocuments`, `utilityBill` |
| **International Vendor** | + `companyRegistration`, `taxIdentification`, `complianceDocuments` |
| **Local (Limited)** | + `companyRegistration`, `memorandumArticles`, `taxIdentification`, `cacStatusReport` |
| **Local (Non-Limited) - Sole** | + `businessRegistration`, `taxIdentification` |
| **Local (Non-Limited) - Partnership** | + `partnershipAgreement`, `businessRegistration`, `taxIdentification` |
| **Non-Profit** | + `companyRegistration`, `taxExemption`, `cacStatusReport` |
| **Trust** | + `trustDeed`, `businessRegistration`, `cacStatusReport` |
| **Government** | + `establishmentDocuments`, `authorizationDocuments` |
| **Unskilled Vendor** | Base documents only |

### Step 4 - Client References Requirements

| Vendor Type | Minimum References | Notes |
|-------------|-------------------|-------|
| **Non-Profit, Government, Trust** | 0 | References not mandatory |
| **Unskilled Vendor** | 2 | Minimum 2 references |
| **All Others** | 3 | Minimum 3 references |

**Additional Step 4 Rules:**
- All reference fields are required when providing references
- `referenceDocuments` required (except for Non-Profit, Government, Trust)
- If `objection` is true, `objectionReason` is required

### Step 5 - Declaration Requirements
- `declarantName` always required
- If `relatedToARM` is true, `relationshipDetails` is required

### Step 6 - Security Requirements
- If `meetsNDPCriteria` is true, `ndpcCertificate` is required

## Validation Rules Summary
The frontend already handled the complex conditional validation based on vendor type combinations. The backend should implement similar validation logic.
