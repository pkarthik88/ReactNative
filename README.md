Below, you can find the installation instructions for Windows and MacOS (To be updated soon).

# ReactNative Installation (Windows)
Below instructions are adapted from https://dev-yakuza.posstree.com/en/react-native/install-on-windows/ and https://reactnative.dev/docs/environment-setup.
## Chocolatey
Chocolatey is a package manager on Windows to install and manage packages. We can install packages simply on Windows via Chocolatey.

* You can install Chocolatey from: https://chocolatey.org/install 
* Follow the instructions under **Install Chocolatey for Individual Use**.
* Check choco version using the command: ```choco –version```
* The recommended version is chocolatey v1.3.1.

## Node, python2 and OpenJDK

react-native is a Javascript library that we will be using for coding the react native client, intended to be executed on the mobile device. For this, we need to install Nodejs, which is a Javascript runtime environment on our development laptop. Python2 is required by the Metro server that helps us install the compiled app code on the physical/emulated android device. Additionally, you need to install OpenJDK (library for compiling the Java code) that will eventually be installed on the Android device.

* Open Windows powershell as an Administrator
* Execute the following chocolatey command to install Nodejs and OpenJDK: ```choco install -y nodejs-lts microsoft-openjdk11```
* You can check the version of node and npm using commands: ```node --version``` and ```npm -v```
* You can also install python2 using: ```choco install -y python2'''
* To check the list of installed choco software, use the command: ```choco list --local-only```. The output for this on my machine looks like the following: ```
chocolatey  1.3.1
nodejs-lts 18.15.0
microsoft-openjdk11 11.0.18
python2 2.7.18```

* Set the JAVA_HOME Environment Variable. In my machine, I set JAVA_HOME as ```C:\Program Files\Microsoft\jdk-11.0.18.10-hotspot```
* Caution: You can uninstall any of the aforementioned programs using the command (e.g., for node): ```choco uninstall -y nodejs-lts``` if you find the need to uninstall later.


## Android Studio Setup
We need to install Android Studio for getting access to the tools required to install on Android physical device, and additionally, to get access to the android emulator. Click the link below to go to Android Studio site and download the installation file.

* Android Studio: https://developer.android.com/studio. 
* Download and install Android Studio. While on Android Studio installation wizard, make sure the boxes next to all of the following items are checked:
* IF the installation asks for elevated permission to run the program **adb**, you can give this permission. 


### Android SDK Tools
* Open Android Studio, click on "Tools" tab and select "SDK Manager".
* In SDK Manager, select the "Android SDK" tab under *System Settings*, then check the box named "Show Package Details" in the bottom right corner.
* Look for and expand the Android 13 entry, then make sure the following items as seen in the image below are checked within this:
![image](https://user-images.githubusercontent.com/16555135/228753652-f80e362b-55e8-4417-9cea-51b81b397e05.png)
* Finally, click "Apply" to download and install the Android SDK tools.
* The download size is approximately 1.5 GB. Make sure you are connected to a Wi-Fi connection with adequate data plan.

### Android Build tools
* Again, go to the "SDK Manager" window -> select "Android SDK" under *System Settings*.
* Next, select the "SDK Tools" tab from the navigation bar at the top and check the box next to "Show Package Details" here as well.
* Look for and expand the Android SDK Build-Tools entry, then make sure that 33.0.0 is selected. You can unselect the others if you want.
* Also make sure that ```Intel x86 Emulator Accelerator (HAXM installer)``` is selected.

![image](https://user-images.githubusercontent.com/16555135/228755900-312591db-8076-497d-84dd-181c23d022c5.png)


* Finally, click "Apply" to download and install the Android SDK and related build tools.
* This download takes about 188MB of space.



### Configure the ANDROID_HOME environment variable

* Identify the path where Android SDK is installed. You can find the actual location of the SDK in the Android Studio "Settings" dialog, under Appearance & Behavior → System Settings → Android SDK. Look for the textbox that shows the path. For example, on my machine, it shows something like ```C:\Users\dcspkv\AppData\Local\Android\Sdk```. Copy this path and save it somewhere.
* Open the Windows Control Panel.
* Click on User Accounts, then click User Accounts again
* Click on Change my environment variables
* Click on New... to create a new ANDROID_HOME user variable that points to the path that you copied earlier:
* ![image](https://user-images.githubusercontent.com/16555135/197795599-a6262e3d-17d6-47bc-a51a-a04f1d72ad24.png)

### Configure the PATH environment variable
This process is to add platform-tools to Path.
* This path is the same path that you copied in previous step, but appended with platform-tools. For example, in my machine, it is ```C:\Users\dcspkv\AppData\Local\Android\Sdk\platform-tools```
* Open the Windows Control Panel.
* Click on User Accounts, then click User Accounts again
* Click on Change my environment variables
* Select the Path variable.
* Click Edit.
* Click New and add the path to platform-tools to the list.


### Creating a Virtual Device (Pixel 5)
* Open Android Studio and look for the top navigation bar.
* Tools -> Device Manager
* Create Device -> Phone -> Pixel 6 -> Next.
* Select "Tiramisu" (API Level 33) -> Next
* Show Advanced setting -> set SD Card (Studio Managed) to 2048 MB.
* Finish
* You can click on the play button to start the android emulator for Pixel 6 phone.

## Installing React Native
* Open a new Powershell Terminal in normal mode (not administrator mode).
* First uninstall any stale versions on your PC. ```npm uninstall -g react-native-cli @react-native-community/cli```
* Install react native ```npx react-native@latest init AwesomeProject```
* This command will automatically install React Native version 0.71.5 (Latest at the time of writing this document)
* This will take a long time. Make sure that the final logs printed on the powershell say that the process was "successful". If it says that the process failed, contact the instructor.

## Testing React Native Sample App
* Move into the newly created App folder: ```cd AwesomeProject```.
* To test the sample application, use the command: ```npx react-native run-android```. Alternatively, you can also run ```npm run android```.
* This will start a new emulator window of a google/android phone and start a basic react native app. You will know it when you see it! :)cd 

![image](https://user-images.githubusercontent.com/16555135/228783852-27fefb82-bb41-4548-ae79-b5de9f649772.png)


# React Native (Running this Project)

## Server
Clone the repository into the docker container. Note that the docker container should have port 3000 open. Once you do that, navigate to ReactNativeServer folder. 
- ```npm install```
- ```systemctl start mongod```
- ```npm start``` (optionally, you can use ```screen npm start``` followed by ctrl+d to run the server in the background)

## Client
* No need to clone this repository.
* Copy the files App.js and IssueList.js into the AwesomeProject folder. 
* You will be able to see the changes instantly on the Android emulator (if it was started already).
* You are good to start coding Assignment 5!
