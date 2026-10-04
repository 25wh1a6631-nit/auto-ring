# 📱 Auto Ringer

> Automatically switch your phone between Ring and Silent mode based on your location.

Ever reached college and realized your phone was still on Ring?

Or reached home and missed an important call because you forgot to switch it back?

**Auto Ringer** solves that automatically.

The app uses Android's geofencing capabilities to detect when you enter or leave saved locations and automatically changes your phone's sound mode.

---

## ✨ Features

- 📍 **Location-Based Automation** — Uses geofencing to detect location changes.
- 🏠 **Home & College Locations** — Save locations for automatic switching.
- 🔔 **Automatic Ring Mode** — Switches to Ring when you reach Home.
- 🔕 **Automatic Silent Mode** — Switches to Silent when you reach College.
- 🎯 **Adjustable Geofence Radius** — Configure the detection radius.
- 🔋 **Battery Optimization Support** — Helps the app continue working in the background.
- 🔄 **Restart Recovery** — Re-registers automation after the phone restarts.
- 🧪 **Manual Testing** — Test Ring and Silent modes without physically changing locations.
- 📊 **Activity Log** — View recent automation events.
- ⚡ **Background Location Checks** — Helps detect missed location transitions.

---

## 🧠 How It Works

```text
                    ┌──────────────────┐
                    │    Auto Ringer   │
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │ Android Location │
                    │     Services     │
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │    Geofencing    │
                    │     Detection    │
                    └────────┬─────────┘
                             │
                 ┌───────────┴───────────┐
                 ▼                       ▼
          ┌──────────────┐        ┌──────────────┐
          │   College    │        │     Home     │
          └──────┬───────┘        └──────┬───────┘
                 │                       │
                 ▼                       ▼
           🔕 Silent Mode           🔔 Ring Mode



| Technology                    | Purpose                         |
| ----------------------------- | ------------------------------- |
| Kotlin                        | Android application development |
| Android SDK                   | Android platform                |
| Google Play Services Location | Location & geofencing           |
| AndroidX                      | Android components              |
| Material Design               | User interface                  |
| Gradle Kotlin DSL             | Build configuration             |
| SharedPreferences             | Local settings storage          |


📱 Requirements
Android Studio
Android device running Android 8.0 or higher
JDK 17 or compatible Android Studio JDK
Location services enabled on the device
USB debugging enabled for development


🚀 Installation
1. Clone the repository
git clone https://github.com/YOUR_USERNAME/AutoRinger.git

Replace YOUR_USERNAME with your GitHub username.

2. Open the project

Open the AutoRinger folder in Android Studio.

Wait for Gradle Sync to complete.

3. Connect your Android device

Enable:

Settings
→ About Phone
→ Build Number
→ Tap 7 times

Then:

Settings
→ System
→ Developer Options
→ USB Debugging
→ ON

Connect your phone to your computer and allow the USB debugging prompt.

4. Run the application

Select your Android device in Android Studio.

Click:

▶ Run
⚙️ Setup

After installing the application, grant the required permissions.

Location Permission

Allow:

Precise Location
Background Location

Background location is required because the app needs to detect location changes even when the application is not open.

Notification Policy Access

Allow the application to control the device's sound mode.

Battery Optimization

For reliable background operation, allow unrestricted battery usage for Auto Ringer.

Recommended:

Settings
→ Apps
→ Auto Ringer
→ Battery
→ Unrestricted

The exact settings may vary depending on the Android device manufacturer.

🏠 Configure Locations
Home

Go to your Home location and save it as:

🏠 Home
College

Go to your College location and save it as:

🎓 College

The application uses these saved locations as geofencing zones.

🎯 Geofence Radius

Auto Ringer allows you to configure the detection radius.

A reasonable starting value is:

150 meters

You can increase the radius if location transitions are detected too late.

🧪 Testing

The application includes manual testing functionality so that automation can be tested without physically travelling between locations.

You can test:

🔔 Ring Mode
🔕 Silent Mode
📍 Location Check

The application also records recent automation activity.

Example:

Entered College → Silent
Left College → Ring
Entered Home → Ring
🔄 After Phone Restart

Android may clear or suspend some background processes after a device restart.

Auto Ringer handles device boot events and attempts to restore the required geofencing configuration.

This allows location-based automation to continue after restarting the phone.

🔋 Battery Optimization

Android and individual smartphone manufacturers may restrict background applications to save battery.

If automatic switching is unreliable:

Open the Auto Ringer app.
Follow the battery optimization instructions.
Set battery usage to Unrestricted.
Make sure Location is enabled.
Avoid force-stopping the application.

Some manufacturers may have additional background-app restrictions.

🔐 Permissions

Auto Ringer may require the following permissions depending on the Android version:

📍 Fine Location
📍 Coarse Location
📍 Background Location
🔔 Notifications
🔕 Notification Policy Access
🔄 Receive Boot Completed

These permissions are required for location detection, background automation, notifications, and sound-mode control.

🔒 Privacy

Auto Ringer is designed as a local Android utility.

The application does not require:

User accounts
A backend server
Cloud storage

Location information is used locally to determine whether the device is within configured automation zones.

⚠️ Limitations

Background location behavior can vary between Android versions and device manufacturers.

For reliable operation:

Keep Location enabled.
Keep Google Location Accuracy enabled where available.
Allow unrestricted battery usage.
Do not force-stop the application.
Grant all required permissions.
Keep the device's location services enabled.

Geofence detection may also have some delay because Android does not guarantee an exact transition time.

🗺️ Future Improvements

Potential improvements include:

📍 Support for multiple custom locations
🔔 Vibrate mode
🌙 Do Not Disturb automation
📅 Schedule-based automation
🗺️ Map-based location selection
🎨 Improved onboarding
📊 Automation statistics
🔔 Custom notifications
🧠 Smarter transition detection
⚙️ Per-location sound profiles
🎯 Why I Built This

Auto Ringer was built around a simple everyday problem:

Why should I have to remember to change my phone's sound mode when my location already tells me what mode I need?

Instead of relying on reminders or manually switching modes, this project explores how Android location services can be used to automate a small but useful part of everyday life.

Through this project, I explored:

Android development with Kotlin
Geofencing
Background location
Runtime permissions
Broadcast Receivers
Android power management
System-level sound controls
Local data persistence


🧑‍💻 Author

Nitya

B.Tech CSE (AI & ML) Student

⭐ Support

If you found this project useful, consider giving the repository a ⭐ on GitHub.
