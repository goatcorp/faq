# XIVLauncher Authenticator App

You can use an app together with XIVLauncher to automatically log yourself in without needing to type the OTP code manually. The app will send the code over your local network to XIVLauncher, which will use it to log you in.

## Setup

### Installation

You can download the newest version of the app from the [app releases page](https://github.com/goaaats/xl-authenticator/releases/latest). You can also find the source code on the linked repository.

#### Installing on Android

Download the APK file from the linked releases page and open it. You will be prompted to allow Chrome/your browser to install applications from unknown sources. After allowing this installation, you will be able to find the app on your regular app drawer.

#### Installing on iOS

Since we can't publish the app on the App Store, you will have to use an alternative store like [AltStore](https://altstore.io/) to install the app. You can also use a Jailbroken device with AppSync Unified from [Karen's repo](https://cydia.akemi.ai/?page/net.angelxwind.appsyncunified).

### Registering the app

To use the app as an OTP Token, you have to register it with your Square Enix account.

You can do so on the [Mog Station](https://secure.square-enix.com/account/app/svc/mogstation) by choosing "Manage Square Enix Account" and then clicking the "One Time Password" option in the title bar.

On the resulting page, you can then choose "Other authenticator apps (Google Authenticator, etc.)". You will see a QR code.

Open the XL Authenticator App and tap "Set-Up OTP code". Scan the provided QR code. After scanning, your SE account username should be listed on the settings page.

If you cannot scan the code due to your camera not working, you can also tap "Enter by hand" and type the code manually. Mind that in this case, your username will not be shown.

**Note:** We recommend scanning the code with another Authenticator app like Authy at the same time, so you have two apps that can generate codes in case one is lost. Please also remember writing down your fallback code in a secure location.

### Entering the XIVLauncher IP

To connect the app to your PC, you first need to find your PC's **local** IP address. To do this, we recommend this [high-quality article by American lifestyle online media-outlet "Lifehacker"](https://lifehacker.com/how-to-find-your-local-and-external-ip-address-5833108).

On the XL Authenticator app settings page, tap "Set XIVLauncher IP" and enter the IP address you determined earlier.

### Enabling the OTP app feature in XIVLauncher

In XIVLauncher, click the settings "gear" icon on the main screen. If you have Auto-Login enabled, you will have to hold shift while starting to get back to the XIVLauncher main screen.

On the following screen, make sure "Enable XL Authenticator app/OTP macro support" is ticked.

NOTE: If you're on the stable build of XIVLauncher 5.5.3 or prior, you won't see this setting because it's always on.

![Make sure to tick this box](https://goatcorp.github.io/faq/asset/otp_checkbox.png)

---

Congratulations! From now on, when XIVLauncher is waiting for you to enter an OTP code, you will be able to just open the app and log yourself in automatically.

## OTP Macros

If you don't want to use the app, you can also use macros on iOS and via MacroDroid on Android.

On the OTP input screen, it's possible to log in automatically by accessing the URL below with the IP of your computer and the OTP you want to use with your account:

`http://[Your PC Address]:4646/ffxivlauncher/[one-time password]`

You can usually find your computer's address through `cmd.exe` by entering the command `ipconfig`.

```text
Ethernet adapter Gigabit Ethernet:

   Connection-specific DNS Suffix  . :
   Link-local IPv6 Address . . . . . : 5ea9:b5a8:77aa:e9a:56e0:1057:8245:a4db
   IPv4 Address. . . . . . . . . . . : 10.0.0.39 <----- We want this
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 10.0.0.1
```

Copy the `IPv4 Address` to the OTP macro.

## Initial settings

When launching your game with OTP, make sure to allow XIVLauncher to communicate past your Windows firewall.

## Phone settings

### iOS

This method has only been tested on iOS 13.1+, it may not work on earlier firmware versions.

- Install the [Shortcuts app](https://apps.apple.com/us/app/%E3%82%B7%E3%83%A7%E3%83%BC%E3%83%88%E3%82%AB%E3%83%83%E3%83%88/id915249334 "Shortcuts app") on an iOS device.
- Allow untrusted shortcuts in your Shortcuts settings in the Settings app.

<img src="https://i.imgur.com/cySnPjr.png" width="280">
<img src="https://i.imgur.com/xg6gig4.png" width="280">

- Open the [FFXIV Login shortcut](https://www.icloud.com/shortcuts/6b4a512582e24e2baeaa08e771c9b998 "FFXIV Login shortcut") in Safari and tap "Get Shortcut".
  - If you open in Chrome or Firefox, you can not open in the Shortcuts app.
- Review the Shortcut and Add it to your shortcut list.

<img src="https://raw.githubusercontent.com/goaaats/FFXIVQuickLauncher/master/images/ios_add_shortcut1.png" width="280">
<img src="https://raw.githubusercontent.com/goaaats/FFXIVQuickLauncher/master/images/ios_add_shortcut2.png" width="280">

- Rewrite the part set as "0.0.0.0" of "Replace With" with your PC's IP address or PC name.

<img src="https://goatcorp.github.io/faq/asset/ios_edit_shortcut1.png" width="280">
<img src="https://goatcorp.github.io/faq/asset/ios_edit_shortcut2.png" width="280">

- Add the Shortcut to your Share Sheet.

<img src="https://i.imgur.com/2FkQBFw.png" width="280">

- Tap "Done".

#### How to Use

- Start XIVLauncher on your PC and start the login process, either by clicking login or by autologin.
- Open the "Square Enix Software Token" app.
- Long tap on the one-time password part and select "Share".

<img src="https://goatcorp.github.io/faq/asset/howtouse_image_ios1_en.png" width="280">

- Select "FFXIV Login".

<img src="https://i.imgur.com/RgGi9yS.jpg" width="280">

### Android (Versions before 10)

> WARNING!!!! THIS MACRO ONLY WORKS WITH ANDROID VERSIONS BEFORE 10!
>
> THIS IS DUE TO A PERMISSION CHANGE WHERE APPS ARE NOT ALLOWED ACCESS TO THE CLIPBOARD!

1. Install the [MacroDroid](https://play.google.com/store/apps/details?id=com.arlosoft.macrodroid) app
2. Hide all notifications for MacroDroid in your Android system settings(optional, but recommended)
3. Open MacroDroid, follow the initial setup
4. Tap "Templates" and "browse"
5. Tap the looking glass and search for "ffxiv"
6. Add the macro called "FFXIV OTP" by "goat" and replace the IP in the "HTTP GET" action with the IP of your computer
7. Go back to the main screen, tap Macros, hold the "FFXIV OTP" macro and select "Create home screen shortcut"

### Android (Versions after 10)

Due to the changes to Android not providing access to the clipboard for background apps, you can make a slight modification to the Macro to open up MacroDroid before sending your OTP to the launcher (Thanks Catalysta#8888!)

Update the macro as such:

<img src="https://cdn.discordapp.com/attachments/581875020632948762/660532896737787906/SmartSelect_20191228-112146_MacroDroid.jpg" width=280>

#### How to use

1. Start XIVLauncher on your PC and start the login process, either by clicking login or by autologin.
2. Tap the home screen shortcut you made for the macro
3. Wait for "Square Enix Software Token" app to automatically open and for the macro to be sent
