# dotnet

DotNet Core Application

## Install 

### Add the dotnet apt-get feed

```
curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
sudo mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg
```

### Register the Microsoft Product feed for your distro version

Ubuntu 14.04 / Linux Mint 17

```
sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-trusty-prod trusty main" > /etc/apt/sources.list.d/dotnetdev.list'
```

### Update your package catalog

```
sudo apt-get update
```

If this fails with an error similar to 

```
“method driver /usr/lib/apt/methods/https could not be found” update error
```

Run the following:

```
sudo apt-get install apt-transport-https
```

Then run

```
sudo apt-get update
```

### Install .NET Core SDK

```
sudo apt-get install dotnet-sdk-2.0.0
```

### Initialize some code

```
dotnet new console -o .
```

A `Program.cs` file will be created

```
using System;

namespace hwapp
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

### Run the app

```
dotnet run
```

### Create web app

```
dotnet new web -o . --force
```

Use --force to overwrite existing project.

This creates a new web app.

To specify host and port modify `Program.cs` to use the following:

```
public static IWebHost BuildWebHost(string[] args) =>
            WebHost.CreateDefaultBuilder(args)
                .UseStartup<Startup>()
                .UseUrls("http://0.0.0.0:8080")
                .Build();
```

Add `.UseUrls("http://0.0.0.0:8080")` to specify host and post to run

It may also be possible to specify host and port using environment variables <sup>[4][4]</sup>

```
ASPNETCORE_URLS="https://*:5123" dotnet run
```

Run the app

```
dotnet run
```

### Templates

You can generate different .NET applications

```
Templates                                         Short Name       Language          Tags               
--------------------------------------------------------------------------------------------------------
Console Application                               console          [C#], F#, VB      Common/Console     
Class library                                     classlib         [C#], F#, VB      Common/Library     
Unit Test Project                                 mstest           [C#], F#, VB      Test/MSTest        
xUnit Test Project                                xunit            [C#], F#, VB      Test/xUnit         
ASP.NET Core Empty                                web              [C#], F#          Web/Empty          
ASP.NET Core Web App (Model-View-Controller)      mvc              [C#], F#          Web/MVC            
ASP.NET Core Web App                              razor            [C#]              Web/MVC/Razor Pages
ASP.NET Core with Angular                         angular          [C#]              Web/MVC/SPA        
ASP.NET Core with React.js                        react            [C#]              Web/MVC/SPA        
ASP.NET Core with React.js and Redux              reactredux       [C#]              Web/MVC/SPA        
ASP.NET Core Web API                              webapi           [C#], F#          Web/WebAPI         
global.json file                                  globaljson                         Config             
Nuget Config                                      nugetconfig                        Config             
Web Config                                        webconfig                          Config             
Solution File                                     sln                                Solution           
Razor Page                                        page                               Web/ASP.NET        
MVC ViewImports                                   viewimports                        Web/ASP.NET        
MVC ViewStart                                     viewstart                          Web/ASP.NET        


Examples:
    dotnet new mvc --auth Individual
    dotnet new webapi 
    dotnet new --help
```


## References:

1. [Install .NET and build your first app on Ubuntu or Mint](https://www.microsoft.com/net/core/#linuxubuntu)
2. [“method driver /usr/lib/apt/methods/https could not be found” update error](https://askubuntu.com/questions/104160/method-driver-usr-lib-apt-methods-https-could-not-be-found-update-error)
3. [Getting Started with ASP.NET Core](https://docs.microsoft.com/en-us/aspnet/core/getting-started)
4. [Specifying a Port Number to the dotnet run Command in ASP.Net Core](http://mrshipley.com/2016/11/29/passing-a-port-number-to-the-dotnet-run-command-in-asp-net-core/)
5. [Getting started with ASP.NET Core MVC on Mac, Linux, or Windows](https://docs.microsoft.com/en-us/aspnet/core/tutorials/first-mvc-app-xplat/start-mvc)



[4]: http://mrshipley.com/2016/11/29/passing-a-port-number-to-the-dotnet-run-command-in-asp-net-core/  "Specifying a Port Number to the dotnet run Command in ASP.Net Core"

