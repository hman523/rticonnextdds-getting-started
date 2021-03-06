# Introduction to Keys and Instances (C#)

**IMPORTANT: The new RTI Connext DDS C# API used in this example is a Preview
and cannot be used in production.**

This code follows the "Introduction to Keys and Instances" chapter of the
[RTI Connext DDS Getting Started Guide](https://community.rti.com/static/documentation/connext-dds/6.0.1/doc/manuals/connext_dds/getting_started/index.html).
Currently that guide walks you through the C++ examples, but you can follow it to
understand what the example does and the DDS concepts it demonstrates.

## Setup
This example requires a *Connext DDS* installation to run the *RTI Code Generator (rtiddsgen)* (see next section). The *RTI Connext DDS C# API Preview* library is
automatically downloaded from nuget.org when you run the example.

The example requires a valid license file, which can be configured with
the `RTI_LICENSE_FILE` environment variable. Follow the instructions under
"Setting Up a License" in the [Getting Started Guide](https://community.rti.com/static/documentation/connext-dds/6.0.1/doc/manuals/connext_dds/getting_started/index.html).

## Run Code Generator
This examples dynamically loads the types it needs from an XML file and uses
`DynamicData` to publish and subscribe to topics. Support for C# types generated
from IDL is not yet available in this Preview release.

To generate the XML definition of the types from IDL, run
*RTI Code Generator (rtiddsgen)* as follows:

```bash
cd 4_keys_instances
rtiddsgen -convertToXml chocolate_factory.idl
```

This generates the file `chocolate_factory.xml`, which is loaded by `ChocolateFactoryTypes.cs` in `4_keys_instances/csharp/Utils/`.

## Build and Run the Applications

This example uses the .NET Core command-line interface (`dotnet`). You can also
build the solution file (`KeysInstances.sln`) from *Visual Studio 2019* or
*Visual Studio for Mac*. *Visual Studio Code* also provides excellent language
support.

From within the `3_keyes_instances/csharp` directory run the following command:

```bash
dotnet run -p TemperingApplication
```

From another command prompt, run:
```bash
dotnet run -p MonitoringCtrlApplication
```

You can run multiple copies of the tempering application on differet terminals:
```bash
dotnet run -p TemperingApplication -- -id 1
```

```bash
dotnet run -p TemperingApplication -- -id 2
```

**Note**: These examples are configured to build a *.NET Core 3.x* application, but
the library is compatible with any *.NET Standard 2.0*-compatible runtime.

If you want to use *.NET 5*, simply edit the `.csproj` files and change:
```xml
<TargetFramework>netcoreapp3.0</TargetFramework>
```

To:
```xml
<TargetFramework>net5</TargetFramework>
```
