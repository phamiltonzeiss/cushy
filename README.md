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
Taken all of the above into account, my initial vision is a web-based portal which focuses on an intuitive User Experience/Interface (UEI) overlying an expanding featureset of self-help tools. The name, CuSHY, is (I hope obviously) subject to revision, but the intention is to give the project the vibe of something safe and reassuring that can serve as a safety net or a go-to resource, depending on the customer profile. It's also funny to me to reference the world tree in context of a project that has a large number of (potential) branching elements, but YMMV.

Anything that could be considered Technical Support but which requires minimal support personnel to manage could fall under this banner: improved self-service licensing? Could be added to CuSHY. Improved email request interface? Could be added to CuSHY. Tech Support feedback system? Could be added to CuSHY. Updated FORUM support request forms/process? Could be added to CuSHY, etc, etc.

## Technical and Practical Considerations
To my mind, the most significant questions at the early stages are:

 - What resources do we need to do this (and do it right)?
 - What existing assets can we leverage to reduce workload/development time?
 - What should the tech stack look like?
 - Are there any processes or practices currently in wide use that would need to be altered to make this project successful?

I'll address these more or less in order, although the first two questions have a lot of interplay so I'm lumping them together.

### Resources: What We Already Have and What We're Going to Need

#### Current Assets
Most of the items listed above under Potential Components more or less mirror something (or several somethings) we already have as an internal resource.

 - Knowledge Base: OneNote, MIRA, SIS, SNAP, SharePoint, Teams WF Chat History, Wiki (rumored)
 - Chat Support: Genesys (maybe?)
 - Request Portal and/or Asset Reference: SAP CRM (maybe?), Salesforce (maybe? eventually?)
 - Communication Hub: Zess.com (in theory)

I did not include the Parts Self-service above because I don't currently have any insight what the Parts department uses for inventory/order processing, or whether whatever they are using could potentially be made fully or partially customer-facing. I'll assume for the time being that component would require ground-up development.

There are a lot of implicit questions in the list above, however. Despite having quite a few repositories of reference material, precious little of it is intended for a customer audience. Brief searches online suggest Genesys does offer a chat-based featureset but it wasn't clear to me with a quick scan whether this is an upgrade/add-on feature or how it's supposed to integrate into TSE workflows. CRM might have the option to have a selection of features available to the public, but we also don't seem to have much if any control over the CRM system. Additionally, my understanding (unless something changed since last I heard) is SAP CRM may be in the process of being replaced by something else (Salesforce, last I heard), which itself may or may not allow customer interaction by default or implementation. In either case, if the suite itself is not able to host a limited set of public features, development effort would need to be made to provide a customer-facing wrapper for some of those functions.

It also shouldn't be understated that we have a metric ton of individual, experiential knowledge across the team. 

#### Required Assets
So, what _don't_ we have already that would need to be developed or acquired? Below is an incomplete list, which I have resisted editorializing for the sake of brevity and clarity. Bear in mind, though, that each of these items represents a likely Herculean undertaking either due to internal red tape, developer investment, business center cost (outlay or ongoing, depending on determined strategy), or simply time.

 - Deployment environment: public-facing web servers, with domain names, admin access, deployment tooling, and necessary redundancy/disaster recovery resources
 - Testing/QA environment: internal-facing mirror of the deployment environment with full admin control, testing frameworks, and pipeline support
 - Data repository: dev and prod database servers, at minimum, ideally also qa instance
 - Front-end code: the UEI connecting the various components
 - Backend code: database integration, API processing, off-the-shelf applications, administrative functions
 - Processes: data vetting, format conversion, approval, auditing, validation, ownership

### Tech Stack
Taking the required assets (above) into account, the environment assets are probably the biggest hurdle. Unlike SNAP, however, there is no workaround I can envision to deliver code/assets to the target audience without these being secured. That said, there are two primary approaches, which may be more or less viable depending on how the existing Zeiss.com site architecture functions and what the overall budget for the project ends up being.

#### Traditional Path
Essentially, this is the hardware investment route. Rack servers, network apparatus, security hardening, co-location. Significant upfront investment is required, most likely will require buy-in/sign-off from the existing data center, NOC, and potentially marketing/site ownership teams. Once everything is set up and running, however, overhead should be relatively minimal outside of development and maintenance efforts, presuming there is some existing infrastructure we can leverage.

#### Cloud Path
This would be the SaaS/PaaS approach, leveraging something like Azure, AWS, or GCP to deploy into cloud platforms. Note that while upfront investment (in dollar terms) may be lower than the Traditional Path outlined above, there is a tradeoff because to my knowledge there is no existing framework for these kinds of services, at least not within the TSE group(s). So some additional time/development effort may be required unless there are other teams at Zeiss already doing versions of this that we could partner with.

Beyond that, there are requisite ongoing costs associated with this paradigm. A very quick AWS Pricing Calculator trawl using wild guesstimate traffic numbers suggests a minimum of $9,600 annually and in my past experience, cloud cost estimates are always woefully undervalued. I think it would be fair to double the provided estimate and assume that running CuSHY on a cloud service could cost something like $20K per year or more, depending on how popular/well-used the service ends up being. I should note that those costs would be lower during the development period, but hardly zero.

#### Other Tech
Regardless of environment choice, we'd also most likely want Nginx or Apache web servers; MySQL or similar database; Python, Ruby, or Go for backend dev; JavaScript/CSS for front end; Jenkins for pipelines; Nagios for monitoring. This stuff is all open source and unlikely to represent any significant cost, up front or ongoing, other than the labor required to set it all up.

Beyond that, further investigation is required. I'm not sure what Zeiss's procurement policies are like, but possible features like live agent chat, document conversion, ticketing automation, payment processing, etc could all potentially be acquired rather than rolling our own. SmartSupp, LiveChat, ZenDesk, Obsidian, SAP Gateway, Paysafe, Stax, Servicenow, Servicate, etc could be analyzed for potential integration as opposed to developing every feature/component in-house.

## Miscellaneous Considerations
To me, the main questions before diving in with any engineering would be:

 - Will we have buy-in/support from Germany to implement this in a way that is actually useful?
 - Will we have local resources available to drive the project all the way to completion and then keep it maintained?

My view is that this isn't the kind of thing that can be completely slow-rolled because partial implementation/deployment--at least of individual components--doesn't carry enough value and/or risks undermining the purpose. If we develop a UEI and dump a few docs into a database and push it onto a Raspberry Pi and start telling our customers about it, it would potentially take only a single instance of any given customer checking the site and not finding what they're looking for before they abandon it and revert their default back to the support phone.

Likewise, unless the processes around something like this are well-thought-out and clearly established, it's likely doomed to be a dead end. Publishing documentation that seems safe for customers only to find out someone doesn't think it should be customer-facing or disagrees on some specific verbiage will undermine the efforts to populate the site with useful, relevant information. Building an API to communicate with SAP only to hit a brick wall getting it integrated with the CRM maintainers would be immensely frustrating.

It's also worth mentioning somewhere that there may be a broader application for (at least) the documentation component here as well. Above, when mentioning the knowlege base, I listed half a dozen systems/repositories where some of the documented knowledge is kept. But that's hardly an exhaustive list: there's also people's personal notes, tons of files stored on the N: drive, training material, and probably a bunch I'm forgetting or don't know about. I feel there's a strong case to be made for consolidating as many of those tools as possible and using a subset of all the available reference documentation for customer self-service. I'd even argue CZMI Tech Support would greatly benefit from a documenation wrangler as a dedicated, full-time role. In any case, any effort to formalize and clarify documentation for customers could also have significant benefits for internal documentation as well.

## Conclusion
A tool like CuSHY has the potential to improve customer satisfaction by a significant margin. Reducing the number of incoming calls (especially those that are relatively easy to resolve or which are not Tech Support-specific) will reduce queue/hold times, providing alternate support interaction methods benefits customers with hearing difficulties or who need less synchronous communication, and taking control of customer-facing, support-specific functionality gives us the power to shape our workflows to best meet our customers' needs. There are significant challenges inherent in a project like this, but I think with sufficient preparation and foresight, they can be mitigated enough to make the end result a success.