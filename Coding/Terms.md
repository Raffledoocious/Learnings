Second System Syndrome
	Tendency of small, elegant, successful systems to be succeeded by over engineered, bloated systems due to inflated expectations and overconfidence

DAO - Data Access Object
	Pattern that provides an abstract interface to some database or persistence mechanism
	Provides the operations with exposing the specific database
	Allows injecting mocks for testing
	
Access Terms
	RBAC - role based authentication
	ABAC - Attribute based authentication
		Based on what is on the subject
		Can have things such as job IDs, group memberships, department memberships
		Wants to access a Resource using an Action, can have environment contexts as well
		Easy to add new users, I am of title Y in department X, granular
	ACL - Access control list
		Grant or deny access to certain digital environments
		Can restrict filesystem or networking
		Based on identity vs your role or attributes

Log Tracing
	User's journey through an application
	Can be more detailed such as how you get into a function, what parameters
	Can be an expensive endeavor and hard to get the data organized
		