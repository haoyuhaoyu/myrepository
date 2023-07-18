# DSAT Survey Count
> \# of received survey response with **score 1 or 2**.

## CAPS LOB Logic 
# [**Advertiser**](#tab/tabid-advertiser)
##### Planning Category
> - BingAds BOS
> - BingAds Services
> - BingAds Support

##### Support Tool
> CAP - Support DSAT

##### Business Logic
> |KPI|Business Logic|
|--|--|
|Support DSAT Survey|Support Filter group Is **Parent = Yes** and **Program = "Standard Support" or "Digital Marketing Center"** and **IsClosed = yes** and **Score = 1 or 2**|
|Services DSAT Survey|Support Filter group Is **Program in ("Manual Optimization Program (MOP)", "Onboarding Consultation", "Optimization Consultation", "Preferred Agency Service")** and **IsClosed = yes** and **Score = 1 or 2**|
|Service AES DSAT Survey|Support Filter group Is **Program = "Advertiser Enablement Services"** and **IsClosed = yes** and **Score = 1 or 2**|

# [**Partner** - Frontline](#tab/tabid-partner-frontline)
##### Planning Category
> - MPN Delivery
> - CSP Delivery
> - Marketplace Delivery

##### Support Tool
> [DfM](https://aka.ms/onesupport/)

##### Business Logic
> Service desk, under all cases with **Product Family = 'Partner Center'**, using the SAP mapping provided by the PC engineering to get the reporting program mapping for **"CSP"**, **"MPN"** and **"Marketplace"**; And we need to apply queue name mapping to specify the Frontline delivered result.
> [!NOTE]
> **Marketplace** including the **"Co-sell"** product incident.   

# [**Partner** - TPnD](#tab/tabid-partner-tpnd)
##### Planning Category
> TPnD Delivery

##### Support Tool
> [OCP SR - TP&D](https://ocpsr.crm.dynamics.com/main.aspx?appid=04136262-3f1e-450c-9874-3b49079d1639)

##### Business Logic
> The count of CSAT survey that scored 1 and 2 stars of answered survey question ***"How satified are you with this Microsoft Technical Consultation experience?"*** in [OCP SR Tech Presales Survey](https://cmr.eu.qualtrics.com/jfe/preview/SV_5zDoVy1BmKI0P8F?Q_SurveyVersionID=current&amp;Q_CHL=preview)

# [**Partner** - ASfP](#tab/tabid-partner-asfp)
##### Planning Category
> ASfP Delivery

##### Support Tool
> [OCP SR](https://ocpsr.crm.dynamics.com/) for Cloud Consult

##### Business Logic
> The count of CSAT survey that scored 1 and 2 stars of answered ASfP survey question ***"Overall quality of SAM service you received"*** *(Question 2 of all ASfP survey questionaires)*

# [**Partner** - CED](#tab/tabid-partner-ced)
##### Planning Category
> Cloud Enablement Desk

##### Support Tool
> [OCP SR](https://ocpsr.crm.dynamics.com/)

##### Business Logic
> The count of CSAT survey that scored 1 and 2 stars of answered CED survey question ***"How satisfied are you with the Microsoft Cloud Enablement Desk Program"*** *(Question 2 of all ASfP survey questionaires)*

# [**Presales**](#tab/tabid-presales)
##### Planning Category
> - Commercial PreSales Azure
> - Commercial PreSales Dynamics
> - Commercial PreSales MainIVR_Other
> - Commercial PreSales O365

##### Support Tool
> [Service Desk](https://servicedesk.microsoft.com/)

##### Business Logic
> The count of CSAT surveys that scored 1 and 2 stars (Dissatisfaction surveys (DSAT)) score based on a 5 star rating given by **all Presales customers (both Sales Prospects and Non-Sales Prospects)**.  Split by **Prospects = Sales Prospects/Non-Sales Prospects**

# [**Save Desk**](#tab/tabid-savedesk)
##### Planning Category
> - Retention Azure Proactive
> - Retention O365 Proactive
> - Retention O365 Reactive
> - Consumer Engagement and Save

##### Support Tool
>[Service Desk](https://servicedesk.microsoft.com/)

##### Business Logic
> - **Score = 1 or 2**
> - **Commercial Survey**: FactSurveyCommercialRetention
> - **Consumer Survey**: ExecPLName=cs3, ServiceRequestToolUsed=srtool and IssueCode1='manage my subscriptions' and IssueCode2 is in ('i want to cancel my subscription','office 365 to microsoft 365 rebrand') or ServiceRequestToolUsed=mst

# [**Store**](#tab/tabid-store)
##### Planning Category
> - BnM
> - Online
> - SMB

##### Support Tool
> CAP

##### Business Logic
> **Support Filter group**: **Life Cycle Name = Sales** and **using Fiscal Hierarchy UTC** and **LOB Roll Up is not Sales - S&R and is not Sales - Supplemental Parts** and **Score = 1 or 2**

> Other filters: 
> - **Vendor**: Alorica, Concentrix, Majorel, Microsoft (WSS), Relia, Teleperformance, Unspecified, and Wicresoft 
> - **Site**: Angeles/Clark (PH), Athens (GR), Chandler (US), Fargo (ND), Lisbon (PT), San Salvador (SV), Sao Paolo (BR), Shanghai (CN), Web Sales Support, and Yokohama (JP) 

> [!NOTE]
> The Bot messaging surveys are excluded

***

## Data Logic
# [**Advertiser**](#tab/tabid-advertiser)
    ([CSAT 1 Star Count]+
        [CSAT 2 Star Count])

# [**Partner** - Frontline](#tab/tabid-partner-frontline)
    ([CSAT 1 Star Count]+
        [CSAT 2 Star Count])

# [**Partner** - TPnD](#tab/tabid-partner-tpnd)
    ([CSAT 1 Star Count]+
        [CSAT 2 Star Count])

# [**Partner** - ASfP](#tab/tabid-partner-asfp)
    ([CSAT 1 Star Count]+
        [CSAT 2 Star Count])

# [**Partner** - CED](#tab/tabid-partner-ced)
    ([CSAT 1 Star Count]+
        [CSAT 2 Star Count])

# [**Presales**](#tab/tabid-presales)
    ([CSAT 1 Star Count]+
        [CSAT 2 Star Count])

# [**Save Desk**](#tab/tabid-savedesk)
    ([CSAT 1 Star Count]+
        [CSAT 2 Star Count])

# [**Store**](#tab/tabid-store)
    ([CSAT 1 Star Count]+
        [CSAT 2 Star Count])

***