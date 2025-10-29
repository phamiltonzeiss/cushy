# Customer Self-Help Yggdrasil (CuSHY)

## Front Matter
This document represents only the author's opinion and project vision. It is meant to be combined with ideas and perspectives from other project participants, stakeholders, and contributors. Where analysis or conclusions differ, discussion should begin.

## Summary of Project
In my year-plus at Zeiss, the notion of a tool or repository where customers can go to inform themselves or find first-line support has been floated surprisingly often considering how long the support organization has operated without such a service. I'm not sure whether this suggests the idea is crucial and/or self-evident, prohibitively difficult to implement for various reasons, less impactful than it seems at first blush, or some/all of the above, but the fact that serious discussion is now underway for what something like this would look like and what it might take to put together is an encouraging development.

The only description of the concept I have received at this point is, "a customer-facing portal," which can obviously mean a lot of things. To determine what a customer-facing portal might entail, I feel it best to start by clarifying the intended purpose of the project.

### Purpose
The main driver, as I have gathered from related discussions, is reducing the number of incoming calls. Since estimates for required number of TSEs to successfully manage the current call volume is well beyond what we could reasonably employ, the best way to improve the customer experience would be to reduce the need for service calls in the first place. To accomplish this, any tool meant to offer customers a self-service alternative would need to address the needs of specific subsets of the customer base:

 - Customers who are Biomed, IT, or otherwise technically savvy who prefer to try resolving technical issues on their own as an initial remediation effort
 - Customers who already know the source of their current issue and only need assistance finding the appropriate remediation
 - Customers using the Tech Support line as an entry point to initiate dialogs with other Zeiss teams/individuals
 - Customers who prefer not to or cannot use phone-based interactive support

A secondary motivation or benefit to a customer-facing self-help tool would be to reduce time to resolution (TTR) for active calls which fall under the banner of "eligible for self-service." TSE agents answering phones may find they are able to "offload" some simple or repetitive calls by directing customers to an online tool, freeing their time to focus on cases where subject matter expertise or focused troubleshooting is required.

### Potential Components
To address the unique needs of each of the customer subsets outlined above, I'd recommend the following project features. These are listed in descending order of impact or importance, but cost or difficulty of implementation is not factored in (at least not here).

 1. Customer-facing Knowledge Base
 1. Chat-based Tech Support
 1. Self-serve Service Request Portal
 1. Communication Hub (Smart/Interactive Directory)
 1. Customer/Asset Reference Database
 1. Parts Self-service

### CuSHY as a Concept
Taken all of the above into account, my initial vision is a web-based portal which focuses on an intuitive User Experience/Interface (UEI) overlying an expanding featureset of self-help tools. The name is (I hope obviously) subject to revision, but the intention is to give the project the vibe of something safe and reassuring that can serve as a safety net or a go-to resource, depending on the customer profile.

## Technical and Practical Considerations
To my mind, the most significant questions at the early stages are:

 - What resources do we need to do this (and do it right)?
 - What existing assets can we leverage to reduce workload/development time?
 - What should the tech stack look like?
 - Are there any processes or practices currently in wide use that would need to be altered to make this project successful?

I'll address these more or less in order, although the first two questions have a lot of interplay so I'm lumping them together.

### Resources: What We Already Have and What We're Going to Need
Most of the items listed above under Potential Components more or less mirror something (or several somethings) we already have as an internal resource.

 - Knowledge Base: OneNote, MIRA, SIS, SNAP, SharePoint, Teams WF Chat History, Wiki (rumored)
 - Chat Support: Genesys (maybe?)
 - Request Portal and/or Asset Reference: SAP CRM (maybe?), Salesforce (maybe? eventually?)
 - Communication Hub: Zess.com (in theory)

I did not include the Parts Self-service above because I don't currently have any insight what the Parts department uses for inventory/order processing, or whether whatever they are using could potentially be made fully or partially customer-facing. I'll assume for the time being that component would require ground-up development.

There are a lot of implicit questions in the list above, however. Despite having quite a few repositories of reference material, precious little of it is intended for a customer audience. Brief searches online suggest Genesys does offer a chat-based featureset but it wasn't clear to me with a quick scan whether this is an upgrade/add-on feature or how it's supposed to integrate into TSE workflows. CRM might have the option to have a selection of features available to the public, but we also don't seem to have much if any control over the CRM system. Additionally, my understanding (unless something changed since last I heard) is SAP CRM may be in the process of being replaced by something else (Salesforce, last I heard), which itself may or may not allow customer interaction by default or implementation. In either case, if the suite itself is not able to be host a limited set of public features, development effort would need to be made to provide a customer-facing wrapper for some of those functions.