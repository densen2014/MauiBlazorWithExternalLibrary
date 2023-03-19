# Description

main maui blazor project ([MauiApp1](https://github.com/densen2014/MauiBlazorWithExternalLibrary/tree/master/MauiApp1))  and a external library with file with razor ([TestLibrary](https://github.com/densen2014/MauiBlazorWithExternalLibrary/tree/master/TestLibrary))

[TestLibrary.csproj](https://github.com/densen2014/MauiBlazorWithExternalLibrary/blob/master/TestLibrary/TestLibrary.csproj)

```
<Project Sdk="Microsoft.NET.Sdk.Razor">


    <PropertyGroup>
        <TargetFrameworks>net7.0;net7.0-android;net7.0-ios;net7.0-maccatalyst</TargetFrameworks>
        <TargetFrameworks Condition="$([MSBuild]::IsOSPlatform('windows')) and '$(MSBuildRuntimeType)' == 'Full'">$(TargetFrameworks);net7.0-windows10.0.19041.0</TargetFrameworks>

        <ImplicitUsings>enable</ImplicitUsings>
        <Nullable>enable</Nullable>
        <SingleProject>true</SingleProject>
        <SupportedOSPlatformVersion Condition="$([MSBuild]::GetTargetPlatformIdentifier('$(TargetFramework)')) == 'ios'">14.2</SupportedOSPlatformVersion>
        <SupportedOSPlatformVersion Condition="$([MSBuild]::GetTargetPlatformIdentifier('$(TargetFramework)')) == 'maccatalyst'">14.0</SupportedOSPlatformVersion>
        <SupportedOSPlatformVersion Condition="$([MSBuild]::GetTargetPlatformIdentifier('$(TargetFramework)')) == 'android'">21.0</SupportedOSPlatformVersion>
        <SupportedOSPlatformVersion Condition="$([MSBuild]::GetTargetPlatformIdentifier('$(TargetFramework)')) == 'windows'">10.0.17763.0</SupportedOSPlatformVersion>
        <TargetPlatformMinVersion Condition="$([MSBuild]::GetTargetPlatformIdentifier('$(TargetFramework)')) == 'windows'">10.0.17763.0</TargetPlatformMinVersion>
        <SupportedOSPlatformVersion Condition="$([MSBuild]::GetTargetPlatformIdentifier('$(TargetFramework)')) == 'tizen'">6.5</SupportedOSPlatformVersion>
        <Configurations>Debug;Release</Configurations>
		<!--<UseMaui>true</UseMaui>-->
	</PropertyGroup>
    
    <ItemGroup>
        <PackageReference Include="Microsoft.AspNetCore.Components.Web" Version="7.0.4" />
    </ItemGroup>

    <PropertyGroup>
        <ImplicitUsings>enable</ImplicitUsings>
        <Nullable>enable</Nullable>
    </PropertyGroup>
    
    <PropertyGroup>
        <LangVersion>latest</LangVersion>
    </PropertyGroup> 
    
</Project>
```

### **Debug and build in windows have not error, but in vs for mac, show this error**  

![image](https://user-images.githubusercontent.com/8428709/226189046-dab643a6-19ac-4a4f-81ca-77ac56ebeefc.png)

### if add `<UseMaui>true</UseMaui>` to TestLibrary.csproj and donet restore, it works, but i don't need all External Library **UseMaui**

### demo
https://github.com/densen2014/MauiBlazorWithExternalLibrary

Installed Workload ID     Manifest Version    Installation Source File   
-----------------------------------------------------
maui-maccatalyst      7.0.59/7.0.100      SDK 7.0.200
maui-ios              7.0.59/7.0.100      SDK 7.0.200
maui-android          7.0.59/7.0.100      SDK 7.0.200


# Steps to Reproduce

1. create a main maui blazor project 
2. create a external library with file with razor `<Project Sdk="Microsoft.NET.Sdk.Razor">`
3. add a razor file to external library
4. add a external library reference to main maui blazor project 
5. debug
