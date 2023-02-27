AWS
	It is a good idea to filter costs based on tagging
	
	CodeDeploy
		Automates deployments to any instance, EC2 or on prem
		Handles complexity of updating applications
		Works with nearly any AWS service
		
	CodePipeline
		Fully managed delivery service, this is the one that ties all of the otheres together
		Plugin architecture
		
	Simple Notification Service
		Send messages with SMS
		Can also do application to application requests
	
	CodeBuild
		Fully managed build service, don't worry about build servers
		Custom build environments, scaling, use existing tools
		
	Private Link
		Private connectivity between VPCs in AWS or on prem
		Does not expose traffic to the public internet
		Does not need firewall or route tables, easier to manage
		
	Transit Gateway
		Central hub to connect VPCs and on-premis networks
		Think of it as a cloud router
		Inter-region pairing supported
		Central console for managing edge connections
		Encryptes all traffic
		Multicast supported
		It's a regional resource and can connect VPCs within same AWS region
		Can be peered with other Gateways
	
		Why this versus a Private Link
			Private link doesn't care about overlapping CIDR blocks
			Partner connections over Private Link are unidirectional
			It's the hub in a large hub and spoke peering networks
			
	Elastic Container Service
		You build and store the images in ECR
		Select images and resources, Fargate, regions, local zones, outposts
	
	DynamoDB
		Fully managed, serverless, key-value NoSQL database
		Security, continuous backup, multi-region backup, in-memory caching
		Uses - media, multidata stores
		
		Streams
			When enabled it captures a time ordered sequence of item level modifications in DynamoDB table and stores for up to 24 hours
			Separate endpoint
			Contains following views for KEYS_ONLY, NEW_IMAGE (after modified), OLD_IMAGE, NEW_AND_OLD_IMAGES
			
			Posts events that you can then react on and modify with queries
			Stores changes to table in a log
			
			Time ordered, YOU are responsible for handling errors, not the Stream
	
	AppConfig
		Capability of AWS Systems Manager - lets you deploy application configuration
		Use an IAM role, access control list, feature flags, settings to store into JSON
		Allows successful deployment, canary, rollback, alarms
		Can manage via the AWS console
	
	Parameter Store
		Hosted secrets management, just straight string management
		
		Vs Secret Manager
			Different sizes, Secrets Manager offers 64Kb, Parameter Store offere 8Kb
			You can encrypt either
			Parameter store is not just secrets, think of it as general string store
			Secret Manager allows different versions to be active at once when you are doing a key rotation
				Uses labels to define this
			Can access Secret Manager secrets across accounts
		

    Lambda
        Extensions
            A way to integrate with external tools like monitoring and governance
            Automatically instrument code without changes
            Can be installed in a container or as a layer
            Builds on an existing API to hook into Lambda execution

        Layers
            A way to add in additional runtime processes for a lambda
		
	Secret Manager
		Store credentials, API keys, and other secrets, consumed by other apps
		Lambda rotates them on a schedule
		
	KMS
		Manage cryptographic keys across applications
		Can encrypt the keys with the SDK
		Signing
		Can generate hash-based authentication codes
	
	Fargate
		Lets you define your container image the resources your need
		Pay for requested compute resources
		Makes the management as abstract as possible
	
	ECS TargetGroup
		Where you can route requests, LoadBalancer gets you to target it
	
	Aurora Postgres
		RDS abstracts away the operations of running EC2
		Aurora splits between Storage and Compute
		A lot of availability zones across cluster nodes, replicas
		There's a serverless component which lets you automatically scale the databases
		Only supports certain engines
		Closest to CosmosDB
		
	API Gateway
		Managing WebSocket APIs at scale
		RESTful, stateless, client/server communication
		
	Simple Queue Service (SQS)
		Fully managed message queue that enable you to decouple and scale microservices
		Allows encryption
		Easy to scale
		Highly available, abstracted, and uses Server Side Encryption
		
	Simple Notification Service (SNS)
		Application to application (think messages) or Application to person (think SMS)
		A2A allows connections to wide variety of services and connections
	
	Private Hosted Zone DNS
		Container that holds information about how you want Amazon Route 53 to respond to DNS queries for a domain and its subdomains within one or more VPCs
		Associate VPCs with the hosted zone
		Create records in the hosted zone to determine how Route 53 responds to queries
	
	Inspector
		Enabled in a few clicks, workloads scan for vulnerabilities
		Contextualizes findings into a single score you can use
		Easily recomended patch remdiation, compliance requirements, zero days 
		
	Kinesis
		A set of shards which contain a sequence of records
		Can have applications which read from the shards
		Accelerated data feed intake
		Real time metrics and reporting - parallel processing via the applications
		
		Reading in a Lamba
			Polls shard in stream using HTTP protocol
			Dedicated connection to each shard that doesn't impact other reading applications
			Reads records in batches
			Invokes function in batches, could be one or many records to iterate through
			Failure options include doing retries, smaller batches, discard records that are too old
				It is possible to push failures to SQS queue or SNS topic
			If you do multiple batches at once, in order is guaranteed at the shard level
			
	EventBridge
		Serverless event bus that lets you receive, filter, transform, and route events
		Push to common, partner, custom event buses with a common schema registry, code binding to a lambda, sns, other API destinations
		Stream of real time data from applications and SaaS applications
		
		Receives event and applies rule to route to a target
		Create event buses which have their own rules
		Allows input transformers and other options to work with the data
	
	Graviton Processor
		Armed based EC2 instance using an open architecture, took an existing one and modified it for how EC2 works
