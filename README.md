# Mesh-Network-Updated
This is an updated version of the previous Mesh nwteork Project. This contains functional code, in order to run the Mesh Network on Nording Thingy:52 devices, with Nordic nRF52840 Development Boards as end devices.  
There are two main hardare components that need to be involved in the Mesh network. Therefore this project is separated into two parts:
1. One is running the Mesh on the Thingy:52 devices - you may see it [below](#here "Goto Documentation on how to successfully run examples on Thingy:52 devices")
2. The other part is focused on having the Mesh on the nRF52840 -   [here ](#here "Goto Documentation on how to successfully run examples on Thingy:52 devices") it is

Documentation on how to successfully run examples on Thingy:52 devices<a name="TOP"></a>
===================
Here is an explanation on how to load the provided code on the Thingy devices.
## Hardware needed ##
- 2 x [Thingy:52](https://www.nordicsemi.com/Software-and-tools/Prototyping-platforms/Nordic-Thingy-52)
- 1 x [nRF52840 Board](https://www.nordicsemi.com/Software-and-Tools/Development-Kits/nRF52840-DK)
- 1 x micro USB cable 
- 1 x  [10-pin 2x5 Socket-Socket 1.27mm IDC (SWD) Cable](https://www.adafruit.com/product/1675)
- 1 x smartphone 

### Hardware setup ###
The HW setup for flashing the code to the Thingy:52 is the following:  
[PC] ---- micro USB ---- [nRF52840] ---- SWD cable ---- [Thingy:52]

## Software needed ##
- PC/laptop:
  - Segger Embedded Studio
    - Remarks:
    - For Segger, I used the version Embedded Studio for ARM, Windows, 64-bit
    - In Segger Embedded Studio, the settings in steps 8 and 9 from this link need to be followed: https://github.com/NordicPlayground/thingy52-mesh-provisioning-demo. However, Step 9 is not so well explained, so I will explain it in more detail, below [Additions](#Additions "Goto Additions")
  
- Phone:
  - [Nordic Thingy](https://play.google.com/store/apps/details?id=no.nordicsemi.android.nrfthingy&hl=en_US)
  - [nRF Mesh](https://play.google.com/store/apps/details?id=no.nordicsemi.android.nrfmeshprovisioner)
 
 #### Remarks: ####
- No HW modifications need to be made to the  nRF52840 board or to the Thingy:52 in the beginning (e.g. no jumpers).
- The nRF52840 will be supplied from the cable (alternatively, it may also use the battery)
- The Thingy:52 boards are always supplied just from the battery. Connecting the SWD cable, the battery will charge

### Initial Steps ###
In order to run the default SW on Thingy:
- For this first step, the Thingy:52’s can run just on battery – no cable needed
- The Thingy:52 devices come with a default firmware installed. This may be used in order to interact with the board for the first time and check its functionalities. For this, the Nordic Thingy Application needs to be downloaded on the smartphone.
- Afterwards, turn on the Thingy:52’s – there is a small switch on the bottom left side. Now, the Thingy:52 will start to advertise 
- Next, activate Bluetooth and location from your phone and enter the Nordic Thingy Application. Now, your phone will be looking for available devices, to connect to
- From now on, you should be able to connect to each new Thingy, give them names and discover all its sensors data in real time.  
-----------------------insert photo here------------------------------------------
- All this information is kept after turning off the Thingy’s. To erase the firmware, please have a look at the next steps

### Next Steps ###
In order to run the Mesh Software, on Thingy:52:
- After discovering the Thingy:52 features,  the Mesh firmware can be loaded into the boards, so that they can participate in a Mesh network. This will give the user the possibility of assigning the boards different individual or group addresses, so that controlling multiple Thingy’s from the phone can be achieved easily  
-To achieve this, the Thingy:52 devices need to be erased of this initial firmware and loaded with a new one. For this, the mentioned tutorial in [this link] (https://github.com/NordicPlayground/thingy52-mesh-provisioning-demo) shall be followed. 
- As I mentioned in the the HW setup part, the way to load the code on Thingy’s is via the SWD cable.

 #### Additions ####
Additions to the already mentioned steps are the following:

Step 5. Clone this repo into \examples\ --> it refers to nrf5_SDK_for_Mesh_v320\examples
Step 9: The following needs to be done from Segger Options (Tools -> Options):  
------------------------------- insert picture here -------------------

 #### Last thoughts ####

- After successfully completing the steps and loading the code on the Thingys, their provisioning needs to be made, from the phone. That is, assigning them with addresses. This is done using the *nRF Mesh App*, available [here] (https://play.google.com/store/apps/details?id=no.nordicsemi.android.nrfmeshprovisioner&hl=de)
- And [here] (https://www.youtube.com/watch?v=XthbU9NP0Yg) is an video example on how the addresses can be assigned from the phone, to achieve a Light Switch – Light Bulb(s) scenario
- Finally, the boars are loaded with a **Client – Server** model. Depending on the addresses assignment from the *nRF Mesh App*, some boards can act as a switch (publisher) and the other(s) as light bulb (subscriber, client).
- ***Bonus***: by having a look in the C code, we may notice that the relay feature is enabled. So now, if we wish to have an end-to-end communication over multiple Thingy’s as hops, this software enables messages forwarding through them. 

