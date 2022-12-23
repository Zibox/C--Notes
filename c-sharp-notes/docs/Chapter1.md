# Dot Net Versioning

## .NET Framework

.NET Framekwork is a dev platform that includes a CLR (Common Language Runtime), which manages the execution of code, and BCL (Base Class Library), used to build apps from. Since v4.5.2 it's been an official component of the OS.

For .NET Framework 4.0 and beyond, all apps written for a .NET Framework sahre the same version of the CLR and libraries stored in the GAC (Global Assembly Cache), which can potentially lead to version hell. Best practice, don't write apps in .NET Framework.

## .NET Core (aka .NET)

Cross platform .NET, CLR is now known as CoreCLR and BCL is CoreFX. 6 and neyond has proper mobile support.

### Seeing which versions of .NET are installed

1. dotnet --list-sdks
2. dotnet --list-runtimes
3. dotnet --info
