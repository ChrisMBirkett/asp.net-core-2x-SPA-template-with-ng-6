# ASP.NET CORE 2.x + Angular 6.x CLI SPA

This project is a basic look at making the ASP.NET CORE 2.x Angular template function with Angular 6x and Angular CLI 6x. 
It is part of my efforts to research and learn to use the new tools, and also be able to share my experiences with my teammates. 

This is the vanilla template app at this time and only serves to demonstrate that Angular CLI v6 could be used to update the SPA and that the 
Angular 6 app and a DotNet Core 2.x SPA could run within the same application.

# Source Control

Installed Git and the Git GUI to create this repo and push the project into source control.

# Running the SPA

The simplest way to run this project to see that it works is to open it in VS2017 Community Edition (for example) and run IIS Express.

To run it from VSCode, open the Terminal and execute the following commands:

1. dotnet restore
2. npm install (located in the ClientApp folder)
3. dotnet build (make sure you return to the root of the project directory after the previous step)
4. dotnet run

Look for the line that looks like to following to know which URL to open in a browser to see the working site:

** Angular Live Development Server is listening on localhost:52013, open your browser on http://localhost:52013/ **

# Steps Taken to Get this Template App Upgraded to Angular 6

The template project uses Angular 4.3.x and Angular CLI 1.7.x. I had to take the following steps to upgrade it.

1. Installed Angular CLI globally: npm install -g @angular/cli
2. Opened a command prompt at the root of the ng-cli app; in this case, ClientApp
3. Run the following command to upgrade ng-cli to the latest 6x version: `npm install --save-dev @angular/cli@^6.0.0;
4. ng update [This shows what packages need to be upgraded]
5. In my case, I had to run the following
   * ng update @angular/cli
   * ng update @angular/core

## Editing of the *.CSPROJ File

In VSCode, click on the CSPROJ file. In Visual Studio 2017, right-click the project root to edit the CSPROJ file.

I reviewed the following looking for ng-cli related commands that could be preventing the build from succeeding (dotnot build):

`<Target Name="PublishRunWebpack" AfterTargets="ComputeFilesToPublish">`

I didn't see any issues with the commands being issued from that section of the CSPROJ file.

I then opened up the package.json file located under the ClientApp folder. Under the `"scripts"` section, I reviewed the commands and removed any usage of `--extract-Css`.

Once I was done with that minor change, I was able to build then run the app:

1. dotnet build
2. dotnet run 