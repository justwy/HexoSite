---
title: design_doc_template
date: 2017-11-07 13:29:27
tags:
---

# Introduction

## Summary
- Provide a single line summary of project
- Who is the intended audience of this document?

## Motivation
- Provide the business background
- What is the expected business/customer impact? This might be increased revenue, selection expansion, ..

## Requirements
- Clearly state the business requirements
- Clearly state the legal requirements, if any (data retention, data access, logging, SOX)
- Add a prediction for the growth rate for the system.
- Clearly state the technical requirements:
  - What are the requirements for scalability?
  - What are the requirements for performance?
  - What are the requirements for availability?
  - What is the data classification and related InfoSec policy requirements
    - Determine the data classification and outline the data handling requirements given the classification (eg: encryption, access controls, etc). The following document links to the documents relevant for determination of the data classification and data handling requirements: https://policy.amazon.com/policy/95
  - What are the requirements for internationalization?
    - Use UTF-8 by default.
    - Consider timezone differences.
    - Consider currency differences.
    - Locale differences. For example not all locales use green to mean good and red to mean bad.
    - Internationalization training in KNET: https://knet.csod.com/LMS/LoDetails/DetailsLo.aspx?loid=0cc563fb-b202-43a2-af80-50e43d9a1617#t=1

## Definitions
- Any key concepts that need to be understood as prerequisites for reading the doc
- If you have a glossary then consider adding it as an appendix.

## Scope
- what is in and out of scope?
- what will always be out of scope?
- what are the likely follow up projects?

## Existing systems
- Is there an existing system or process that is to be replaced? If yes provide details.

# Design
Multiple competing designs can be presented. Present your recommendation after the design proposals and your reasoning for that choice.

Consider presenting the following content for each of the designs:

## High-level Architecture
- Provide an architecture written description and diagram
  - From this, a reader should understand the most important runtime components of your system and how they relate.  
    - How do you coordinate your computation?   Services responding to requests?   Daemon processes listening to SQS queues or SWF?   DJS workflows?
    - Do you persist data, and if so, where?   Authoritative datastore?   Do you export from to enable other kinds of data access, such as for reporting or search?
    - What are the most important external systems you are integrating with?
  - Architecture diagrams often capture information that is similar to Deployment diagrams, but typically in a more free-form / easily visually interpreted way.
  - For AWS components, in your architecture diagram, consider re-using the standard AWS icons
- As necessary to communicate the plan, consider adding additional diagrams:
  - class diagrams or entity-relationship diagrams to show how business information has been captured in a domain model or data structure
  - data flow diagrams or workflow-diagrams to show how different data enters your system, is transformed, joined, and passed downstream
  - sequence diagrams to show interactions over time, especially when particular timing of events is essential to the design or scenario being considered

## Data Modelling and Data Flow
- Provide an E/R diagram if appropriate
- Provide a data flow diagram if appropriate
- Provide schema of data produced by the system. Data consumed by the system should comprise the requirements section.

## User Interface
- provide mockups of key UI interfaces

## Availability
- How does this design achieve the above-mentioned goals for availability?
- What is the availability of the systems dependencies and how does that translate into this systems level of availability?

## Performance
- How does this design achieve the above-mentioned goals for performance?
- What are the likely performance bottlenecks and how might they be overcome? For instance you might describe system dependencies that affect performance or compute-heavy algorithms.

## Scalability
- How does this design achieve the abovementioned goals for scalability?
- When you need to scale your service up how will this be achieved.
- What are the likely scaling bottlenecks and how might they be overcome? For instance there might be services or data stores on which you depend that limit scalability, ...

## Internationalization
- How does this design achieve the abovementioned goals for internationalization?

## Security
- Attach a TT link if you have gone through the security consultation process.
- Describe how the design is impacted by any data handling requirements.
  - Are all of the systems on which this system depends able to handle data of that particular classification?
- Link to all of the relevant security policies.
- Describe the mechanism/s used for authentication. Eg: Kerberos, AAA, AWS Auth.
- Describe the mechanism/s for authorization. Eg: IAM policies.
- TODO (Anthony): Link to the tool that lets user do a self certification.
- Once you have created an Anvil application, please attach a link to it.

## Costing
- Estimate the current and predicted future cost of the system based on the expected throughput and rate of growth.

## Operational
- What monitors should be in place to identify error conditions?
- What alarms should be in place to aggregate monitors and notify on call of problems?
- What logging is required?

## Risks and Project Dependencies
- On what other projects does this project depend?

## System Dependencies
- On what other systems and/or technologies does this system depend?
- How do the limitations of those systems or technolgoies affect this design?
  - For instance is the reliability reduced or increased as a result of taking on the system or technology dependency?
  - How doess the dependency affect availability?
  - How does the dependency affect throughput? (eg: KMS or other AWS service access rate limits, S3 hot keys, ..)

## Estimate
- Present a rough estimate of the level-of-effort required, if available.

## Service APIs
- Provide details of the API's, if any.

# Deployment and Testing

## Deployment
- What is the rollout plan?
- What is the roll back plan?

## Testing
- What system tests should be in place?
- What stress testing will need to be done?
- What performance testing will need to be automated?

## Migration Plan
- Are data migrations required?
- Are new schema versions required?
- How will this be managed?

## Milestones / Schedule

## Open Questions
- What are the open questions that need to be resolved?
