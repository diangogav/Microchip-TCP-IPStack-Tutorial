This guide is based in a post make by maxruben at https://www.microchip.com/forums/m722110.aspx.

This post helped me start on the TCPIP/Stack Library Microchip and i decided to shared with you in more detail.

---
 1. Download the microchip-libraries-for-applications v2013-06-15 on https://www.microchip.com/mplab/microchip-libraries-for-applications

 2. Install TCP library

 3. In the installation path, find the TCP folder, this contain a demo application named DemoApp that we will use as the based for our apliccation.

 4. Open DemoApp project in MPLABx and compiled for check to work.

 5. Having in mind the microcontroller we will use, and having checked the necessary requirements, go to the Configs directory in the DemoApp folder. 

 6. cite maxruben: There you can see two types of files for the different build configurations (demo boards). One starts with HWP and the other with TCP. These are the configuration files used to configure your hardware (HWP) and the different TCP/IP protocols, memory type and size to use for ram and storage for web pages and basic TCP/IP settings (TCPIP).

 7. cite maxruben: Make a copy of the files that most closely matches your hardware and TCP/IP requirements and rename them to something appropriate for your configuration. "HWP_C18_ENC28.h" and "TCPIP_C18_ENC28.h" for example.

 8. cite maxruben: Now you can go into MPLABX and in the dropdown list for the different build configurations, go all the way down and select Costumize...

 9. cite maxruben: The project properties dialog for all build configurations are opened. Click the Manage Configurations... button. Select a configuration and click the Duplicate button. Now select the newly created configuration and click the Rename button and rename it. With the renamed configuration still selected, finally click the Set Active and OK buttons.

 10. cite maxruben: Then you get back to the project properties dialog for the newly created configuration. Change the processor, hardware tool (debugger/programmer) and compiler tool chain to the ones you wish to use.

 11. cite maxruben: Still in the project properties dialog, select the compiler in your configuration tree in the categories list to the left. This will show the options for the compiler which is a bit different depending on the compiler you want to use. In the General category look for the Preprocessor macro definitions field. This is now set to the value for the configuration you copied. Change this to CFG_INCLUDE_C18_ENC28 for example. Set the same symbol for the assembler options.

 12. cite maxruben:  Now close the project properties dialog with the OK button.

 13. cite maxruben:  Go into the project panel, expand the header files and open HardwareProfile.h. Scroll down to where it says:
"#if defined (YOUR_BOARD)...
Change YOUR_BOARD to CFG_INCLUDE_C18_ENC28 and the following line to #include "Configs/HWP_C18_ENC28.h"

 14. cite maxruben: Open the HW Config folder in the project pane, right click it and select Add Existing Item... in the context menu that opens. Select the HWP_C18_ENC28.h file. Now you should also exclude this file for all other project configurations. You have to change to all other build configurations (with the drop down list), right click the file, select properties and check the Exclude from build checkbox.

 15. cite maxruben: Open your hardware profile header file (HWP_C18_ENC28.h). Somewhere at the top there is a macro definition for the hardware setup. Change this to something for your hardware, PIC18_MYBOARD for example. Now you have to change all hardware definitions and #pragma config settings to match your hardware. Use the PIC18_MYBOARD in the main.c file to add code that is only used for your hardware.

 16. cite maxruben: Open the TCPIPConfig.h file. Add a #if defined(CFG_INCLUDE_C18_ENC28) and in the row following that: #include "Configs/TCPIP_C18_ENC28.h" and change the #if to #elif in the following row.

 17. cite maxruben: Open TCPIP Config folder under Header Files in the project panel and add the TCPIP C18 ENC28.h file to the project and exclude it from all other build configurations.

 18. cite maxruben: Open the TCPIP_C18_ENC28.h file and change it for your TCPIP requirements.

 Is posible simulated this in Proteus using WinPcap_4_1_3 (no work for me in Windows 10). 