# CSAT
> 5 Star average rating of answered survey.

## CAPS LOB Logic 
# [**Advertiser**](#tab/tabid-advertiser)
##### Planning Category
> - BingAds BOS
> - BingAds Services
> - BingAds Support

##### Support Tool
> CAP - Support CSAT

##### Business Logic
> |KPI|Business Logic|
|--|--|
|Support CSAT|Support Filter group Is **Parent = Yes** and **Program = "Standard Support" or "Digital Marketing Center" or "Unified Product Support"** and **IsClosed = yes**|
|Services CSAT|Support Filter group Is **Program in ("Extended Engagement", "Onboarding Consultation", "Optimization Consultation", "Preferred Agency Service")** and **IsClosed = yes**|
|Service AES CSAT|Support Filter group Is **Program = "Advertiser Enablement Services"** and **IsClosed = yes**|

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
> 5 Star average rating of answered survey question ***"How satified are you with this Microsoft Technical Consultation experience?"*** in [OCP SR Tech Presales Survey](https://cmr.eu.qualtrics.com/jfe/preview/SV_5zDoVy1BmKI0P8F?Q_SurveyVersionID=current&amp;Q_CHL=preview)

# [**Partner** - ASfP](#tab/tabid-partner-asfp)
##### Planning Category
> ASfP Delivery

##### Support Tool
> [OCP SR](https://ocpsr.crm.dynamics.com/) for Cloud Consult

##### Business Logic
> 5 Star average rating of answered ASfP survey question ***"Overall quality of SAM service you received"*** *(Question 2 of all ASfP survey questionaires)*

# [**Partner** - CED](#tab/tabid-partner-ced)
##### Planning Category
> Cloud Enablement Desk

##### Support Tool
> [OCP SR](https://ocpsr.crm.dynamics.com/)

##### Business Logic
> 5 Star average rating of answered CED survey question ***"How satisfied are you with the Microsoft Cloud Enablement Desk Program"*** *(Question 2 of all CED survey questionaires)*

# [**Presales**](#tab/tabid-presales)
##### Planning Category
> - Commercial PreSales Azure
> - Commercial PreSales Dynamics
> - Commercial PreSales MainIVR_Other
> - Commercial PreSales O365
> - SMB_Presales

##### Support Tool
> [Service Desk](https://servicedesk.microsoft.com/)

##### Business Logic
> The average Customer Satisfaction (CSAT) score based on a 5 star rating given by **all Presales customers (both Sales Prospects and Non-Sales Prospects)**.  Split by **Prospects = Sales Prospects/Non-Sales Prospects**

> |VSB Store|Business Logic|
|--|--|
|**PlanningCategory = "SMB_Presales"**| including MSX survey(Datasourcegroup = "MSX")
|Total CSAT|Total 5 Star Score / Total Survey|
|Phone CSAT|Total CSAT with SupportChannelName contains "Phone"|
|Human CSAT|Total CSAT with SupportChannelName = "Chat"|
|MSX CSAT|Total CSAT with Datasourcegroup = "MSX"|

# [**Save Desk**](#tab/tabid-savedesk)
##### Planning Category
> - Retention Azure Proactive
> - Retention O365 Proactive
> - Retention O365 Reactive
> - Consumer Engagement and Save

##### Support Tool
>[Service Desk](https://servicedesk.microsoft.com/)

##### Business Logic
> - **Commercial Survey**: FactSurveyCommercialRetention
> - **Consumer Survey**: ExecPLName=cs3, ServiceRequestToolUsed=srtool and IssueCode1='manage my subscriptions' and IssueCode2 is in ('i want to cancel my subscription','office 365 to microsoft 365 rebrand') or ServiceRequestToolUsed=mst
> - **Commercial CSAT**:CSAT of Commercial Survey
> - **Consumer (D) CSAT**: CSAT of Consumer Survey when Save Team is Dedicated

# [**Store**](#tab/tabid-store)
##### Planning Category
> - BnM
> - Online

##### Support Tool
> CAP

##### Business Logic
> **Support Filter group**: **Life Cycle Name = Sales** and **using Fiscal Hierarchy UTC** and **LOB Roll Up is not Sales - S&R and is not Sales - Supplemental Parts**

> Other filters: 
> - **Vendor**: Alorica, Concentrix, Majorel, Microsoft (WSS), Relia, Teleperformance, Unspecified, and Wicresoft 
> - **Site**: Angeles/Clark (PH), Athens (GR), Chandler (US), Fargo (ND), Lisbon (PT), San Salvador (SV), Sao Paolo (BR), Shanghai (CN), Web Sales Support, and Yokohama (JP) 

> |Consumer|Business Logic|
|--|--|
|**PlanningCategory in ("Online","BnM","Unspecified")**| Bot survey only display for Bot related KPIs, not included in other KPIs 
|Total CSAT|Total 5 Star Score / Total Survey|
|Phone CSAT|Total CSAT with SupportChannelName contains "Phone"|
|Human CSAT|Total CSAT with SupportChannelName = "Chat"|
|Bot CSAT|**Life Cycle Name = Sales and Exec PL Name = CS3** and **ServiceLineName IN ('Sales - B&M','Sales - Core IVR Pre Sales','Sales - CS Pre-Sales','Sales - MS Store Online','Sales - Post Sales - Non-Specific','Unspecified')** and **Support Queue FullName LIKE '%BOT%'** |


> [!NOTE]
> The Bot messaging surveys are excluded

***

## Data Logic
# [**Advertiser**](#tab/tabid-advertiser)
    IF(ISBLANK([CSAT Survey Responses]),
        BLANK(),
        DIVIDE(([CSAT 1 Star Count]*1)+
        ([CSAT 2 Star Count]*2)+
        ([CSAT 3 Star Count]*3)+
        ([CSAT 4 Star Count]*4)+
        ([CSAT 5 Star Count]*5),
        [CSAT Survey Responses]))

# [**Partner** - Frontline](#tab/tabid-partner-frontline)
    IF(ISBLANK([CSAT Survey Responses]),
        BLANK(),
        DIVIDE(([CSAT 1 Star Count]*1)+
        ([CSAT 2 Star Count]*2)+
        ([CSAT 3 Star Count]*3)+
        ([CSAT 4 Star Count]*4)+
        ([CSAT 5 Star Count]*5),
        [CSAT Survey Responses]))

# [**Partner** - TPnD](#tab/tabid-partner-tpnd)
    IF(ISBLANK([CSAT Survey Responses]),
        BLANK(),
        DIVIDE(([CSAT 1 Star Count]*1)+
        ([CSAT 2 Star Count]*2)+
        ([CSAT 3 Star Count]*3)+
        ([CSAT 4 Star Count]*4)+
        ([CSAT 5 Star Count]*5),
        [CSAT Survey Responses]))

# [**Partner** - ASfP](#tab/tabid-partner-asfp)
    IF(ISBLANK([CSAT Survey Responses]),
        BLANK(),
        DIVIDE(([CSAT 1 Star Count]*1)+
        ([CSAT 2 Star Count]*2)+
        ([CSAT 3 Star Count]*3)+
        ([CSAT 4 Star Count]*4)+
        ([CSAT 5 Star Count]*5),
        [CSAT Survey Responses]))

# [**Partner** - CED](#tab/tabid-partner-ced)
    IF(ISBLANK([CSAT Survey Responses]),
        BLANK(),
        DIVIDE(([CSAT 1 Star Count]*1)+
        ([CSAT 2 Star Count]*2)+
        ([CSAT 3 Star Count]*3)+
        ([CSAT 4 Star Count]*4)+
        ([CSAT 5 Star Count]*5),
        [CSAT Survey Responses]))

# [**Presales**](#tab/tabid-presales)
    IF(ISBLANK([CSAT Survey Responses]),
        BLANK(),
        DIVIDE(([CSAT 1 Star Count]*1)+
        ([CSAT 2 Star Count]*2)+
        ([CSAT 3 Star Count]*3)+
        ([CSAT 4 Star Count]*4)+
        ([CSAT 5 Star Count]*5),
        [CSAT Survey Responses]))

# [**Save Desk**](#tab/tabid-savedesk)
    IF(ISBLANK([CSAT Survey Responses]),
        BLANK(),
        DIVIDE(([CSAT 1 Star Count]*1)+
        ([CSAT 2 Star Count]*2)+
        ([CSAT 3 Star Count]*3)+
        ([CSAT 4 Star Count]*4)+
        ([CSAT 5 Star Count]*5),
        [CSAT Survey Responses]))

# [**Store**](#tab/tabid-store)
    IF(ISBLANK([CSAT Survey Responses]),
        BLANK(),
        DIVIDE(([CSAT 1 Star Count]*1)+
        ([CSAT 2 Star Count]*2)+
        ([CSAT 3 Star Count]*3)+
        ([CSAT 4 Star Count]*4)+
        ([CSAT 5 Star Count]*5),
        [CSAT Survey Responses]))

***