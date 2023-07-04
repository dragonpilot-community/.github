# Welcome to Dragonpilot

<img src="https://github.com/dragonpilot-community/dragonpilot/blob/release3/selfdrive/assets/img_spinner_comma.png" align="center"
     alt="DP" width="240" height="240">

<details>
  <summary><b>Table of Contents<b></summary>
  <ol>
    <li>
      <a href="#about-this-fork">About This Fork</a>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#how-to-install">Installation</a></li>
      </ul>
      <ul>
        <li><a href="#branch-definitions">Branch Definitions</a></li>
      </ul>
    </li>
    <li><a href="#main-features">Main Features</a></li>
    <li><a href="#setting-menu">Usage</a></li>
    <li><a href="#community-and-contributing">Community</a></li>
    <li><a href="CONTRIBUTORS.md">Contributing</a>
    <li><a href="#user-data">User Data</a></li>
    <li><a href="#license">License</a></li>
  </ol>
</details>

About This Fork
================

This fork is focused on Toyotas and Lexus with secondary attention given to Honda and Hyundai. All of the upstream vehicle are supported. 

Warning
=============

***This fork is recommended for experienced users of openpilot only. This fork contains many experimental features and tweaks that modify heavily and differ from stock openpilot experience. Use at your own risk.***

Main Features
==============
 - Always On lateral for all car makes.
 - Dashcam recoarding function. Stored in /data/media/0/videos/
 - All tuning types for all vehicles. (PID, INDI, LQR, TORQUE)
 - The ability to toggle every aspect of your openpilot experience
 - Mapd support thanks to the @move-fast
 - Mapd can be used offline on select regions by downloading database on device.
 - Mapd can recoginze stop sign, yield sign, speed bump and round about.
 - DE2E (dynamic end to end long) auto switch between ACC to E2E Long( works with voacc cars as well i.g honda, vw) [Demo Video](https://youtu.be/O4qxUAk9qRk)
 - Accleration Profiles controlled from your car's physical button ( TOYOTA ONLY: drive mode button ) or from the UI (OP Long only).
 - Dynamic Follow for all OP long cars. (Toyota can use the distance button on the wheel)
 - Better Long tune for Toyota.
 - Low speed override for Toyota.
 - Auto lock and unlock door for Toyota.
 - Volkswagen support for auto resume.
 - Choose bettween three different Lateral palanner. (0.8.13, 0.8.16, latest)
 - Laneline with auto DLP (Dynamic Lane Profile) @sunnyhaibin.
 - Lane chage mode (1 = lane change assist, 2 = auto lane change assist) both customizeable.
 - Car selector for fast start up.
 - MapBox support without needing comma prime
 - C2 support for lastest master release via beta/release2/release2_e2e branches
 - Rainbow path for all the tesla lovers (changes based on the accelration) 
 - Block alc if you are close to the road edge.
 - Dynamiclly Change lateral tune based on user selected toggle.
 - Enhanced BSM detection for Toyota. (Prius is now supported and rav4 TSS1) other vechials may work if it has stock bsm system but openpilot does not support it.
  
Branch Definitions
====================

 - `release3:` main branch for c3 users rebased to [comma/master](https://github.com/commaai/openpilot) a week prior then checked for stability before added lastest Dragonpilot features on top for your enjoyment.
 - `release2:` main branch for c2 users based of [comma/master](https://github.com/commaai/openpilot), functionally as stable as the c2 will be given it's hardware limitations.
 - `beta2/3:` Cutting edge most likely unstable branches of what future of Dragonpilot will be
 - `release2_e2e:` cutting edge features being tested on older version otherwise stable version of Dragonpilot
 
How To Install
===============

 - `Shane fork installer for Comma 3:` Type (https://smiskol.com/fork/dp) on custom URL window for `release3:`. 
 - `Shane fork installer for Comma 2:` Type (https://smiskol.com/fork/dp/beta2) on custom URL window for `beta2:`.
 - `Shane fork installer for Comma 2:` Type (https://smiskol.com/fork/dp/release2) on custom URL window for `release2:`.
 - `Shane fork installer for comma 2:` Type (https://smiskol.com/fork/dp/release2_e2e) on custom URL window for `release2_e2e:`.

Community and Contributing
===============
We do not have a specialized discord or slack for development and no plans to make one. 
All development of dragonpilot is to take place in [Dragonpilot development repo](https://github.com/dragonpilot-community/dp-devel) this includes any bugs or issue.

Setting Menu
=============
BIG BLUE box is the car selector for fast start up. Other wise please try this if your car doesn't recognize on ignition don't make a bug report untill you tried it please.
   
 - `navigation`
   * Will only Works when `Enable Nav` is on under dp-maps. To set your home / work destination use the qr code on the sidebar.
   
 - `Dragonpilot General tab`
   - **Use Custom API server:** Enable this if you wish to connect to a custom API server.Default to \"https://api.retropilot.org/", change \"dp_api_custom\" if you want to change API server URL. Reboot required.
   - **GPS Logger:** This will store your track in `/data/media/0/gpx_logs/`. Reboot required.
   - **Auto Shutdown:** Enable this if you wish to shutdown your device automatically.
   - **Flashing Panda Firmware:** Tap the button to update your panda firmware. The device should reboot once if it finish updating.
   - **Pandas Firmware Recovery:** Tap the button ONLY if your panda ran into issue.
   - **Reset dragonpilot config:** Tap the button to reset all your dragonpilot congiration to default value. Reboot required.
   - **Delete All Driving Log:** Tap the button to delete ALL your driving logs (including dashcam `/gpx/` driving logs)
   - **Dashcam mode** Tap to record screen. This will record all UI elements and current camera view displayed on main display. Located `/data/media/0/videos/`

 - `Dragonpilot Controls tab`
   - **Always On Lateral:** 0 = stock  1 = Stock Long (if you use stock acc) 2 = OP Long (if your car supports op long). Reboot required.
   - **Planner Vesrion:** change your lateral planner version. 1 = 0.8.13 2 = 0.8.16
   - **Controller Type:** Override the default controller. 1 = PID 2 = LQR 3 = Torque Your Vehicle may not support all the options, YMMV.
   - **Use Lanelines:** Use Lanelines instead of End-to-End when possible
   - **Use Alternative Controller:** This feature will let you use alternative lateral controller at higher set speed.
     - **When set speed Above:** when acc SET speed above the setting, it will switch to alternative controller. 1 km/h = 0.62 mph
     - **Alternative controller:** 1 = PID 2 = LQR 3 = Torque. Your Vehicle may not support all the options, YMMV
     - **Use Lanelines:** Use Lanelines instead of End-to-End when possible
   - **Enable Torque Ctrl Auto Tune:** Enable auto tune Torque controller. WORKS WELL ONLY ON SOME VEHICLES. More linear steering experience.
   - **ALC RoadEdge Detection:** Enabling this will prevent lane change when you are too close to road edge.
   - **Manual Lane Change:** Enabling this will allow lane change manually when blinker is on. NOTES: Once LCA/ALCA is enabled, those settings will override manual lane change.
                            e.g. If you have this option on and LCA at 20km/hr, ALCA at 40km/hr, speed below 20km/hr will be manual lane change. If you disable LCA/ALCA and have this option on, manual lane change will apply to ALL SPEED.
   - **Lane Change Mode:** 1 = Lane Change Assist (LCA) 2 = Auto Lane Change Assist (ALCA)
     - **LCA Min Speed:** LCA minimum engage speed in mph. 1 mph = 1.61 km/h
     - **ALCA Delay:** Once the vehicle meets all ALCA criteria, it will wait for the seconds set here before performing lane change automatically
     - **ALCA Min Speed:** ALCA minimum engage speed in mph. 1 mph = 1.61 km/h
   - **Manually Control Accel Mode:** Enable this if you wish to adjust openpilot's acceleration control.
   - **Enable vision based turn control:** Use vision path predictions to estimate the appropriate speed to drive through turns ahead
   - **Manually Control Following Distance Mode:** Enable this if you wish to adjust openpilot's following distance. openpilot by default keeps 1.45 secs distance to lead car. When on close will be dynamic but get closer in traffic. Normal is also dynamic and it get further and far is stock 1.45se
   - **Dynamic End-to-end:** Automatically Turn On and Off End-to-end longitudinal, this will ignore the stock end-to-end settings
     - **DE2E w/ VOACC:** Enable this if your vehicles is in VOACC (e.g. Honda Bosch / VAG)
     - **DE2E Adapt Following Mode:** Enable this if you wish to use following dist. mode in DE2E.
     - **DE2E Adapt Accel Mode:** Enable this if you wish to use accel mode in DE2E.
   - **Enable Device Temp Check:** Override openpilot temperature safe check to engage
   - **Enable Max Ctrl Speed Check:** allows openpilot run at more than 95 mph
   

- `Dragonpilot UI tab`
   - **Display Mode:** Standard = stock, On-Road = The display will be off when driving (excluding warnings), MAIN = The display will be off when ACC Main is on (excluding warnings), OP = The display will be off when OP is enabled (excluding warnings), Off = The display will be off completely (including warnings). REBOOT REQUIRED.
   - **Alert Volume:** The audible alert mode determines whether or not the device will emit a sound when there is an alert. Standard = The device will emit a sound for all alerts, Warning = The device will only emit a sound for warnings, Off = The device will not emit any sound.
   - **Screen Brightness:** Adjust your screen brightness.
   - **Display Speed:** Enable this to display your current speed.
   - **Display Event/Steer Icon:** Enable this to display the icon.
   - **Display Driver Monitor Indicator:** Enable this to display the icon,
   - **Display side info** Enable this to display steering angle/lead car/distance/engine RPM.
   - **Display Top Info:** Enable this to display time / system temp / battery level.
   - **Display Lead Speed/Distance:** Display detected lead objects' speed and distance.
   - **Display Driver Camera:** Display Driver Camera when reversing.
   - **Rainbow Path:** For all the tesla fanboy's..

- `Dragonpilot Cars tab`
   - **Enable SnG Mod Toyota:** Enable this to fix stop and go (SnG) issue on some models. Reboot required.
   - **Enable FM Physical Button Ctrl Toyota:** Enable this to link Following Distance Mode (FM) control to the physical button (TSS2).\ONLY WORK ON SOME OF TSS1 VEHICLES WITH SDSU. Reboot required.
   - **Enable AM Physical Button Ctrl Toyota:** Enable this to link Accel Mode (AM) control to the physical button (TSS2). ONLY WORK ON SOME OF TSS1 VEHICLES. Reboot require.
   - **Enable Enhance BSM Requests:** Enabling this will block alc for all the car's that has stock factor BSM that openpilot currently do not support. (Prius TSS2 and Rav4 TSS1 has been fully tested and working) also allow's your toyota/lexus see more object's. Reboot require.
   - **Turn On Cruise Speed Override Toyota:** This feature will let you set your cruise speed below vehicle standard. (usually at 26~40 km/h)
   - **Enable Door Auto Lock Toyota:** Enable this to lock doors when drive above 25 km/h. ONLY WORK ON SOME VEHICLES.
   - **Enable Door Auto Unlock Toyota:** Enable this to unlock doors when shift to gear P. ONLY WORK ON SOME VEHICLES.
   - **Enable TSS2 RAV4 Special PID Tune:** Enable this to use a special PID tune on 2019+ TSS2 RAV4. Reboot Required.
   - **Enable TSS-P Prius Special Torque Tune:** Enable this to use a special Torque tune on PRIUS 2017 w/ bad angle sensor. Reboot Required.
   - **Enable Reverse ACC Set speed:** Enabling this will reverse set acc short press +5 jump, Long press +1 Jump. Reboot Required.
   - **Enable EPS Mod Mod Honda:** Enable this will increase steering, USE IT ONLY if you have a modded EPS firmware. Reboot required.
   - **Display Below Steer Speed Alert Mazada** Enable this will show below steer speed alert.Thanks to @TheCrowd
   - **Bypass Dashcam mode Mazada** Enable this to bypass dashcam mode.
   
- `Dragonpilot Maps tab`
 - **DP NAV:**
      - **Enable Nav.:** This will let use the build in Navigation. Reboot required.
        - **Enable Local Nav Server:** This will let use Navigation feature with your own access key. Use web interface to control it: *http://<device_ip>:8082* or scan the qr code on the sidebar. You will need to apply your own mapbox token at https://www.mapbox.com/. Internet access from mobile phone (tethering) is required. Reboot required.
        - **Search Destination using Google Maps:** This will allow you to search destination in google map api. You will need to apply your own google map api key. Enter your key detail in web interface once it's enabled.
        - **Show Full Screen Nav.:** This will show navigation in full screen. Please tap green boarder if you wish to switch back drive view.
 
 - **DP MapD**
      - **Enable MapD:** Use OSM to assist lateral/longitudinal control. Please note: This feature will works only when your car support OP longitudinal. *MapD will contribute your route to OSM for future improvement automatically.* You can add your own offset for mapd just follow the readme under `/selfdrive/mapd` Not connecting to the internet for while might feel up device storage from all the gps traces.
        - **Enable Speed Limit Control:** Use speed limit signs information from map data and car interface to automatically adapt cruise speed to road limits.
        - **Enable Speed Limit Offset:** Set speed limit slightly higher than actual speed limit for a more natural drive.
        - **Enable Map Data Turn Control:** Use curvature info from map data to define speed limits to take turns ahead.
        - **Show debug UI elements:** Show UI elements that aid debugging.
      - **Use Mapd without data:** You need minimum of 50 gb storage in `/data/media/0/`. Run `df -h /data/media/0/` to see how much space you have available. Strongly recommend getting 1 TB ssd. If you decide not to upgrade you can delete all logs under dp-general.
      - **OpenstreetMap Data:** update check and offline datebase use for mapd offline maps. Requires `Enable Mapd` and  `Use Mpad without data` toggle active to work. (Thanks to @sunnyhaibin for UI portion of DB selector)
        

User Data
================

By default, dragopilot does upload data to comma servers(unless user turns off the toggle). You may enable data collection and forwarding to either comma or retropilot.api via toggle under DP general.
Logger is on by default.
We log crashes and fingerprinters to our sentry server.
Mapd when toggle and enabled will automatic upload your gps trace to openstreetmap for everyone to see. This to help the mappers who work on openstreetmaps better map your area.

License
================

openpilot is released under the MIT license. Some parts of the software are released under other licenses as specified.

Any user of this software shall indemnify and hold harmless Comma.ai, Inc. and its directors, officers, employees, agents, stockholders, affiliates, subcontractors and customers from and against all allegations, claims, actions, suits, demands, damages, liabilities, obligations, losses, settlements, judgments, costs and expenses (including without limitation attorneys’ fees and costs) which arise out of, relate to or result from any use of this software by user.

**THIS IS ALPHA QUALITY SOFTWARE FOR RESEARCH PURPOSES ONLY. THIS IS NOT A PRODUCT.
YOU ARE RESPONSIBLE FOR COMPLYING WITH LOCAL LAWS AND REGULATIONS.
NO WARRANTY EXPRESSED OR IMPLIED.**

---

<img src="https://d1qb2nb5cznatu.cloudfront.net/startups/i/1061157-bc7e9bf3b246ece7322e6ffe653f6af8-medium_jpg.jpg?buster=1458363130" width="75"></img> <img src="https://cdn-images-1.medium.com/max/1600/1*C87EjxGeMPrkTuVRVWVg4w.png" width="225"></img>
