# Mesh-Network-Updated
This is an updated version of the previous Mesh nwteork Project. This contains functional code, in order to run the Mesh Network on Nording Thingy:52 devices, with Nordic nRF52840 Development Boards as end devices

# Publish - Subscribe communication between boards: # 

1. On the pc:
- load the appropriate code to the Thingy:
- run the project found in \nrf5_SDK_for_Mesh_v320\examples\thingy52-mesh-provisioning-demo-master\thingy_provisioning_demo
- load the appropriate code to the DevBoard:
  - SERVER:
    - For the board which will be turning the _LED_ on, navigate to  \nrf5_SDK_for_Mesh_v320\examples\light_switch\server and choose the appropriate project.  
  - CLIENT:
    - For the board which will be the _SWITCH_, navigate to: \nrf5_SDK_for_Mesh_v320\examples\light_switch\client and choose the appropriate project. 

2. In the phone App:
- if (node == LED) then from „Elements“ → Generic On OFF Server → First from „Bound App Keys → click „Bind Key“. Then, „Subscriptions“ →Subscribe → then choose an address*  
- if (node == SWITCH) then from „Elements“ → Generic On OFF Client → First from „Bound App Keys → click „Bind Key“. Then, „Publish“ →Publish Address → then choose an address*  

*This must be the same address
