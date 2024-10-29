---
tags: 🧠️/📥️/🏛️/🟥️
source: 
publish: true
parent: 
aliases: 
type: course
status: 🟥
---

Related: [[Data Engineering]]
URL: 

## Introduction to data engineering
* Intro
	* Data flow in an org and where Data engineers come in. 
	* Requirement gathering 
	* Think like a data engineer
		* Identify business goals and stakeholder needs
			* identify business goals and stakeholders you will serve
			* Explore existing systems and stakeholder needs
			* Get an idea of stakeholder actions with data product
		* Define system requirements
			* translate stakeholder needs to functional requirements
			* define non-functional requirements
			* document and take signoff
		* Choose tools and technologies
			* identify tools and tech to meet non-fucntional reuqirements
			* perform cost benefit analysis and choose between comparable tools and tech
			* prototype and test your system, align with stakeholder needs
		* Build, evaluate, iterate, evolve
			* build and deploy your production data system
			* monitor, evaluate and iterate on your system to improve it
			* evaluate your system based on stakeholder needs
	* [[Data Engineering]] on the cloud
		* On prem -> cloud migration is frequent, but not a part fo this course. 
		* aws service categories: 
			* compute: 
				* ec2(VMs)
				* lambda: serverless functions - runs in response to a trigger
				* ECS(elastic container service)
				* EKS(Elastic K8s service)
			* Networking: 
				* VPC(private network cloud)
					* region bound
			* Storage: 
				* object storage-s3, unstructured data
				* block-ebs, db storage, low latency env, other features specific to DB's
					* ==RDS-relational db==
					* ==redshift - data warehouse, can perform data transformations here==
				* File storeage-efs, file structure based
			* security -- AWS owns security OF the cloud, you are responsible for security IN the cloud
	* Data engineering lifecycle
		* diagram: 
			* ![](https://i.imgur.com/M2mWm7y.png)
		* 

		* queries, modelling and transformation
			* queries are typically written in sql
				* ![](https://i.imgur.com/ljarRhZ.png)
				* query is kept seperate from transformation, as it is a significant part, and writing a bad query can result in db's going down. 
				* its good to have a in depth knowledge of how the query is being processed.
			* data modelling: choosing a structure of data that is useful for end user(data analyst/data scientist)
				* this includes denormalizing data, standardizing terminology(different departments might be having different meanings for customer field)
			* data transformation: 
				* next step: data after modelling is manipulated, enhanced and saved for BA/DS. 
				* it might be a multi step process as the data moves through the architecture.
				* 

	* Undercurrents in data engineering lifecycle
		* security
		* data management
		* data architecture
		* Dataops
		* Orchestration
		* software engineering
	* AWS examples
* Data architecture
	* what is it?
	* principles
	* failure scenarios
	* batch & streaming architectures
	* compliance 
	* Choosing the right technologies
	* investigating your architecture on AWS
* Translating requirements to architecture
	* stakeholder management and requirement gathering
	* translating to architecture
	* 