# EMINENT Results Database

This repository contains the results of EMINENT maturity assessments that have been performed on various interoperability communities. This document will address the following subjects:

1) How to perform a maturity assessment and add your results to this database
2) How to perform a maturity tracking assessment
3) How the contents of this repository are organized and how to use/interpret the data
4) How we apply the FAIR principles

the maturity assessment survey that produces the results contained in this repository can be found [here](https://ec.europa.eu/eusurvey/runner/Eminent). 

## How to perform a EMINENT maturity assessment

This section is split in two parts. The first on more logistical aspects of executing a maturity assessment and manageing the information, the second part on our experiences with interviewing methods.

### Executing a maturity assessment and managing results

If you wish to perform a maturity assessment of an interoperability community (like a standardization group, an open source project community or any other group of organizations and individuals that collaborate to solve a common problem in a standardized way), the [EMINENT questionnaire](https://ec.europa.eu/eusurvey/runner/Eminent) is the tool to use.

The process roughly looks as follows:

![Matrity assessment process](./DocumentationResources/ProcessesModels/AssessMaturityProcess/Assess%20Maturity%20Process.png)

In a nutshell:
1) the interoperability community reaches out to a researcher to perform a maturity assessment, and selects the group of interviewees
2) The researcher will create an identifier for the study and asks all respondents to fill in that code in question 10.
3) The researcher will conduct interviews with the identified group'
4) The researcher processes the data, creates a maturity assessment report and, depending on whether permission was given, adds the response data to this repository. 

The researcher has to options for using the survey. The first is to create an [issue](https://github.com/int-net/EminentResultsDatabase/issues), or contact the [int:net community](https://intnet.eu/) to use the survey published at [EUSurvey](https://ec.europa.eu/eusurvey/runner/Eminent). This is probably the easiest method as the researcher will be able to use the already implemented infrastructure. Members of the int:net community can also help process the data and add the results to this repository.

Alternatively, a researcher may decide to run a separate instance of the survey (that can be found [here](https://github.com/int-net/EminentSurvey)). This might be desirable if the researcher wants access to the raw EUSurvey data, if the results are particularly confidential, or if the researcher wishes to make modifications to the survey, for instance, if they wish to have more information about the respondents (NB. this may make the data incompatilble with the [data processing tooling](https://github.com/int-net/EminentReportingTool) used for this repository).

#### Submitting result data to this repository

EMINENT is a tool that aims to increase our ability to create interoperable solutions. Communities learning from eachother will absolutely stimulte that growth. So if you use this tool, pleas consider submitting the responses to this repository.

---

**NB: all responses that are collected using the EUSurvey version of the maturity assessment are completely anonymous. There is no way of tracing responses to an individual.**

---

If you wish to add your data to this publication. Please go through the following steps:

- Fork this repository
- Follow the instructuions [here](https://github.com/int-net/EminentReportingTool/blob/main/README.md) to transform the raw data from the EUSurvey xml format to RDF and merge that data to the graph pointing the ```input_rdf``` as well as the ```output_rdf``` variables of the ```responses_to_ld()``` function to the ```'./EminentResponses/EminentResponses.ttl'``` file (effectively replacing it).
- Create a pull request in this repository

### Best practices for interviewing

There are multiple ways of conducting this maturity assessment.

- In-person interviews where the researcher interviews every interviewee one by one
    - pro's: 
        - Intervierwees get to ask clarification questions
        - High response rate
    - cons: 
        - Time consuming. A study involving 10 interviewees, requires making 10 appointments of an hour
        - Isolation. the questionnaire involves complex questions/answers at a level some interviewees may not be operating on a day to day basis. The researcher can clarify questions, but cannot help the interviewee make the translation from the questions and examples in the survey to their real-world situation.
- Self assessment: the researcher sends the questionnaire around and interviewees fill it in at their own convenience
    - pro's: 
        - Very flexible
        - Relatively low effort for the researcher
    - cons:
        - low response rate: expect about 5-10% of the invited people to respond after multiple reminders.
        - Isolation: just like the previous method, but the interviewee cannot ask clarifying questions. We've received feedback that people just give up and don't submit the answers.
- Workshop: organize 1 or more sessions (on-line or in-person) where you fill in the survey simultaneously. It is important that every individual fills in their own survey as supposed to 1 survey for the group as opinions might vary and this should be reflected in the results and analysis
    - pro's:
        - Manageable effort for the researcher
        - Medium/high response rate (not all of the intended interviewees will be able to attend the workshop)
        - Group discussion: one of the biggest challenges fir most of the interviewees has been to translate the language of the questionnaire to their experience. In a group setting, people can discuss their interpretation or think of- and share- concrete examples of why they think a certain characteristic is appropriate for a given dimension. 
        - Interviewees get to ask clarification questions
    - cons: 
        - Workshops with many attending can be difficult to plan
        - strong voices may influence quiet dissenters in how they respond

During the int:net project, we found the 3rd option to be most effective. During the interviewing process, community members started to already think of ways the community could improve. Since this is a tool for learning and not for judgement, those discussions are the desired outcome, and without even seeing the report, that outcome was being achieved.



## How to perform a maturity tracking assessment

![Maturity tracking assessment process](/DocumentationResources/ProcessesModels/TrackMaturityProcess/Track%20Maturity%20Process.png)


## The database and how to use it



## How we apply the FAIR principles

Research data should support reproducabiltity and the advancement of knowledge. To support this the [GO_FAIR Innitiative](https://www.go-fair.org/go-fair-initiative/) has developed the **F**(indable)**A**(ccessible)**I**(nteroperable)**R**(euseable) principles. In this secion, we'll discuss 1 by one how we have tried to apply them to this data set.

### Findable

- F1: (Meta) data are assigned globally unique and persistent identifiers
    - Every response, answerset, and questionnaire, as well as the definitions in the information model and the maturity model are identified with a URI
- F2: Data are described with rich metadata
    - The data has the following metadata:
        - To which study the responses belong
        - Anonymized metadata of the area of expertize of the respondent as well as the area of operation of the organization they represent
        - which (version of) the questionnaire and questions were used.
- F3: Metadata clearly and explicitly include the identifier of the data they describe
    - The use of RDF for the serialization of the data makes this explicit
- F4: (Meta)data are registered or indexed in a searchable resource
    - Work in progress (will probably be registerd in [https://data.europa.eu/en](https://data.europa.eu/en))


### Accessible
- A1.1: The protocol is open, free and universally implementable.
    - The data is stored as RDF
    - on a github repository that may be cloned/forked
- A1.2: The protocol allows for an authentication and authorisation procedure where necessary
    - This dataset contains only open data so reading is open to anyone
    - If someone wishes to add to (write) the dataset, this is handled through gits merge process
- A2: Metadata should be accessible even when the data is no longer available
    - Work in progress

### Interoperable
- I1: (Meta)data use a formal, accessible, shared, and broadly applicable language for knowledge representation
    - the information model used is published in this repository and consists of the folling ontolgoies:
        - A specialization of the [sosa ontology](https://www.w3.org/TR/vocab-ssn/).
        - Elements of [prov-o](https://www.w3.org/TR/prov-o/)
        - Elements of FOAF
        - Elements of [Dublin Core Terms](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/)
        - Elements of [the Orgabization Ontology](https://www.w3.org/TR/vocab-org/)
        - Domain specific terminology that is defined with in artefacts in this repository
- I2: (Meta)data use vocabularies that follow the FAIR principles
    - As the information model is part of this repository, what is stated under this section applies to the information model as well
- I3: (Meta)data include qualified references to other (meta)data
    - The use of the above listed ontologies adds meaning to the relationships used in the data.

### Reusable
- R1: (Meta)data are richly described with a plurality of accurate and relevant attributes
    - See comments under F3, I1, I2 and I3. Particularly the metadata that is added to each answerset should help users get a sense of what perspective is represented by the answers.
- R1.1: (Meta)data are released with a clear and accessible data usage license
    - see the license added to this repository
- R1.2: (Meta)data are associated with detailed provenance
    - The use of the prov-o standard should make this more explicit, although the requirement to comply to the [GDPR](https://gdpr-info.eu/) means the ability to traceback answersets to individuals is not supported.
- R1.3: (Meta)data meet domain-relevant community standards
    - The use of information standards should simplify the use of this data.
    - the use of RDF is not necessarily common in the space of questionnaires, a domain in which spreadsheets are the more common format. However tooling has been provided for the most common analysis needs, as well examples of sparql quesries earlier in this document, to convert rdf to CSV based on the users need.
    - the Electrical utility domain, with its use of [CIM/CGMES](https://www.entsoe.eu/data/cim/cim-for-grid-models-exchange/) is not new to RDF.


We hope this section gives insight in how we try to uphold the FAIR principles for this dataset. If you have feedback or suggestions on how we can improve this, please feel free to raise an [issue](https://github.com/int-net/EminentResultsDatabase/issues).
