		
C#
	Default time is 1/1/0001 at 12 AM
	
	AppDomain
		 Provide an isolation boundary for security, reliability, and versioning, and for unloading assemblies
		 Typically created by runtime hosts
		 
	Task.Yield()
		Lets you return things as they complete, one at a time so you can use immediately
		You can await on a foreach and have yield in an async method
		
	RecyclableMemoryStream
		Superior behavior for performance critical systems
		Uses pooled buffers to eliminate large object heap collection
		Spend less time paused in GC
		Bounded pool size
		Avoid extraneous allocations
		Metrics for performance tracking
		Thread safe!
		
	Record Types
		Immutable datatype with read only properties, must use init; modifier on properties
		
	IHealthCheck
		Check the status of a component in the systems
		Can also call manually
		Typically used externally to monitor an app's status
		You map the health check to an endpoint for checking in on the app
		
	Exception Filter
		An exception filter is executed when a controller method throws any unhandled exception that is not an HttpResponseException exception.
		
	
	C# 8 switch syntax
	  var result = status switch
            {
                HealthStatus.Unhealthy => HealthCheckResult.Unhealthy(_failedMessage),
                HealthStatus.Degraded => HealthCheckResult.Degraded("Dependencies haven't been initialized yet."),
                _ => new HealthCheckResult(status),
            };
		default at the end
		
	using statement
		Doesn't require braces in C# 8
		Calls dispose when an object goes out of scope
		using StringReader left = new StringReader(numbers), right = new StringReader(letters);
			Declaration syntax in C# 8 which lets you declare the same type 
			
	Scrutor
		Uses the same ASP.NET Core container registration
		Can scan calling assemblies, executing assemblies, entry assembly, depedencies, contexts
		Can add nested, internal, private classes
			Filter by namespace, name a class ends with, duplicate service
		Can close generic types
		Specify the lifetime of your registrations
		
	DispatchProxy vs RealProxy
		RealProxy can't be used as remoting is not supported in .NET Core
		
		
	Remoting
		Used for communicating across application domains which is troublesome
		Use IO.Pipes or MemoryMappedFile class, StreamJsonRPC
		Use network for across machines
		
	Access modifiers
		Sealed - no other class can inherit from it
		
	RealProxy
		Crosscutting concerns, things that belong to the whole application domain and not just one
		IPropertyChanged events, logging, verification, authentication
		Decorate means you create a new class that decorates and calls the old one
			Negative is you have a lot of classes which duplicate the information, lots of aspect classes, per one that you want logging for
		Generic of type T and then calls the base constructor
		
		// with one proxy
		public static IRepository<T> Create<T>()
		{
			var repository = new Repository<T>();
			var dynamicProxy = new DynamicProxy<IRepository<T>>(repository);
			return dynamicProxy.GetTransparentProxy() as IRepository<T>;
		}
		
		public static IRepository<T> Create<T>()
		{
			var repository = new Repository<T>();
			var decoratedRepository =
			  (IRepository<T>)new DynamicProxy<IRepository<T>>(
			  repository).GetTransparentProxy();
			  
			// Create a dynamic proxy for the class already decorated
			decoratedRepository =
			  (IRepository<T>)new AuthenticationProxy<IRepository<T>>(
			  decoratedRepository).GetTransparentProxy();

			return decoratedRepository;
		}
		
		You can also do filtering
			private Predicate<MethodInfo> _filter;
			
			public static IRepository<T> Create<T>()
			{
				var repository = new Repository<T>();
				var dynamicProxy = new DynamicProxy<IRepository<T>>(repository)
				{
					Filter = m => !m.Name.StartsWith("Get")
				}
				
				return dynamicProxy.GetTransparentProxy() as IRepository<T>;  
			}

	INotifyPropertyChanged
		Used more in UIs where it raises an event when a property changes so you can act on it
	
	
	WhenAny
		Creates a task that will complete when any of the supplied tasks have completed, even if the first one faults
	
	SelectAny
		Flattens list of lists into a single list
		IEnumerable<PhoneNumber> phoneNumbers = people.SelectMany(p => p.PhoneNumbers);
	
Working with nulls in .NET 7
  ??= 
    Null coalescing operator
    Returns values of left hand operand if null, otherwise evaluates the left hand operator

    Example code:
```
int? value = null;

Console.WriteLine(value is null); // true
value ??= 10;
Console.WriteLine(value); // 10
```

  null-forgiving operator
    ```
    #nullable enable
public class Person
{
    public Person(string name) => Name = name ?? throw new ArgumentNullException(nameof(name));

    public string Name { get; }
}
```

  value! says to ignore/suppress the null warnings
  When the compiler doesn't recognize it can't be null but you know it to be true
  Has not effect at runtime, only used in static analysis, at runtime the value is evaluated

Inline assignment
- public int Value { get; set; } = 10;


