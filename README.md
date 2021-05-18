# jenkins-pracs
Originally Jenkinspracs on private repo. 

Installing Jenkins Download the .war file from jenkins.io

Download and install latest Java version

Run the command below on the commandddd4 prompt

C:\Jenkins>java -jar jenkins.war Running from: C:\Jenkins\jenkins.war webroot: $user.home/.jenkins 2021-03-19 18:40:49.504+0000 [id=1] INFO org.eclipse.jetty.util.log.Log#initialized: Logging initialized @531ms to org.eclipse.jetty.util.log.JavaUtilLog

Jenkins initial setup is required. An admin user has been created and a password generated. Please use the following password to proceed to installation:

3d0f3120e4b449f8bdab525a0497

This may also be found at: C:\Users\oeume.jenkins\secrets\initialAdminPassword

Go to the bropwser and type in localhost:8080 enter the password above and continue

Install suggested plugins Create admin user and get started Configure Jenkins using the manage Jenkins tab

Download common tools Git, Nuget, Mavin and NUnit. First download chocolatey (package manager for windows 10) using powershell Set execution policy as follows

Windows PowerShell Copyright (C) Microsoft Corporation. All rights reserved.

Try the new cross-platform PowerShell https://aka.ms/pscore6

PS C:\Users\oeume> Get-ExecutionPolicy Restricted

PS C:\Users\oeume> Set-ExecutionPolicy AllSigned

Execution Policy Change The execution policy helps protect you from scripts that you do not trust. Changing the execution policy might expose you to the security risks described in the about_Execution_Policies help topic at https:/go.microsoft.com/fwlink/?LinkID=135170. Do you want to change the execution policy? [Y] Yes [A] Yes to All [N] No [L] No to All [S] Suspend [?] Help (default is "N"): A Set-ExecutionPolicy : Access to the registry key 'HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell' is denied. To change the execution policy for the default (LocalMachine) scope, start Windows PowerShell with the "Run as administrator" option. To change the execution policy for the current user, run "Set-ExecutionPolicy -Scope CurrentUser". At line:1 char:1

Set-ExecutionPolicy AllSigned

PS C:\Users\oeume> Set-ExecutionPolicy RemoteSigned

Execution Policy Change The execution policy helps protect you from scripts that you do not trust. Changing the execution policy might expose you to the security risks described in the about_Execution_Policies help topic at https:/go.microsoft.com/fwlink/?LinkID=135170. Do you want to change the execution policy? [Y] Yes [A] Yes to All [N] No [L] No to All [S] Suspend [?] Help (default is "N"): A Set-ExecutionPolicy : Access to the registry key 'HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell' is denied. To change the execution policy for the default (LocalMachine) scope, start Windows PowerShell with the "Run as administrator" option. To change the execution policy for the current user, run "Set-ExecutionPolicy -Scope CurrentUser". At line:1 char:1

Set-ExecutionPolicy RemoteSigned
  + CategoryInfo          : PermissionDenied: (:) [Set-ExecutionPolicy], UnauthorizedAccessException
  + FullyQualifiedErrorId : System.UnauthorizedAccessException,Microsoft.PowerShell.Commands.SetExecutionPolicyCommand

PS C:\Users\oeume> Get-ExecutionPolicy Restricted

PS C:\Users\oeume> Set-ExecutionPolicy Bypass -Scope Process

Execution Policy Change The execution policy helps protect you from scripts that you do not trust. Changing the execution policy might expose you to the security risks described in the about_Execution_Policies help topic at https:/go.microsoft.com/fwlink/?LinkID=135170. Do you want to change the execution policy? [Y] Yes [A] Yes to All [N] No [L] No to All [S] Suspend [?] Help (default is "N"): A

PS C:\Users\oeume> Get-ExecutionPolicy Bypass

Run the command below to install chocolatey

PS C:\WINDOWS\system32> Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1')) Forcing web requests to allow TLS v1.2 (Required for requests to Chocolatey.org) Getting latest version of the Chocolatey package for download. Not using proxy. Getting Chocolatey from https://chocolatey.org/api/v2/package/chocolatey/0.10.15. Downloading https://chocolatey.org/api/v2/package/chocolatey/0.10.15 to C:\Users\oeume\AppData\Local\Temp\chocolatey\chocoInstall\chocolatey.zip Not using proxy. Extracting C:\Users\oeume\AppData\Local\Temp\chocolatey\chocoInstall\chocolatey.zip to C:\Users\oeume\AppData\Local\Temp\chocolatey\chocoInstall Installing Chocolatey on the local machine Creating ChocolateyInstall as an environment variable (targeting 'Machine') Setting ChocolateyInstall to 'C:\ProgramData\chocolatey' WARNING: It's very likely you will need to close and reopen your shell before you can use choco. Restricting write permissions to Administrators We are setting up the Chocolatey package repository. The packages themselves go to 'C:\ProgramData\chocolatey\lib' (i.e. C:\ProgramData\chocolatey\lib\yourPackageName). A shim file for the command line goes to 'C:\ProgramData\chocolatey\bin' and points to an executable in 'C:\ProgramData\chocolatey\lib\yourPackageName'.

Creating Chocolatey folders if they do not already exist.

WARNING: You can safely ignore errors related to missing log files when upgrading from a version of Chocolatey less than 0.9.9. 'Batch file could not be found' is also safe to ignore. 'The system cannot find the file specified' - also safe. chocolatey.nupkg file not installed in lib. Attempting to locate it from bootstrapper. PATH environment variable does not have C:\ProgramData\chocolatey\bin in it. Adding... WARNING: Not setting tab completion: Profile file does not exist at 'C:\Users\oeume\Downloads\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1'. Chocolatey (choco.exe) is now ready. You can call choco from anywhere, command line or powershell by typing choco. Run choco /? for a list of functions. You may need to shut down and restart powershell and/or consoles first prior to using choco. Ensuring Chocolatey commands are on the path Ensuring chocolatey.nupkg is in the lib folder

PS C:\WINDOWS\system32>

PS C:\Users\oeume> You can use chocolatey to install Git, Nuget, Mavin amd NUnit.

Configure Git to work with Jenkins - since I have already installed Git. Go to Manage jenkins tab under Git secton and change the name to GitLocal also change the "path to Git executable section" to the correct location of Git on the machine

Also configure JDK already installed. Go to edit system environment variableby going to system properties/advanced/environment variables. Click on create new user variables....JAVA_HOME and search the path to add using browse button

Set environment variables for JDK

Also edit the system variables and point it to correctly using %JAVA_HOME%\bin.

Search for Maven on chocolatey and install using powershell as below

PS C:\WINDOWS\system32> choco install maven Chocolatey v0.10.15 Installing the following packages: maven By installing you accept licenses for the packages. Progress: Downloading maven 3.6.3... 100%

maven v3.6.3 [Approved] - Likely broken for FOSS users (due to download location changes) maven package files install completed. Performing other installation steps. The package maven wants to run 'chocolateyInstall.ps1'. Note: If you don't run this script, the installation will fail. Note: To confirm automatically next time, use '-y' or consider: choco feature enable -n allowGlobalConfirmation Do you want to run the script?([Y]es/[A]ll - yes to all/[N]o/[P]rint): y

Downloading Maven from 'https://archive.apache.org/dist/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.zip' Progress: 100% - Completed download of C:\Users\oeume\AppData\Local\Temp\chocolatey\maven\3.6.3\apache-maven-3.6.3-bin.zip (9.16 MB). Download of apache-maven-3.6.3-bin.zip (9.16 MB) completed. Hashes match. Extracting C:\Users\oeume\AppData\Local\Temp\chocolatey\maven\3.6.3\apache-maven-3.6.3-bin.zip to C:\ProgramData\chocolatey\lib\maven... C:\ProgramData\chocolatey\lib\maven C:\Users\oeume.m2 PATH environment variable does not have %M2_HOME%\bin in it. Adding... Environment Vars (like PATH) have changed. Close/reopen your shell to see the changes (or in powershell/cmd.exe just type refreshenv). The install of maven was successful. Software installed to 'C:\ProgramData\chocolatey\lib\maven'

Chocolatey installed 1/1 packages. See the log for details (C:\ProgramData\chocolatey\logs\chocolatey.log).

PS C:\WINDOWS\system32> refreshenv Refreshing environment variables from registry for cmd.exe. Please wait...Finished.. PS C:\WINDOWS\system32>

Refresh powershell to see changes in environment vairables

PS C:\WINDOWS\system32> refreshenv Refreshing environment variables from registry for cmd.exe. Please wait...Finished.. PS C:\WINDOWS\system32>

Forked executeautomation repository for sample code do not see a %M2_HOME%\bin in the user variable window as was supposed to be setup by chocolatey automatically but there is a C:\ProgramData\chocolatey\lib\maven\apache-maven-3.6.3 path setup under system variable.

I will try to run maven and see if it works.

Run Maven from the windows command prompt (cucumberbasic folder) as admin. Git bash also works.

C:\WINDOWS\system32>cd C:\Users\oeume\Desktop\GitPracs\cucumberbasic

C:\Users\oeume\Desktop\GitPracs\cucumberbasic>mvn [INFO] Scanning for projects... [INFO] ------------------------------------------------------------------------ [INFO] BUILD FAILURE [INFO] ------------------------------------------------------------------------ [INFO] Total time: 0.220 s [INFO] Finished at: 2021-03-20T05:28:39-04:00 [INFO] ------------------------------------------------------------------------ [ERROR] No goals have been specified for this build. You must specify a valid lifecycle phase or a goal in the format : or :[:]:. Available lifecycle phases are: validate, initialize, generate-sources, process-sources, generate-resources, process-resources, compile, process-classes, generate-test-sources, process-test-sources, generate-test-resources, process-test-resources, test-compile, process-test-classes, test, prepare-package, package, pre-integration-test, integration-test, post-integration-test, verify, install, deploy, pre-clean, clean, post-clean, pre-site, site, post-site, site-deploy. -> [Help 1] [ERROR] [ERROR] To see the full stack trace of the errors, re-run Maven with the -e switch. [ERROR] Re-run Maven using the -X switch to enable full debug logging. [ERROR] [ERROR] For more information about the errors and possible solutions, please read the following articles: [ERROR] [Help 1] http://cwiki.apache.org/confluence/display/MAVEN/NoGoalSpecifiedException

C:\Users\oeume\Desktop\GitPracs\cucumberbasic>

Run mvn clean to clean the project and most importantly download the required plugins that we need.

C:\Users\oeume\Desktop\GitPracs\cucumberbasic>mvn clean👍

[INFO] Scanning for projects... [INFO] [INFO] -----------------------< groupId:CucumberBasics >----------------------- [INFO] Building CucumberBasics 1.0-SNAPSHOT [INFO] --------------------------------[ jar ]--------------------------------- Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/plugins/maven-clean-plugin/2.5/maven-clean-plugin-2.5.pom

[INFO] ------------------------------------------------------------------------ [INFO] BUILD SUCCESS [INFO] ------------------------------------------------------------------------ [INFO] Total time: 4.141 s [INFO] Finished at: 2021-03-20T05:33:45-04:00 [INFO] ------------------------------------------------------------------------

C:\Users\oeume\Desktop\GitPracs\cucumberbasic>

C:\Users\oeume\Desktop\GitPracs\cucumberbasic>mvn compile👍 [INFO] Scanning for projects... [INFO] [INFO] -----------------------< groupId:CucumberBasics >----------------------- [INFO] Building CucumberBasics 1.0-SNAPSHOT [INFO] --------------------------------[ jar ]--------------------------------- [INFO] Changes detected - recompiling the module! [WARNING] File encoding has not been set, using platform encoding Cp1252, i.e. build is platform dependent! [INFO] Compiling 1 source file to C:\Users\oeume\Desktop\GitPracs\cucumberbasic\target\classes [INFO] ------------------------------------------------------------- [ERROR] COMPILATION ERROR : [INFO] ------------------------------------------------------------- [ERROR] No compiler is provided in this environment. Perhaps you are running on a JRE rather than a JDK? [INFO] 1 error [INFO] ------------------------------------------------------------- [INFO] ------------------------------------------------------------------------ [INFO] BUILD FAILURE [INFO] ------------------------------------------------------------------------ [INFO] Total time: 15.510 s [INFO] Finished at: 2021-03-20T05:45:59-04:00 [INFO] ------------------------------------------------------------------------ [ERROR] Failed to execute goal org.apache.maven.plugins:maven-compiler-plugin:3.1:compile (default-compile) on project CucumberBasics: Compilation failure [ERROR] No compiler is provided in this environment. Perhaps you are running on a JRE rather than a JDK? [ERROR] [ERROR] -> [Help 1] [ERROR] [ERROR] To see the full stack trace of the errors, re-run Maven with the -e switch. [ERROR] Re-run Maven using the -X switch to enable full debug logging. [ERROR] [ERROR] For more information about the errors and possible solutions, please read the following articles: [ERROR] [Help 1] http://cwiki.apache.org/confluence/display/MAVEN/MojoFailureException

C:\Users\oeume\Desktop\GitPracs\cucumberbasic>

Am still trying to figure out this error. https://stackoverflow.com/questions/26313902/maven-error-perhaps-you-are-running-on-a-jre-rather-than-a-jdk Used the search above as suggested to install Java jdk as below

PS C:\WINDOWS\system32> choco install jdk8👍 Chocolatey v0.10.15 Installing the following packages: jdk8 By installing you accept licenses for the packages. Progress: Downloading jdk8 8.0.211... 100%

jdk8 v8.0.211 [Approved] jdk8 package files install completed. Performing other installation steps. The package jdk8 wants to run 'chocolateyInstall.ps1'. Note: If you don't run this script, the installation will fail. Note: To confirm automatically next time, use '-y' or consider: choco feature enable -n allowGlobalConfirmation Do you want to run the script?([Y]es/[A]ll - yes to all/[N]o/[P]rint): y

Downloading JDK from https://javadl.oracle.com/webapps/download/GetFile/1.8.0_211-b12/478a62b7d4e34b78b671c754eaaf38ab/windows-i586/jdk-8u211-windows-x64.exe Installing jdk8... jdk8 has been installed. PATH environment variable does not have C:\Program Files\Java\jdk1.8.0_211\bin in it. Adding... jdk8 may be able to be automatically uninstalled. Environment Vars (like PATH) have changed. Close/reopen your shell to see the changes (or in powershell/cmd.exe just type refreshenv). The install of jdk8 was successful. Software installed to 'C:\Program Files\Java\jdk1.8.0_211'

Chocolatey installed 1/1 packages. See the log for details (C:\ProgramData\chocolatey\logs\chocolatey.log). PS C:\WINDOWS\system32> refreshenv Refreshing environment variables from registry for cmd.exe. Please wait...Finished.. PS C:\WINDOWS\system32>

Reinstall jdk The same issue. I had to shut down Jenkins and uninstall JDK since no chanes can actually take effect with jenkins still running off the previous java PS C:\WINDOWS\system32> choco install jdk8 Chocolatey v0.10.15 Installing the following packages: jdk8 By installing you accept licenses for the packages. jdk8 v8.0.211 already installed. Use --force to reinstall, specify a version to install, or try upgrade.

Chocolatey installed 0/1 packages. See the log for details (C:\ProgramData\chocolatey\logs\chocolatey.log).

Warnings:

jdk8 - jdk8 v8.0.211 already installed. Use --force to reinstall, specify a version to install, or try upgrade. PS C:\WINDOWS\system32> choco install jdk8 --force Chocolatey v0.10.15 Installing the following packages: jdk8 By installing you accept licenses for the packages. jdk8 v8.0.211 already installed. Forcing reinstall of version '8.0.211'. Please use upgrade if you meant to upgrade to a new version. Progress: Downloading jdk8 8.0.211... 100%
jdk8 v8.0.211 (forced) [Approved] jdk8 package files install completed. Performing other installation steps. The package jdk8 wants to run 'chocolateyInstall.ps1'. Note: If you don't run this script, the installation will fail. Note: To confirm automatically next time, use '-y' or consider: choco feature enable -n allowGlobalConfirmation

Run mvn clean and mvv compile again C:\Users\oeume\Desktop\GitPracs\cucumberbasic>mvn clean👍 [INFO] Scanning for projects... [INFO] [INFO] -----------------------< groupId:CucumberBasics >----------------------- [INFO] Building CucumberBasics 1.0-SNAPSHOT [INFO] --------------------------------[ jar ]--------------------------------- [INFO] [INFO] --- maven-clean-plugin:2.5:clean (default-clean) @ CucumberBasics --- [INFO] Deleting C:\Users\oeume\Desktop\GitPracs\cucumberbasic\target [INFO] ------------------------------------------------------------------------ [INFO] BUILD SUCCESS [INFO] ------------------------------------------------------------------------ [INFO] Total time: 0.429 s [INFO] Finished at: 2021-03-21T06:26:21-04:00 [INFO] ------------------------------------------------------------------------

C:\Users\oeume\Desktop\GitPracs\cucumberbasic>mvn compile👍 [INFO] Scanning for projects... [INFO] [INFO] -----------------------< groupId:CucumberBasics >----------------------- [INFO] Building CucumberBasics 1.0-SNAPSHOT [INFO] --------------------------------[ jar ]--------------------------------- [INFO] [INFO] --- maven-resources-plugin:2.6:resources (default-resources) @ CucumberBasics --- [WARNING] Using platform encoding (Cp1252 actually) to copy filtered resources, i.e. build is platform dependent! [INFO] skip non existing resourceDirectory C:\Users\oeume\Desktop\GitPracs\cucumberbasic\src\main\resources [INFO] [INFO] --- maven-compiler-plugin:3.1:compile (default-compile) @ CucumberBasics --- [INFO] Changes detected - recompiling the module! [WARNING] File encoding has not been set, using platform encoding Cp1252, i.e. build is platform dependent! [INFO] Compiling 1 source file to C:\Users\oeume\Desktop\GitPracs\cucumberbasic\target\classes [INFO] ------------------------------------------------------------------------ [INFO] BUILD SUCCESS [INFO] ------------------------------------------------------------------------ [INFO] Total time: 2.023 s [INFO] Finished at: 2021-03-21T06:26:30-04:00 [INFO] ------------------------------------------------------------------------

C:\Users\oeume\Desktop\GitPracs\cucumberbasic>

Build success. Quite easy

Creating free style project using Jenkins

From cloning git hub to manually compiling project... We first create a free style project Select source code by copying Git repository

When I pasted th source code link in the box provided on jenkins, the following error occurs Failed to connect to repository : Error performing git command: C:\Program Files\Git\bin ls-remote -h https://github.com/eoumenwa/cucumberbasic.git HEAD

Trouleshoooting guide below https://www.blazemeter.com/blog/how-to-integrate-your-github-repository-to-your-jenkins-project

Go to settings/webhooks and add a new webhook Copy Jenkins environment URl and paste under payload URL and add /github-webhook/

I had issues using localhost:8080 as my Jenkins environment URL for the webhook so I used the public IP address (http://73.152.119.181:8080) as suggested from the link (https://stackoverflow.com/questions/59208288/webhook-error-issue-while-integrating-github-with-jenkins)

This connection to the payload failed then I changed content type to application/x-www-form-urlencoded from application/json. No success

Using ngrok concept (https://github.com/jenkins-x/jx/issues/5633) 1.Download the https://ngrok.com/download server where it is running with Jenkins . 2../ngrok http 8080 ,it will give one http URL ..wait for some time ..some time taking 2 to 3 mins . 3.http://<......>ngrok.io eg http://3b2db437.ngrok.io 4.http://<...>/github-webhook/ eg http://3b2db437.ngrok.io/github-webhook/ .. ====>Don't give port 8080 as we already passed /ngrok http 8080 5.Final test the github webhook status .

Result of /ngrok http 8080

ngrok by @inconshreveable

Session Status online

Session Expires 1 hour, 59 minutes

Version 2.3.35

Region United States (us)

Web Interface http://127.0.0.1:4040

Forwarding http://48ea7e299e92.ngrok.io -> http://localhost:80

Forwarding https://48ea7e299e92.ngrok.io -> http://localhost:80 Connections ttl opn rt1 rt5 p50 p90 0 0 0.00 0.00 0.00 0.00

Updated the github webhook URL as follows............. http://48ea7e299e92.ngrok.io/github-webhook

This did not still work.

Next step suggested by (https://stackoverflow.com/questions/26620312/git-installing-git-in-path-with-github-client-for-windows is to add Git path to system variables. As 

follows. C:\Program Files\Git\bin\git.exe;C:\Program Files\Git\cmd Now running git --version on cmd shows me the version which was never the case. Restarted cmd prompt. Shut 

down Jenkins server as well.

Going back to line 399 to try http://73.152.119.181:8080/.........Tried and no success Reverting to ngrok https://9d332411bf34.ngrok.io/github-webhook/

This issue will be kept in view. ngrok timed out already.

Here is what worked https://20c9de6c131c.ngrok.io/github-webhook/ I was running ngrok http 80 instead of 8080. Although this is a temporary pass, am happy to move on.....

Am still getting the erro message below on Jenkins

Failed to connect to repository : Error performing git command: C:\Program Files\Git\cmd ls-remote -h https://github.com/eoumenwa/cucumberbasic.git HEAD

Maybe I need to reinstall git using chocolatey just like I did with Java. Seems whatever was not installed with chocolatey would not work since I had installed both Java and 

Git before now. Though the Java is comfortably running Jenkins..........just wondering

Gained insight into creating pipeline project to build and test using cucumber as well as reporting with and without stages. Staging concept is worthy of note giving a 

snapshot of activity timeline. Also understood how to change commands to pipeline scripts in Jenkins Ruby basics.

Performed a reboot after a while. Attempting to run choco install git on powershell to see if things will fly.
