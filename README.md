<img alt="packageIcon" src="https://github.com/endecipher/ActivityLogger/blob/main/packageIcon.png" width=20% height=20%> 

# ActivityLogger

Simple, extensible activity/event logging implementation for .NET

[![NuGet version (ActivityLogger)](https://img.shields.io/nuget/v/ActivityLogger.svg?style=flat-square)](https://www.nuget.org/packages/ActivityLogger/)

## Documentation

Extend and register (as a Singleton) via DI the below interface for logging activities.
```C#
public interface IActivityLogger
{
    void Log(Activity e);
}
```

Create your custom Activities by inheriting from the below:
```C#
public abstract class Activity : IActivity
{
    
}
```



Basic properties would include
```C#
ActivityLogLevel Level // LogLevel enum
string EntitySubject 
string Event 
string Description 
DateTimeOffset EventTime 
```

Apart from the above, each Activity can hold an optional number of parameters/entities/objects
```C#
AddParam(ActivityParam param)
```

An Activity can be enhanced with Caller Information by using 
```C#
WithCallerInfo()
```

An Activity can be also be enhanced with certain context related information, which would be certain common properties, specific to application usage (or) context


### Example usage
```C#
ActivityLogger?.Log(new ConcreteActivity
{
    Description = $"",
    EntitySubject = "",
    Event = "",
    Level = ActivityLogLevel.Debug,

}
.With(ActivityParam.New(Id, ""))
.With(ActivityParam.New(State, ""))
.WithCallerInfo());
```

 



## Contributing

Contributions are always welcome!



## Authors

- [@endecipher](https://www.github.com/endecipher)


## License

[MIT](https://choosealicense.com/licenses/mit/)

