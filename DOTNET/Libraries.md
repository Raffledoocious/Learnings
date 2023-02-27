Lightguard
  https://github.com/feO2x/Light.GuardClauses
  Library for easy conditional checks in C#
    
Rate Limiting
  https://github.com/stefanprodan/AspNetCoreRateLimit
  Tie into a cache and lets you set a lot of rules based on ip, path, client, etc
  You can fetch policies via prefix and a key to update them, Arthus uses this

AutoMapper
  https://github.com/AutoMapper/AutoMapper
  Way to map types from one to another, often between layer boundaries
  Configuration done on startup and once per AppDomains
  There's a way to make sure the mapping is valid, very cool!

Moq
  https://github.com/moq/moq4

  Strict vs Loose
    Strict - exception thrown whenever method or property is invoked without matching configuration
    Loose - All invocations accepted and Moq tries to create a default value
    Default - equivalent to loose
    var mock = new Mock<IService>(MockBehavior.Strict);

  Protected()
    Can use the protected namespace to mock out protected methods

    ```
    mock.Protected()
    .Setup("Step1")
    .Callback(() => TestContext.Progress.Writeline("Step1"));
    ```

    Notice that you must call what you are mocking by name.
