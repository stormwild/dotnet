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

Run the app

```
dotnet run
```



## References:

- [Install .NET and build your first app on Ubuntu or Mint](https://www.microsoft.com/net/core/#linuxubuntu)
- [“method driver /usr/lib/apt/methods/https could not be found” update error](https://askubuntu.com/questions/104160/method-driver-usr-lib-apt-methods-https-could-not-be-found-update-error)
- [Getting Started with ASP.NET Core](https://docs.microsoft.com/en-us/aspnet/core/getting-started)

