# ReactNative Installation (Windows)
Below instructions are adapted from https://dev-yakuza.posstree.com/en/react-native/install-on-windows/ and https://reactnative.dev/docs/environment-setup.
## Chocolatey
Chocolatey is a package manager on Windows to install and manage packages. We can install packages simply on Windows via Chocolatey.
You can install Chocolatey from: https://chocolatey.org/
Check choco version using the command: ```choco –version```

## Node, python2 and OpenJDK

react-native is a Javascript library and we need to install Nodejs, which is a Javascript runtime environment. Nodejs: https://nodejs.org/. On the other hand, OpenJDK is a library for running Java. This is necessary since we will eventually run our react-native code on android (a java based system).

* Open Windows powershell as an Administrator
* Execute the following chocolatey command to install Nodejs and OpenJDK: ```choco install -y nodejs.install openjdk11```
* You can check the version of node and npm using commands: ```node --version``` and ```npm -v```
* You can also install python2 using: ```choco install -y python2'''
* To check the list of installed choco software, use the command: ```choco list --local-only```. The output for this on my machine looks like the following: ```Chocolatey v1.0.0
chocolatey 1.0.0
nodejs-lts 16.18.0
openjdk11 11.0.16.20220913
python2 2.7.18
Temurin11 11.0.16.10100```
* Caution: You can uninstall any of the aforementioned programs using the command (e.g., for node): ```choco uninstall -y nodejs-lts```


## Android Studio Setup
We need to install Android Studio to develop Android app with react-native. Click the link below to go to Android Studio site and download the installation file.

* Android Studio: https://developer.android.com/studio.
* Download and install Android Studio. While on Android Studio installation wizard, make sure the boxes next to all of the following items are checked:
** Android SDK
** Android SDK Platform
** Android Virtual Device
** Hyper-V: Performance (Intel ® HAXM)

![image](https://user-images.githubusercontent.com/16555135/197799640-0076e4bf-2adc-4a36-ad2b-37f02964b79d.png)


* Open Android Studio, click on "More Actions" button and select "SDK Manager".
* Select the "SDK Platforms" tab from within the SDK Manager, then check the box next to "Show Package Details" in the bottom right corner.
* Look for and expand the Android 12 (S) entry, then make sure the following items are checked:
** Android SDK Platform 31
** Intel x86 Atom_64 System Image 
** Google APIs Intel x86 Atom System Image
* Next, select the "SDK Tools" tab and check the box next to "Show Package Details" here as well.
* Look for and expand the Android SDK Build-Tools entry, then make sure that 31.0.0 is selected.
* Finally, click "Apply" to download and install the Android SDK and related build tools.

### Configure the ANDROID_HOME environment variable

* Identify the path where Android SDK is installed. On your machine, it is likely that it will be installed in ```C:\Users\<Your_system_username>\AppData\Local\Android\Sdk```. First navigate through file browser and note down the path. Alternatively, you can alsofind the actual location of the SDK in the Android Studio "Settings" dialog, under Appearance & Behavior → System Settings → Android SDK.
* Open the Windows Control Panel.
* Click on User Accounts, then click User Accounts again
* Click on Change my environment variables
* Click on New... to create a new ANDROID_HOME user variable that points to the path to your Android SDK:
* ![image](https://user-images.githubusercontent.com/16555135/197795599-a6262e3d-17d6-47bc-a51a-a04f1d72ad24.png)

### Configure the PATH environment variable
This process is to add platform-tools to Path.
* Open the Windows Control Panel.
* Click on User Accounts, then click User Accounts again
* Click on Change my environment variables
* Select the Path variable.
* Click Edit.
* Click New and add the path to platform-tools to the list. 
* The default location for this folder is: ```C:\Users\<your_system_username>\AppData\Local\Android\Sdk\platform-tools```


### Creating a Virtual Device (Pixel 5)
* Open Android Studio.
* More Actions -> Virtual Device Manager
* Create Device -> Phone -> Pixel 5 -> Next.
* Select "S" (API Level 31) -> Next
* Show Advanced setting -> set SD Card (Studio Managed) to 2048 MB.
* Finish
* You can click on the play button to start the android emulator for Pixel 5 phone.

## Installing React Native

* First uninstall any stale versions on your PC. ```npm uninstall -g react-native-cli @react-native-community/cli```
* Install react native ```npx react-native init AwesomeProject```
* This will take a long time. Make sure that the final logs printed on the powershell say that the process was "successful". If it says that the process failed, contact the instructor.

## Testing React Native Sample App
* To test the sample application, use the command: ```npx react-native run-android```
* This will start a new emulator window of a google/android phone and start a basic react native app. You will know it when you see it! :)

# React Native (Running this Project)

## Server
Clone the repository into the docker container. Note that the docker container should have port 3000 open. Once you do that, navigate to ReactNativeServer folder. 
- ```npm install```
- ```systemctl start mongod```
- ```npm start``` (optionally, you can use ```screen npm start``` followed by ctrl+d to run the server in the background)

## Client
* Copy the files App.js and IssueList.js into the AwesomeProject folder. 
* You will be able to see the changes instantly on the Android emulator (if it was started already).
* You are good to start coding Tutorial 5!


# Final Submission
* Please update App.js, IssueList.js and package.json files (and any other required files) into the repository. TAs will copy and paste these files into their setup to evaluate your project.
* Final submission is your github classroom repository. So, please make sure you make the commits on time.
* Those new to git: Always remember, *add*, then *commit*, and then *push*
