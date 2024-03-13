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

Main Features (release3 only. THIS BRANCH DOES NOT SUPPORT C3X USE BETA3 )
==============
 - Always On lateral for all car makes.
 - Dashcam recoarding function. Stored in /data/media/0/videos/
 - All tuning types for all vehicles. (PID, INDI, LQR, TORQUE)
 - The ability to toggle every aspect of your openpilot experience
 - DE2E (dynamic end to end long) auto switch between ACC to E2E Long( works with voacc cars as well i.g honda, vw) [Demo Video](https://youtu.be/O4qxUAk9qRk)
 - Accleration Profiles controlled from your car's physical button ( TOYOTA ONLY: drive mode button ) or from the UI (OP Long only).
 - Dynamic Follow for all OP long cars. (Toyota can use the distance button on the wheel)
 - Better Long tune for Toyota.
 - Low speed override for Toyota.
 - Auto lock and unlock door for Toyota.
 - Volkswagen support for auto resume.
 - Choose bettween three different Lateral palanner. (0.8.13, 0.8.16, latest)
 - Laneline with auto DLP (Dynamic Lane Profile) @sunnyhaibin.
 - Lane chage mode (auto lane change assist) customizeable.
 - Car selector for fast start up.
 - MapBox support without needing comma prime
 - C2 support for lastest master release via beta/release2/release2_e2e branches
 - Rainbow path for all the tesla lovers (changes based on the accelration) 
 - Block alc if you are close to the road edge.
 - Dynamiclly Change lateral tune based on user selected toggle.
 - Enhanced BSM detection for Toyota. (Prius is now supported and rav4 TSS1) other vechials may work if it has stock bsm system but openpilot does not support it.
 - WIP: https://bit.ly/navonop
  
Branch Definitions
====================

 - `beta3:` main branch for c3 users rebased to [comma/master](https://github.com/commaai/openpilot) a week prior then checked for stability before added lastest Dragonpilot features on top for your enjoyment.
 - `r2:` main branch for c2 users based of [comma/master](https://github.com/commaai/openpilot), functionally as stable as the c2 will be given it's hardware limitations.
 - `d2/3:` developemnt branch on the cutting edge most likely unstable branches of what future of Dragonpilot will be..
 
How To Install
===============

 - `Shane fork installer for Comma 3:` Type (https://smiskol.com/fork/dp) on custom URL window for `beta3:`. 
 - `Shane fork installer for Comma 2:` Type (https://smiskol.com/fork/dp/r2) on custom URL window for `r2:`.
 - `Shane fork installer for Comma 2:` Type (https://smiskol.com/fork/dp/d3) on custom URL window for `development:`.
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
