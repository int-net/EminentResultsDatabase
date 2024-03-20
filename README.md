# EMINENT Results Database

This work has received funding from the European Union’s Horizon Europe research and innovation programme under grant agreement N°101070086 (int:net).

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

After at least 2 maturity assessments have been performed on the same community (with sufficient time in between the studies), the communtie can request a maturity tracking report. This report summarizes the previous results and summarizes the change in maturity across the capabilities and dimensions over time.

The process to do so looks as follows:

![Maturity tracking assessment process](/DocumentationResources/ProcessesModels/TrackMaturityProcess/Track%20Maturity%20Process.png)

In a nutshell:
- the community requests a maturity tracking study
- a researchers gathers all public and/or confidendial response data
- the researcher performs a data analysis based on the communties needs and creates a report 

The researcher may have to reject certain older studies if insufficient people participated (as determined by requirements the community expressed for the study) or if the questionnaire changes sufficiently that the answers given previously cannot be compared any longer to answers given in more recent studies. 

---

NB: this is a senario that we intend to avoid for the public survey. But if a survey was modified for a prarticular study, this may become the case.

---

## The database and how to use it

This database consists of 3 parts:

1) Maturity Model and (over time) its versions
    - found in ```./EminentMaturityModel/```
2) The Survey and (over time) its versions
    - found in ```./EminentQuestionnaire/```
3) The responses to the questionnaire for all studies
    - found in ```./EminentResponses/```

These artifacts are published separately as they have a different change cycle. The maturity model and the questionnaire should hardly change over time, but if a change does occur, it might affect the interpretation of the response data. The responses data will change more regurlarly as new studies are being performed.

When these artifacts are combined into a single graph, they jointly paint a picture of the maturity of different communtities that participated in the studies. In this section, well go over informationsmodels (rdfs/owl ontologies) that describe the data in the different artifacts, and in the final part we'll show how all these models fit together.

### EMINENT Maturity Model

The eminent maturity model contains the Capabilities, Dimensions and Characterisitics that make up the EMINENT Maturity Model (hence the ```emm:``` prefix).

![Data model of the maturity model](./DocumentationResources/InformationModels/MaturityModelProfile/Maturity%20Model%20Profile.png)

The maturity model is pretty straight forward.

#### ```emm:Capability```

The ```emm:Capability``` class is meant to represent business capabilities as defined in [Archimate](https://pubs.opengroup.org/architecture/archimate3-doc/ch-Strategy-Layer.html). As these can be hierarchical , the ```dcterms:isPartOf``` relationsship is used to link sub-capabilities to their super-capabilities. The ```skos:definition``` attribute is used to define the capability in human readable format

#### ```emm:Dimension```

Within EMINENT we look at each capability across 4 dimensions:
- Process
- People and organization
- Information
- Resources

This class represents the individual dimension for each capability. For example: the information Dimension of Community Growth would be an element of this class. The information Dimension of Market Creation would be a different ([```owl:differentFrom```](https://www.w3.org/TR/2004/REC-owl-features-20040210/#differentFrom)) element in this class.

A dimension is linked to a capability using ```dcterms:isPartOf```, and the human readable definition is given using ```skos:definition```.

#### ```emm:Characteristic```

A Characteristic is a description of what a maturiity level for a given dimension and a given capability looks like. This is extpressed as a set of conditions that should be observed before the organization or interoperability community achieves the given level of maturity.

The description is given using ```skos:definition```. The ```ema:maturityScore``` contains the (integer between 0-5) mmatirty score that is associated with that chartacteristic.

### EMINENT Maturity Assessment 

The Eminent Maturity Assessment (hence the ``ema:`` prefix) contains the (machine readable format of the) questionnaire that is used for the interoperability maturity assesments. 

![Information model of the maturity assessment](./DocumentationResources/InformationModels/QuestionaireProfile/Questionaire%20Profile.png
)

#### ```ema:Questionnaire```

This is the class of questionnaires. In this database, this class will only see 1 instance of this class, ```ema:Eminent```, as all data in this database will be in response to that questionnaire, and all ema:QuestionnaireVersions will be different versions of that questionnaire. 

#### ```ema:QuestionnaireVersion```

This class models the different versions of the questionnaire. Every time changes are made to the questionnaire, it will be published as a ```new ema:QuestionnaireVersion```.

---

NB: By convention (for the purposes of EMINENT) version managament is handled at the questionnaire level. This means that Questions, though phrased differently across versions, will retain their URI and the distinction and difference management is indicated through their relationship to a version of the questionnaire.

---

The identifier that EUSurvey gives to the survey is published under ```dcterms:identifier```. the ```dcat:version``` denotes the version conform [semantic versioning](https://semver.org/) and the version has a title that is published as ```skos:prefLabel```.

#### ```ema:Question```

The ```ema:Question``` class contains the questions in the questionnaire. The human readable identifier is publishded as ```dcterms:identifier```. The way the question is phrased is published under ```ema:phrasing```. The question is associated to the ```emm:Dimension``` it measures through ```ema:measures```. 

### EMINENT Responses

The Eminent Responses contain the answers that were selected by the interviewees. 

![Information model of the EMINENT Responses](./DocumentationResources/InformationModels/AnswersetProfile/Answer%20Set%20Profile.png)

#### ```ema:Answer```

The ```ema:Answer``` models the ansers that respondents give to the questionnaire. Answers are connected to the Questions they answer through the ```sosa:usedProcedure``` association. The answer that was selected can be found through the ```sosa:hasResult``` attribute. In the context of this dataset, this will be an ```emm:Characteristic```. In case the description of the ```emm:Characteristic``` changes over time, the original text is stored under ema:resultText. The ```dcterms:isPartOf``` links the Answer to the AnswerSet (see below)


#### ```ema:AnswerSet```

The ```ema:AnswerSet``` models the set of answers that an interviewee has given to (a single itteration of) an interiview.

The ```sosa:usedProcedure``` association is used to link an ```ema:AnswerSet``` to the ```ema:QuestionnaireVersion```. 

The ```ema:AnswerSet``` is linked to (anonimous) metadata of the ```foaf:Person``` who prided the answerset through ```prov:wasQuotedFrom```

#### ```foaf:Person```

The definition of an individual person conform the Friend Of A Friend speciification.

A ```foaf:Person``` is linked to the organization they represent through the ```prov:actedOnBehalfOf``` relationship. While this database does not contain Peron Identifyable Information (PII), the person is annotated by their area of expertise (expressed using the SGAM model, see below). This information is linked via the ```ema:AreaOfExpertise```

#### ```org:Organization```

[Organziation](https://www.w3.org/TR/vocab-org/#class-organization) as defined by the organization ontology.

To avoid the possibility of identifying the person who answered the question if they represent a small organization (like a self employed consultant for instance), the database only stores some generic information about the organizartion. Notably: the ```ema:desscription``` which has the following possible values:

- Energy Utility
- Energy Market Party
- Government
- Vendor
- Consultancy
- Research

The ```ema:organizationSize``` attribute indicates the rough size of the organization, It has the following possible values:


- 1-10
- 11-100
- 101-500
- 501-1000
- 1001-5000
- more than 5000

The ```ema:sector``` attribute indicates the energy sector the organization is active in. It has the following possible values:



- Electricity
- Natural Gas
- Heat
- Hydrogen
- Other

Finally, the ```ema:areaOfOperation``` expresses the area of operation in terms of a ```ema:FocusArea```.


#### ```ema:FocusArea```

The ```ema:FocusArea``` class models a focus area (like an area of expertise or an area of operation) in terms of the SGAM model. It has three attributes:

- ```ema:inZone``` contains the SGAM Zones that are part of the focus area. 
- ```ema:inDomain``` contains the SGAM Domains that are part of the focus area. 
- ```ema:onLayer``` contains the SGAM Interoperability Layers that are part of the focus area. 


#### ```sgam:Zone```

This is the enumeration class that models the SGAM Zones. Possible values are:
- ```sgam:Process```
- ```sgam:Field```
- ```sgam:Operation```
- ```sgam:Enterprise```
- ```sgam:Market```

#### ```sgam:Domain```

This is the enumeration class that models the SGAM Domains. Possible values are:
- ```sgam:CostomerPremises```
- ```sgam:DER```
- ```sgam:Distribution```
- ```sgam:Transmission```
- ```sgam:Generation```

#### ```sgam:InteroperabilityLayer```

This is the enumeration class that models the SGAM Interoperability Layers. Possible values are:
- ```sgam:FrameworkLayer```
- ```sgam:BusinessLayer```
- ```sgam:FunctionLayer```
- ```sgam:InformationLayer```
- ```sgam:ProtocolLayer```
- ```sgam:ComponentLayer```


### The EMINENT Vocabulary

Combining the different models we have seen so far, we get a picture of what the totality of the information content looks like. This can be found in the diagram below:

![Eminent Vocabulary](./DocumentationResources/InformationModels/EminentVocabulary/Eminent%20Vocabulary.png)

For those interested in linked data intgration, this diagram also shows how the EMINENT information model is alligned with SOSA, FOAF and ORG. 

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
