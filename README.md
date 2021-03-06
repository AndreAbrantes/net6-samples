# .NET 6.0.0 Client App Samples for Android, iOS, macOS, and Windows

_These apps are based on previews of Mobile (iOS/Android) and Desktop (macOS/Windows) in .NET 6 which are **not for production use**. Expect breaking changes as this is still in development for .NET 6._

If you are looking for the absolute newest download links, see the [develop](https://github.com/dotnet/maui-samples/tree/develop) branch.

## Installing with .NET MAUI Check Tool

This is a community supported, open source, global dotnet tool intended to help evaluation your development environment and help you install / configure everything you need to build a .NET MAUI application.

Install: `dotnet tool install -g redth.net.maui.check`

Run: `maui-check`

This will evaluate your environment and in most cases optionally install / configure missing components for you, such as:

* OpenJdk / AndroidSDK
* .NET 6 Preview SDK
* .NET MAUI / iOS / Android workloads and packs
* .NET MAUI Templates
* Workload Resolver .sentinel files for dotnet and Visual Studio Windows/Mac
* Currently does not install workloads required for WinUI3

For more information and source code, visit [redth/dotnet-maui-check](https://github.com/redth/dotnet-maui-check)

## .NET 6 Preview Installers

If you prefer to install everything manually, you can find all of the official installer links below:

* Windows: [dotnet-sdk-6.0.100-preview.5.21302.13-win-x64.exe](https://download.visualstudio.microsoft.com/download/pr/df52c798-6143-42f1-98e0-9cc7fc6257cd/cc09da4dcb8a59c1dcf905952f3382a1/dotnet-sdk-6.0.100-preview.5.21302.13-win-x64.exe)
* macOS: [dotnet-sdk-6.0.100-preview.5.21302.13-osx-x64.pkg](https://download.visualstudio.microsoft.com/download/pr/134a7c15-69cf-40b3-ba78-a78a666ac2de/996de9580ee6c05b2bcb0e9456fdf877/dotnet-sdk-6.0.100-preview.5.21302.13-osx-x64.pkg)

_NOTE: newer builds of .NET *may* work, but your mileage may vary.
You can find the full list of builds at the [dotnet/installer][dotnet/installer] repo._

## `dotnet workload install` Command

A new `dotnet workload install` command is available for installing
the mobile workloads.

On Windows, in an Administrator command prompt:

    > dotnet workload install microsoft-android-sdk-full

On macOS, you'd need to use `sudo`:

    $ sudo dotnet workload install microsoft-android-sdk-full

The workload ID for each platform is:

* `microsoft-android-sdk-full`
* `microsoft-ios-sdk-full`
* `microsoft-maccatalyst-sdk-full`
* `microsoft-macos-sdk-full`
* `microsoft-tvos-sdk-full`

> NOTE: using `maui-check` is the preferred method for installing
> workloads, because it will check your system for other software.

## Projects

* HelloMaui - a multi-targeted .NET MAUI Single Project for iOS and Android
* HelloAndroid - a native Android application
* HelloiOS - a native iOS application
* HelloMacCatalyst - a native Mac Catalyst application
* HelloWinUI3 - .NET MAUI WinUI3 application. WinUI3 requires build and deploy with the latest preview of Visual Studio 2019 16.11. .NET MAUI WinUI currently does not work with Visual Studio 2022

[dotnet/installer]: https://github.com/dotnet/installer#installers-and-binaries

## Android

Prerequisites:

* Starting in .NET 6 Preview 4, [Microsoft OpenJDK 11](https://www.microsoft.com/openjdk) is recommended.
* You will need the Android SDK installed as well as `Android SDK Platform 30`. Simplest way to get this is to install the current Xamarin workload and go to `Tools > Android > Android SDK Manager` from within Visual Studio.

For example, to build the Android project:

    dotnet build HelloAndroid

You can launch the Android project to an attached emulator or device via:

    dotnet build HelloAndroid -t:Run

## iOS

Prerequisites:

* Xcode 12.5. Earlier versions won't work.

To build the iOS project:

    dotnet build HelloiOS

To launch the iOS project on a simulator:

    dotnet build HelloiOS -t:Run

## WinUI3

Currently WinUI3 requires build and deploy. You will need to open the HelloWinUI3.sln with the latest preview of Visual Studio 2019 16.11. WinUI currently does not work with Visual Studio 2022

* Windows: [Get started with Project Reunion](https://docs.microsoft.com/en-us/windows/apps/project-reunion/get-started-with-project-reunion#set-up-your-development-environment)

- Install the following 0.8 Preview Reunion VSIXs. .NET MAUI currently only works with 0.8 Reunion Preview and will not work with 0.8 Reunion Stable.
  - Uninstall any WinUI extensions that you may have previously installed
  - https://marketplace.visualstudio.com/items?itemName=ProjectReunion.MicrosoftProjectReunionPreview
  - https://marketplace.visualstudio.com/items?itemName=ProjectReunion.MicrosoftSingleProjectMSIXPackagingTools

## .NET MAUI

To launch the .NET MAUI project, you will need to specify a `$(TargetFramework)` via the `-f` switch:

    dotnet build HelloMaui -t:Run -f net6.0-android
    dotnet build HelloMaui -t:Run -f net6.0-ios
    dotnet build HelloMaui -t:Run -f net6.0-maccatalyst

## Using IDEs

IDE integration into Visual Studio, Visual Studio for Mac, and Visual Studio Code are a work in progress. 

### Visual Studio

Currently, you can use Visual Studio 2019 16.11 on Windows (with the
Xamarin workload installed). .NET 6 Preview 5 requires MSBuild 16.11,
so .NET 6 projects will not be able to load in older versions of
Visual Studio.

### Visual Studio for Mac

Visual Studio for Mac is not supported at this time, but will be coming in a future release.

### iOS from Visual Studio

To build and debug .NET 6 iOS applications from Visual Studio 2019 you must manually intall the .NET 6 SDK and iOS workloads on both **Windows and macOS** (Mac build host).

If while connecting Visual Studio to your Mac through XMA you are prompted to install a different version of the SDK, you can ignore that since it refers to the legacy one.

> Note: currently only the iOS simulator is supported (not the remoted simulator).

### Mac Catalyst from Visual Studio for Mac

Running and debugging apps from Visual Studio for Mac is not supported at this time..

### Known Issues - Visual Studio & Visual Studio for Mac

* There are no project property pages available for both iOS and Android
* Editors (i.e. Manifest editor, Entitlements editor, etc.) will fail to open, so as a workaround please open those files with the XML editor.

### Visual Studio Code

Support has been added to allow debugging of **Android** based apps in Visual Studio Code. Open the `net6-mobile-samples.code-workspace` in Visual Studio Code.

    > code net6-mobile-samples.code-workspace

To build your application use open the Command Pallette and select `Run Build Task`. Select `Build` and then the `Target` you want to run. Available targets are:

* `Build` : Builds the Project.
* `Install` : Installs the Application on a Device or Emulator.
* `Clean` : Clean the Project.

You can then select the `Project` and then the `Configuration` (`Debug` or `Release`) you want to `Build`.

To Debug goto the `Run` Tab and make sure `Debug` is selected. Click the Run button. You will be prompted on which project you wish to run, then asked which `TargetFramework` you want to target. For now only `net6.0-android` is supported. You will then be asked if you want to attach the debugger. Finally you will be asked which configuration you wish to use `Debug` or `Release`. After this the application should deploy and run, breakpoints should behave as normal.
