Maps-Tutorial
=============

A tutorial on how to add Google Maps into an Android Application.

Setting up a Google Map inside your Android Application can be one of the most difficult things to do when creating
and Android app. There are VERY specific steps you must follow and missing even one step can cause problems.

Disclaimer: This tutorial is for Google Maps Android API v2 and works as of May 11, 2013. Updates to Google Maps Android
API or a creation of v3 can result in this guide becoming obsolete.

*******Part 1: Setting up your API Key***********
The first step is setting up your API Key through Google Developer. To do this, we must first get a piece of information known as the SHA-1 fingerprint. Note that there are two different keys: One for debugging and designing on your own device/computer & one for actually releasing into the Google Play Store.

1. Launch a Terminal Window (Mac OS X/Linux) or Command Prompt Window (Windows).
2. cd to your Java bin location:
  Windows: C:\Program Files\Java\jdk1.7.0_17\bin   (add (x86) if needed for 32-bit Java install on a 64-bit computer)
	Mac: cd to /usr/libexec/java_home then cd to bin

3. Type the following into the terminal/command prompt window:

Mac: keytool -list -v -keystore ~/.android/debug.keystore -alias androiddebugkey -storepass android -keypass android

Windows: keytool -list -v -keystore "C:\Users\your_user_name\.android\debug.keystore" -alias androiddebugkey -storepass android -keypass android

4. You should see output similar to this:
 Alias name: androiddebugkey
 Creation date: Jan 01, 2013
 Entry type: PrivateKeyEntry
 Certificate chain length: 1
 Certificate[1]:
 Owner: CN=Android Debug, O=Android, C=US
 Issuer: CN=Android Debug, O=Android, C=US
 Serial number: 4aa9b300
 Valid from: Mon Jan 01 08:04:04 UTC 2013 until: Mon Jan 01 18:04:04 PST 2033
 Certificate fingerprints:
      MD5:  AE:9F:95:D0:A6:86:89:BC:A8:70:BA:34:FF:6A:AC:F9
      SHA1: BB:0D:AC:74:D3:21:E1:43:07:71:9B:62:90:AF:A1:66:6E:44:5D:75
      Signature algorithm name: SHA1withRSA
      Version: 3

From this output, copy the line SHA1: (without the SHA1:) to the clipboard.

5. Go to this website: https://code.google.com/apis/console/ You will need a Google Account. Sign-in if needed.

6. On the left hand side, there will be a menu with the current project as it's name. From the menu, create a new project.

7. Click on Services (again, on the left). Scroll to Google Maps Android API v2. Switch this to the ON position.

8. Click on API Access (again, on the left).

9. Click Create new Android key....

10. Paste the SHA1 key you copied to the clipboard. THEN type a semicolon, followed by the package name of the project you plan to implement the project into.
10a. Note that if you are developing on muliple computers, you can put multiple SHA1 keys on multiple lines. Don' forget to add the package name to each one.

11. Click Create. An API key will appear. Copy it to the clipboard.

****Part 1a: Changing the API key for release******
Replace step 3 with the following:

keytool -list -v -keystore your_keystore_name -alias your_alias_name

If you need to find your alias name, type the following into a Terminal/Command Prompt window: keytool -list -keystore your_keystore_name. Replace your_keystone_name with the path & name of the keystore, including the .keystore extension.

********Part 2: Eclipse Setup**********
1. You MUST have the following Android SDK's installed:
-Under Tools: Android SDK Tools
-Under the API's you will be developing for: Google APIs
-Under Extras: Google Play Services
If you have issues, a troubleshooting tip I suggest is installing every single Android SDK.

2. Open Eclipse. If you are running Windows, Run Eclipse as an Administrator.

3. Go to File > Import.

4. Select Android > Exisiting Android Code Into Workspace. Then click Next.

5. Type this into the Root Directory: C:\Program Files (x86)\Android\android-sdk\extras\google\google_play_services (Note you may need to remove the (x86) if running a 32-bit system or if the Android SDK installed is 64-bit).

6. Under Projects to import, select libproject\google-play-services_lib.

7. Check the box "Copy projects into the workspace. Click Finish.

8. Now you should have the google-play-services_lib in your Project Explorer.

**********Part 3: Project Setup**********
1. Go to File > New > Other.

2. Select Android > Android Application Project.

3. Use the same package name you used in Part 1.

4. Where it says Complie With: select the Google APIs (Google, Inc.) that matches your Target SDK.

5. Adjust remaining setting as you so desire & finish the project setup.

6. Once the project is setup, right click (or Ctrl-Click) the project folder. Select Android Tools > Add Support Library.

7. Accept the license and install. If you get errors in the Android Console, make sure you are running Eclipse as an administrator.

8. Right click/Ctrl-click the project folder again and select Properties.

9. Under Android Properties, in the Library section, click the Add... button.

10. Select google-play-services_lib and click OK.

11. Click OK.


From here, the code is pretty much self-explanatory. Make sure to add your API key where it says "Your API Key Here" in the AndroidManifest.xml file.

If you experience difficulties, the first thing to check is the LogCat for authroization failures. If you get this, regenerate your API key using the steps in Part 1. Generated API keys are active almost instantaneously.

Final Disclaimer: Apps with maps rarely work in emulators and in 99.9% of cases must be tested on actual devices.
