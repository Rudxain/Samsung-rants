# About

> WARNING: This contains slurs/swear-words

## Intro

I was already bored/tired of using Samsung products (specially phones), but now I'm at my **absolute limit.**

## Backstory

All started when I was using my Galaxy J3 Mission, tinkering around, looking at the "Running processes" section of the dev settings.
Then, I notice that the launcher (Samsung Experience Home) was running **all the time** since the device was turned on (it matched "Up Time").
The culprit was the "notification listener service", which I couldn't turn off because it was **hidden from the "Notification Access" list.**
This was very annoying, because it constantly consumed RAM for no reason.

## Present

I was gifted a Galaxy A31, I was disappointed I got yet another Samsung phone (before the J3, I had a Sony Xperia Z5, and before that I got a Galaxy S4).
But I was very happy that I could finally use Android 12, and even happier because I finally have an **unlockable bootloader!**
(I was so unlucky that the Z5 was hard-locked, not even the official Sony codes helped me. The J3 was "even-harder-locked" because of Verizon's fault)

I was doing the same monitoring+tinkering process... when suddenly... **the Game Launcher was running** for no reason. I went to the details, and guess what...
**IT'S THE FUCKING NOTIFICATION LISTENER AGAIN! AND IT'S ALSO HIDDEN FROM THE NOTIFICATION ACCESS LIST!!!**

At least, I can disable the app, but that's still unnecessary (why do I have to completely disable an app just to get rid of 1 listener?)

## Other stuff I hate

### SMS history
For some reason, Samsung thought it's a good idea to log SMSs in the Phone app, **even if "Show messages" is disabled.**
So if you want to save storage, or increase your privacy, you're forced to enable "Show messages" to delete them (or block the SMS permission of the Phone app)
This is even worse when the vast majority of messages are useless carrier ads and reminders, now you're forced to delete those messages **ON BOTH APPS**.

This annoyance got even worse when they added the "Trash" feature to all their apps. Now you gotta delete it thrice!!! (unless you disable the Trash)

They haven't improved this, for years.

### My Files
Speaking of logging, "My Files" logs recently used files **even if the list is hidden**, meaning you also have to remember to clear it.

It also shows hidden files in the "storage analyzer", despite disabling the "show hidden files" option.

It says "MB" but it actually is "MiB", which is misleading. I noticed this because the AOSP Files really uses MB units.

### Persistent clipboard

I installed Gboard, used it for some time, cleared its 📋CB history, uninstalled it, and noticed S Keyboard **still has the old CB entries**.

This is a massive **privacy vulnerability!**
Imagine you thought you deleted all passwords from a 3rd-party CB, only to get hacked by someone who took your phone and enabled S Keyboard as the default keyboard.

They haven't fixed this for years! The J3 Mission has the exact same problem.

I don't think this is an "Android limitation", the system can easily detect when a different keyboard is being used, and avoid logging on the native CB.

### Automatic dictionary

S Keyboard automatically adds words to its dictionary, **all the time**, unlike Gboard, which doesn't collect data when using Chrome-incognito (perhaps S Keyboard does something similar with S Internet? IDK).

This means you have to clear **ALL PERSONALIZATION DATA**, everytime you use Incognito.

Gboard has a dedicated menu to manage the dictionary.

Again, unsurprisingly, they haven't improved this for years. Come on, S, is it really that hard?

### Legacy Google dependency

[Another one](https://youtu.be/jEI3N9kIyP4), about the keyboard (3 strikes!!!).

You know that microphone button that converts speech to text? Turns out, it _depends on the Google app, not G Speech Services._

Since I uninstalled G, I realized the difference between "Voice Typing" and "Voice Typing \[Legacy]", in the input settings. "Legacy" means "Google app".

Now, everytime I want to use voice input, I have to open the notification panel, and select "Google Voice Typing" (provided by Speech Services).

It seems I had to `clear`-data to force the keyboard to use the new API. This is unacceptable UX

### Split-Screen depends on Apps-Edge
[See this UAD issue](https://github.com/0x192/universal-android-debloater/issues/124)

### Useless account
S forces users to use a Samsung Account, even for *looking at the list of app updates in Galaxy Store.*
So if you want to control auto-updates for individual apps, you gotta login to a useless S Account! Amazing, isn't it?! /s

That is just the tip of the iceberg, S forces you to use that account for lots of other unnecessary things!

### Bloatware
S has an obsession with making and pre-installing apps that Google already made.
As a minimalist person, this is absolutely disgusting:

- "So you like Google Assistant? How about you use Bixby instead?"
- "You still use G lens? How about you use Bixby Vision?"
- "G Tasks doesn't exist! Use Reminder!"
- "Don't use Google Autofill! Use S Pass"
- "Chrome is so 2016, use S Internet"
- "Gmail sucks, use S Mail"
- "BTW, look at these not-sponsored-at-all suite of Facebook, Microsoft, Intel, McAfee, Clean Master, and Grammarly software!"

Ok Samsung, how about you stop leeching off of Android, and make your own motherfucking operating system? (just like Huawei).
Oh wait, [they did](https://arstechnica.com/gadgets/2015/02/samsung-z1-review-the-first-tizen-smartphone-still-feels-like-plan-b)

### GOS

I thought "Game Optimizing Service" was mostly useless, until I learned [it's actually counterproductive](https://pcgamer.com/samsungs-game-optimization-service-might-be-throttling-the-performance-of-over-10000-apps).

It can't be disabled on SM-A315G, **not even with ADB**

### Deep-Sleeping apps are "disabled"

[See this Reddit thread](https://reddit.com/r/AndroidQuestions/comments/149lfg3/why_batteryrestricted_apps_are_considered_disabled)

# No-sleep-app = never-sleep
Removing an app from the "sleeping apps" list automatically adds it to "never sleeping".

This is inconvenient, to say the least.

### Can't clear disabled apps

Despite the fact that AOSP and ADB allow you to clear app data after it's been disabled, Galaxy devices don't allow you to do so, for some reason.

You can only clear cache!

### Cache is calculated twice

Speaking of app data, if you go to Settings -> Apps, and clear the cache of any app, you'll notice that "Data" is decremented. This is technically true, because cache is kinda part of data. This wouldn't be a bug, if it wasn't for the fact that **"Total" is the sum of code, data, and cache.** This means "Total" is adding "Cache" twice!

I had to make an Automate-flow to check the ACTUAL size of installed apps, because of this bug.

**This bug still exists since Android 5** (Galaxy S4)

### Blue Light Filter

When I was looking at hidden app activities in my J3 Mission, I noticed S made its own "BLF" independent of AOSP's "Night Light",
but it was no-op, so I had to resort to the AOSP version (which was also hidden from Settings, for some reason).

Everytime I wanted to toggle NL, I had to use an Automate-flow that changed the setting. And if I wanted to configure the color temperature or schedule, I had to use Automate to open the hidden activity.

They literally updated my device from Android 7 to 8, and decided to hide a well-behaved fully-functional feature, just because they were working on a clone that doesn't even work on the lock-screen (while fingerprint scanner is active)...

Thank you, Samsung, for being so annoying!

### Linear brightness

Android 9P introduced a logarithmic brightness slider. I'm using Android 12, and **IT'S STILL LINEAR**. TBF, this may be a hardware limitation, because OLED is usually driven by PWM. **BUT THERE IS NO EXCUSE**, they can literally fix this on the software side!

How come I didn't notice this flaw?! I've been using this phone for months! (brightness 0, that's why. I'm a vampire)

### Sunlight mode

[Adaptive brightness will force the screen **brightness to MAXIMUM VALUE**](https://forum.xda-developers.com/t/adaptive-brightness-disable-maximized-sunlight-mode.4493467), if it thinks there's "too much ambient light". The lux threshold is hardcoded, it's the same regardless of training data.

This forces me to disable AB temporarily, just to lower the brightness.

This is not "adaptive" at all.

### Lockscreen post-processing

Regardless of brightness, the lockscreen has a severely reduced bit-depth. So much that it causes big banding artifacts in wallpapers.
[This only happens while fingerprint unlock is active](https://r2.community.samsung.com/t5/Galaxy-A/A51-lockscreen-display-color-issue/m-p/4218019/highlight/true#M203235). It seems this is a hardware limitation.

The wallpaper is cropped and rotated when the device is rotated, but the home wallpaper stays the same.

IDK if these are Android things, but I'm pretty sure it's Samsung's fault. I've never seen an Android have that inconsistency.

### Bad Lock

What's the point of "Lock instantly with Side-Key" if "insta-lock when screen turns off" also applies to the side key itself?! It should only lock after screen-timeout expires.

What's the point of turning off the screen via double-tap if it's getting locked anyways??!!! (Not to mention the obvious lie of "Side Key").

Almost all S devices have this UX problem: If you want to lock the device, you must wait for a timeout, or turn-off the screen. If you only want to turn-off the screen, **you must wait for a timeout**.

The only alternative is "Lockdown mode", which is equivalent to signing-out of the OS-user-account, which in turn disables all app notifications and WhatsApp calls.

I had to make a /Llamalab/Automate flow to manually lock the device. A **basic** piece of functionality.

### DTMF stuttering
[See this G Groups thread](https://groups.google.com/g/automate-user/c/22iukdGJm10/m/j-6VKTlAAAAJ)

### Invalid MMI codes

I've never seen a Galaxy device properly respond to an MMI code.

You know, those numbers and symbols you have to dial in the Phone app to open hidden settings? [That's forbidden](https://tenor.com/view/we-dont-do-that-here-black-panther-tchalla-bruce-gif-16558003)

None of the AOSP codes, nor OEM-specific (Samsung), work. It doesn't matter if the device is old or new (from Galaxy J3 to A31)

The only ones that worked so far are:
- "USB Settings": `*#0808#`
- `HwModuleTest`: \*#0\*#

### RIP SUIT
[No System UI Tuner?!](https://wompampsupport.azureedge.net/fetchimage?siteId=7575&v=2&jpgQuality=100&width=700&url=https%3A%2F%2Fi.kym-cdn.com%2Fphotos%2Fimages%2Fnewsfeed%2F002%2F297%2F368%2F17f.jpg)

### Cannot share via WiFi Direct

Since One UI 3.1 released, the option to send data via Wi-Fi Direct has been hidden (perhaps even completely removed).

S recommends Google's Nearby Share as an alternative.

Now I'm forced to use the slow Bluetooth, when Nearby Share decides the devices aren't compatible with WFD. Another option is LAN sharing, but this requires a centralized router to act as bridge

### Unintuitive screen capture

There are 4 ways to capture the screen:

- Tasks Edge: Allocates more RAM, and constantly uses more screen real-state. Fortunately, it doesn't show up in the final screenshot.
- Smart Select Edge: JPEG compression. And it's hard to take a full-screen capture.
- Palm Swipe gesture, "Advanced Feature™": Sometimes, it fails to recognize the gesture, causing a UI touch at a random place.
- Game Booster: It only shows up when playing a game.

Also, even on Android 12, there's no way to record a video of the screen, other than Game Booster.

I'm forced to install apps, or use `adb shell screenrecord`

### Crappy camera

The A31 Camera app doesn't allow manual focus distance, not even in "pro" mode, despite the fact that both [Open Camera](https://play.google.com/store/apps/details?id=net.sourceforge.opencamera) and [WebCamera](https://riju.github.io/WebCamera/samples/camera) can control it (this means the firmware supports manual-focus). TBF, the native app supports 3 "focus modes": macro, portrait, auto. Lots of other Galaxy devices support MF, but their camera apps hide it.

Minimum ISO (in "pro" mode) is higher than actual min ISO. I noticed this when taking pictures of bright stuff, then looking at the JPEG EXIF metadata. S6, J3 Mission, and J2 Prime, all have similar artificial limits.

The image quality in the A31 is almost the same as the J3 Mission, despite the fact that there's a freaking multi-cam setup.

### QR tile depends on Weather Daemon

https://github.com/0x192/universal-android-debloater/issues/598

https://github.com/0x192/universal-android-debloater/issues/785

### Memory "optimization"
Something I find pointless, and perhaps harmful, is Device Care app.
The battery optimization features are nice and all, *but why Memory?*
It doesn't "close background apps", it **deletes RAM-cache**, that's the *opposite* of device optimization.
Even worse, they added "Auto-Optimize", and it's **enabled by default,** meaning that every single day, your device **discards ALL of its RAM-cache**, only to generate it again.

Wait, it actually stops "background" apps!, but only those in the "recent apps" screen, which are the most frequently used apps!, therefore **reducing startup perfomance for apps that the user ACTUALLY USES**

This has been an issue **for years**, before One UI even existed.

### Persistent swap memory
Speaking of that, there's a "RAM Plus" feature that's set to **4GB by default**. This has several problems:

- the "Virtual RAM" is **always active**, unlike Linux's swap (which is only active when RAM explodes). this considerably reduces flash-storage lifespan, because of the frequent write-operations
- more background apps means more battery wasted
- storage is already slower than memory, and running too many BG apps will decrease performance

The good news is that "One UI 5" will allow users to easily turn it off. I have "One UI 4" so I had to [use ADB to disable it](https://forum.xda-developers.com/t/disable-samsung-ram-plus.4491743).
To control it easily, I granted /Llamalab/Automate `WRITE_SECURE_SETTINGS` permission. This also allows me to [enable it again](https://reddit.com/r/galaxys10/comments/zj7itl/comment/izw7y8q) (just-in-case)

## etc

This following isn't a rant, I just find it funny that [S Cloud requests a permission that will be permanently denied](https://reddit.com/r/TechNope/comments/10crdie/when_the_system_denies_a_permission_that_it)

## Conclusion

Needless to say, I fucking hate Samsung, **almost as much as Apple**. I wish I had a phone by any other brand (except Huawei and Xiaomi, those are useless to me)

S knows they have a monopoly over the smartphone market, and they love to abuse that power.
**S is following the steps of YouTube**

To be fair, S is a good hardware designer/manufacturer, I just think they suck at software design.
BTW, I think this is the reason why Google and S complement each other, because G sucks at hardware.

I've never used a Galaxy Nexus, but I guess it was a high-quality phone for its time (for the reasons mentioned previously)
