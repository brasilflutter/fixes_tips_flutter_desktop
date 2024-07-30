# How to Configure Inno Setup to Create an Installer for Flutter Applications on Windows


* To create an installer for a Flutter application on Windows, you can use Inno Setup, a popular tool for creating installers on Windows. Inno Setup helps you package and distribute your application in a  professional manner. Below is a step-by-step guide to configure Inno Setup and create an installer for your Flutter build.

* Prerequisites
  Inno Setup Installed: Download and install Inno Setup from the official website.

[Link](https://jrsoftware.org/isdl.php#stable)

* Steps to Create the Installer
  Prepare to Build the Flutter Application

* First, you need to generate the build folder for your Flutter application. Open the terminal and navigate to your Flutter project directory, then run the command:
  - flutter build windows --release
  This will create a build\windows\runner\Release directory that contains your application executable and all necessary files.

* Create an Inno Setup Script
  Inno Setup uses .iss scripts to define how the installer should be configured. Open Inno Setup and create a new script. You can use the wizard to generate a basic script and then customize it.
  Below is a basic example Inno Setup script for a Flutter application:
  
```
  [Setup]
  AppName=ProjectName
  AppVersion=1.0
  DefaultDirName={pf}\ProjectName
  DefaultGroupName=ProjectName
  OutputDir=output
  OutputBaseFilename=ProjectName
  Compression=lzma
  SolidCompression=yes
  
  [Files]
  Source: "PATH-PROJECT\build\windows\x64\runner\Release\*"; DestDir: "{app}"; Flags: ignoreversion recursesubdirs createallsubdirs
  
  [Icons]
  Name: "{group}\ProjectName"; Filename: "{app}\ProjectName.exe"
  Name: "{group}\Uninstall ProjectName"; Filename: "{uninstallexe}"

  [Run]
  Filename: "{app}\MinhaAplicacao.exe"; Description: "{cm:LaunchProgram,MinhaAplicacao}"; Flags: nowait postinstall skipifsilent
```

# Explanation of the main blocks:

  [Setup]: Defines the basic settings of the installer, such as application name, version and default directory.
  [Files]: Specifies the files that will be included in the installer and their destinations.
  [Icons]: Creates shortcuts in the Start menu and on the desktop.
  [Run]: Defines what should be executed after installation, such as starting the application.

* Compile the Script
  After creating and saving the .iss script, click "Compile" in Inno Setup to generate the installer. Inno Setup will create an .exe file in the specified directory (OutputDir) that can be distributed and  used to install your application.

* Test the Installer
  Run the generated installer in a test environment to ensure that everything works as expected. Verify that the application installs correctly and that all files and shortcuts are created as specified.

* Distribute the Installer
  After testing and confirming that the installer works correctly, you can distribute the .exe file to end users. They will be able to install your application easily using the created installer.

* Additional Tips
  Documentation: Refer to the official Inno Setup documentation for more details and advanced options.
  Customization: You can further customize the installer by adding custom installation screens, languages, and more.