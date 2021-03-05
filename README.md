# RouteConfiguration

this library help you to clean your configure method in startup class.
by this library, your routing goes to another class .


## step one
in the first step (after adding this library to your project), create a class that implement IProfileRouteMapper interface.
in this interface , you must create your routes.
you can set patterns,names,Constrants,DataTokens and options in here by chain routeMapBuilder methods. 
![image](https://user-images.githubusercontent.com/36743160/110174191-01877680-7e15-11eb-881d-0f643a0450a6.png)


## step two
in your configureService method in Startup class , add this lines of code.
services.AddSingleton<IProfileRouteMapper, "your class name in prior step" >();
services.Configure<Profile>(c => { });
  
## step three
add IOptions<"your class name in prior step"> in configure method (this is inject by DI)

![image](https://user-images.githubusercontent.com/36743160/110174558-883c5380-7e15-11eb-80af-943a8aa5bc83.png)

## step four
set bottom code in the end of configure method.

app.UseEndpoints(endpoints =>
{
     endpoints.MapperEndPoint(configure.Value);
});
