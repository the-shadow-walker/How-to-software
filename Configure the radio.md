Configuring the radio is quite simple. I will most likely make a video and link the documentation so that it is always up to date, but for now I will go over our team specific docs.

**Documentation:** https://frc-radio.vivid-hosting.net/overview/programming-your-radio-at-home
**The video:** I haven't made the video yet

### Plugging the radio in
- This can vary quite a bit for robots depending on how we power the radio that year, in general for the robot we will use direct 12v to the radio, and then Rio (or whatever the new onboard possessor is from now on, Pi 5 compute module pls?) to the port labeled "Rio" and then AUX 1 and 2 is used for anything else like Photon Vision, Questnav, etc...
- The port labeled "DS" (Driver Station) is where you will plug the laptop that you are using to configure/connect the radio. 
- Most of the time we will power the Access point radio (The one that plugs into your computer.) over POE (Power Over Ethernet) and it will plug into the "RIO" port. You will know it powered on when the led's on the top turn on.
- To summarize, The computer plugs into "DS", The Rio plugs into "RIO", Power plugs into either the 12v direct or over POE which also plugs into the "RIO".


  ### Initial connection
- First connect the radio via Ethernet. This step applies for both the robot radio and the access point radio.
- After that open your web browser and navigate to either http://192.168.69.1 or http://10.49.11.1 if the radio has already been configured 
- It should take you to a config screen that looks like this:
![[Pasted image 20260611115836.png|316]]

Once you get to that screen, you can now configure the radio.
### For the radio that plugs into the robot (Robot Radio)
- At the top set it to the access point mode
- You can leave both 2.4ghz and the QoS BW Limit
- You don't have to enable the SystemCore mode (unless we specifically need it)
- Set team number to 4911
- SSID suffix can be whatever the name of the robot is (ex: Rossi for the 2026 robot)
- WPA key for 6 ghz connection can be something like ROSSI4911 (Name in caps, followed by number)
- WPA key for 2.4 ghz can be the same as the 6 ghz one
- Once that has been typed in click the big "Configure" button

### For the radio that plugs into the laptop (Access Point)
The process will be quite similar, TODO: Get the actual GUI of this (this is for the robot radio config, not the ap config, but they should be similar.):
At the top set it to the access point mode
- You can leave both 2.4ghz and the QoS BW Limit
- You don't have to enable the SystemCore mode (unless we specifically need it)
- Set team number to 4911
- SSID suffix can be whatever the name of the robot is (ex: Rossi for the 2026 robot)
- WPA key for 6 ghz connection can be something like ROSSI4911 (Name in caps, followed by number)
- WPA key for 2.4 ghz can be the same as the 6 ghz one
- Once that has been typed in click the big "Configure" button


### Troubleshooting
There is a --lot-- to cover for troubleshooting, but the led indicators can be very helpful. The full led debug docs can be found here: https://frc-radio.vivid-hosting.net/overview/led-status-indications

Turning it on and off again can be surprisingly helpful, and also re configuring both radios making sure everything matches up and that both robots are turned on. After competitions, you will have to reconfigure the robot radio.