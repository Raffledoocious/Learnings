Veracode
	Governance and app security scanning
	Vulnerability scan of packages and application
	Static analysis, dynamic analysis, composition analysis
	
Swashbuckle
	Embedded UI included for Swagger documents
	Swagger and OpenAPI generator

OpenAPI and Swagger
	OAS 3.0 is the specification and Swagger is the implementation
	Specification of your APIs
	Swagger has a lot of tooling around editing these documents, generating code, and UI
	x-nullable to mark as can be null		
	
Coverlet
	Cross platform unit test coverage
	https://github.com/coverlet-coverage/coverlet
			
NSwag
	Let's you easily generate clients through the APIs
	Desktop app supported and a variety of means to generate clients
	Use an nswag.json to specify how generation works

GoldenGate
	Allows you replicate, filter, and transform data from one database to another
	Only moves committed transactions
	Data movement is in real time
	
Casbin
	Enforce policy on the objects
	Manage the role-user mappings and role-role mappings
	Built in Superusers and root roles
	
SourceGraph
	https://about.sourcegraph.com/
	GitHub interaction for repository searching and discovery
	Target vulnterabilities, find issues

Protocol Buffers
    Message formats are defined in their own .proto file
    Portable, space efficient, automated
    Protobuffer compiler will implements the encoding and parsing of data in an efficient binary format
    Define messages as aggregations of typed fields
    Compiler will generate the C# files as needed
    You tag fields with tag numbers (string number = 1;), this defines what the field uses in binary encoding

    Backwards compatability
        Must not change the tag numbers
        You CAN delete fields
        You can add fields but you must use new tag numbers