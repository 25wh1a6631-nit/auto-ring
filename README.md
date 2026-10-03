# Ring On Demand

Build a fully functional Android-first app for my Motorola Moto G85 5G that automatically switches my phone between Ring and Silent mode based on whether I am at Home or College.



🎯 The problem



I often come home from college and forget to turn my phone back to Ring mode. Because of this, I miss important calls.



I want an app that handles this automatically in the background.



The basic behavior should be:



🏠 At Home → Ring mode 🔔



🎓 At College → Silent mode 🔇



I should not have to manually change the sound mode every day.



---



1. CORE AUTOMATION



The app must use real Android geofencing/location detection, not a fake in-app simulation.



I should be able to save two locations:



🏠 Home



A location selected using:



- Current location

- OR a map/location picker



🎓 College



A location selected using:



- Current location

- OR a map/location picker



Both locations should have an adjustable geofence radius, for example:



- 100 m

- 200 m

- 300 m

- Custom radius



Default: around 150–200 m.



---



2. SOUND MODE LOGIC



The core logic should be:



When I ENTER the Home geofence



Automatically switch the actual phone to:



🔔 Ring mode



Then show a notification:



«🏠 Welcome home — Ring mode enabled.»



---



When I ENTER the College geofence



Automatically switch the actual phone to:



🔇 Silent mode



Then show:



«🎓 College detected — Silent mode enabled.»



---



When I LEAVE College



Do NOT immediately switch to Ring mode.



I may still be travelling home, shopping, visiting somewhere, etc.



Instead, wait until I actually enter the Home geofence.



Then switch to Ring mode.



---



When I leave Home



Do NOT automatically switch to Silent mode simply because I left Home.



Only switch to Silent mode when I actually enter the College geofence.



This distinction is important.



The desired state machine is:



HOME → Ring



TRAVELLING → Keep current mode



COLLEGE → Silent



TRAVELLING HOME → Keep current mode



HOME AGAIN → Ring



---



3. COLLEGE SCHEDULE



Add an optional college schedule.



Example:



Monday–Friday

College starts: 8:30 AM

College ends: 4:00 PM



Allow the user to customize:



- Days

- Start time

- End time



However, location should be the primary trigger.



For example:



If college normally ends at 4 PM but I reach home at 5 PM:



→ Stay in the current mode while travelling

→ Switch to Ring immediately when I enter Home.



If I reach home at 3:30 PM:



→ Switch to Ring immediately when I enter Home.



Do NOT rely only on fixed times.



---



4. IMPORTANT EDGE CASES



Handle these situations properly.



Case 1 — I am already at Home



If the app starts while I am already inside the Home geofence:



→ Detect Home

→ Set Ring mode if automation is enabled.



Case 2 — I am already at College



If the app starts while I am already inside the College geofence:



→ Detect College

→ Set Silent mode if automation is enabled.



Case 3 — I leave College



Do not switch to Ring immediately.



Wait until Home is detected.



Case 4 — I visit somewhere after college



Example:



College → Mall → Home



Do not change the mode at the mall.



Only change it when Home is detected.



Case 5 — I visit somewhere from Home



Example:



Home → Shopping → Home



When I return Home:



→ Ensure Ring mode is enabled.



Case 6 — Geofence boundary



Avoid repeatedly switching modes if I am moving around near the edge of a geofence.



Use appropriate geofence radius, transition handling, debouncing/cooldown, and Android location APIs.



---



5. MAIN DASHBOARD



Create a very clean and modern dashboard.



The main screen should immediately show:



Current location



🏠 At Home



or



🎓 At College



or



📍 Away



Current sound mode



🔔 Ring



or



🔇 Silent



Automation



🟢 Automation Active



or



⚪ Automation Paused



Next action



Examples:



«"Ring mode will activate when you reach Home."»



or



«"Silent mode will activate when you reach College."»



---



6. QUICK CONTROLS



Add simple controls:



- Enable Automation

- Disable Automation

- Test Ring Mode

- Test Silent Mode

- Change Home

- Change College

- Edit College Schedule

- Change Geofence Radius



The Test buttons should actually attempt to change the phone's real sound mode.



---



7. PERMISSION SETUP



Create a simple first-time setup flow.



Explain and request only the permissions genuinely required.



The app may need permissions related to:



- Location

- Background location

- Notifications

- Notification policy / Do Not Disturb access if required for changing sound modes



Do not simply request permissions without explaining them.



For each permission, explain in simple language why it is needed.



Example:



«📍 Location access

We use your location only to know when you arrive at Home or College so we can automatically change your sound mode.»



---



8. MOTOROLA MOTO G85 5G SUPPORT



I am specifically using a:



Motorola Moto G85 5G



running Android.



Build the app with Android/Motorola background restrictions in mind.



The app must:



- Work when the app is closed/minimized.

- Continue geofence monitoring in the background.

- Recover after phone restart.

- Handle Android background-location restrictions.

- Handle Motorola battery optimization/background restrictions.

- Detect when required permissions are missing.

- Tell me exactly what settings I need to enable if Motorola prevents reliable background operation.



If battery optimization needs to be disabled for this app, provide a clear setup guide directing the user to the appropriate Android/Motorola settings.



Do not assume that simply keeping the app open will solve the problem.



---



9. ACTUAL SOUND MODE CONTROL



This is extremely important.



Do NOT create an app where the UI merely says:



"Ring mode enabled"



while the actual phone remains silent.



The app must use the appropriate Android system APIs to attempt to change the actual device ringer/sound mode.



When Home is detected:



Actual phone → Ring



When College is detected:



Actual phone → Silent



If Android requires a special permission or user authorization to modify sound/Do Not Disturb settings:



1. Detect that permission is missing.

2. Explain why it is required.

3. Provide a button to open the appropriate Android settings page.

4. Clearly show whether setup is complete.



Do not pretend the automation works if Android has blocked the required action.



---



10. BACKGROUND RELIABILITY



Use proper Android mechanisms for:



- Geofencing

- Background location

- Broadcast receivers where appropriate

- Boot/restart recovery

- Notifications

- Sound/ringer mode management



The app should not constantly poll GPS unnecessarily.



Prefer Android's efficient geofencing/location mechanisms.



Save the current automation state locally so the app can recover after being killed or restarted.



---



11. NOTIFICATIONS



Whenever the app automatically changes the mode, show a small notification.



Examples:



🏠 Welcome home

Ring mode has been enabled.



🎓 College detected

Silent mode has been enabled.



Also notify me if automation cannot work because an important permission or system setting is disabled.



---



12. AUTOMATION LOG



Add a simple history screen showing recent automatic actions.



Example:



Today



- 8:42 AM — College detected → Silent

- 5:18 PM — Home detected → Ring



This helps me verify that the automation is actually working.



Keep this lightweight; no unnecessary analytics.



---



13. SETTINGS



Create a Settings page with:



Locations



- Home location

- College location

- Geofence radius



Schedule



- College days

- Start time

- End time



Automation



- Enable/Disable

- Notifications on/off



Permissions



Show a simple status:



✅ Location permission

✅ Background location

✅ Notification permission

✅ Required sound/Do Not Disturb access



If something is missing:



⚠️ Permission required



with a button to fix it.



---



14. UI DESIGN



Make the UI modern, minimal, and extremely easy to understand.



I do NOT want a complicated productivity app.



The app should feel like a tiny utility that quietly works in the background.



Use:



- Clean cards

- Large status indicators

- Simple icons

- Rounded UI elements

- Good spacing

- Light and dark mode

- Clear typography

- Minimal buttons



The home screen should be understandable within 5 seconds.



The main focus should be:



Where am I?



What sound mode am I in?



Is automation working?



---



15. FIRST-TIME USER EXPERIENCE



On first launch:



Screen 1



"Never miss a call because you forgot your ringer again."



Explain the purpose in one or two sentences.



Screen 2



Set Home location.



Screen 3



Set College location.



Screen 4



Set college days and timings.



Screen 5



Enable required Android permissions.



Screen 6



Show:



«You're all set.



🏠 Home → Ring

🎓 College → Silent»



Then take the user to the dashboard.



---



16. IMPORTANT PRODUCT PRINCIPLE



The app should be location-driven, not time-driven.



The schedule is only additional context.



The most important rules are:



ENTER HOME → RING



ENTER COLLEGE → SILENT



LEAVE COLLEGE → DON'T CHANGE



LEAVE HOME → DON'T CHANGE



ANYWHERE ELSE → DON'T CHANGE



This prevents unwanted sound-mode changes.



---



17. TECHNICAL QUALITY



Build a real functional MVP, not a visual prototype.



Prioritize:



1. Reliable Home/College geofencing

2. Actual Android sound-mode changes

3. Background operation

4. Correct permissions

5. Motorola compatibility

6. Simple UI

7. Automation history



Avoid unnecessary features, accounts, social features, advertisements, analytics, or complicated onboarding.



The goal is a small app that solves exactly one problem extremely well:



I should never miss an important call just because I forgot to turn my phone back to Ring mode after college.



Before considering the project complete, test the complete flow:



Home → College → Home



and verify that the actual phone sound mode changes correctly at each stage.

This project was built with [Lovable](https://lovable.dev).

## Build with Lovable

Continue developing this project in the [Lovable editor](https://lovable.dev/projects/c160659a-d8fb-408b-bbf7-f3fed50242ba).

- **Ship faster**: describe what you want to build and Lovable handles the code.
- **Stay in sync**: every change made in Lovable is committed straight to this repository.
- **Full ownership**: this code is yours. Push to `main` on GitHub and your changes sync back into Lovable, ready for your next prompt.

## Development

Prefer working locally? You need Node.js and npm — [install with nvm](https://github.com/nvm-sh/nvm#installing-and-updating).

```sh
git clone <this-repository-url>
cd <repository-name>
npm i
npm run dev
```
