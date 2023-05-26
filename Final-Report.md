[[_TOC_]]
https://csse.msoe.us/srdsgn/finalreport/
___________________________________________
# Project Information
## OLED Keyboard Team
- Christian Doughty
- Zachary Kangas
- Muize Rahman
- Jaden Rogel
- Noah Stiemke
## Advisors
Dr. Walter Schilling and Dr. Sohum Sohoni
##Sponsor
Erik Krippaehne of Pac-imd

# Executive Summary
The project at it's core was an attempt to create a new kind of keyboard that uses OLED screens on the keycaps of a mechanical keyboard, as well as a software program to accompany the keyboard. 

We utilized many technologies to achieve this goal, including but not limited to circuit design, Microsoft Windows interfacing, various programming languages, raspberry pi's, along with various requirements to get the Raspberry Pi active.

We were able to accomplish _____ during the time on the project. While our initial goal was an entire keyboard, between physical and electrical limitations, cost requirements, and time limitations, we were only able to produce a numpad. During the time on the project, each member of the team used and learned new skills, using new technologies and extensive amounts of research and testing to get each component to work.



# Project Summary
This should show pictures, and potentially other stuff on an overview of the project


## Plan Summary
### Total time by each team member
- Christian Doughty: 140~ Hours
- Zachary Kangas: 140~ Hours
- Muize Rahman: 142~ Hours
- Jaden Rogel: 130~ Hours
- Noah Stiemke: 155~ hours

### List of competed PBIS by sprint
[Sprints Report Wiki Page](https://dev.azure.com/MSOE2022SeniorDesignProjects/OLED_Keyboard/_wiki/wikis/OLED_Keyboard.wiki/425/Sprints-Report)

# Documentation
## Design
Much of our design was setup during the inception phase of the project to attempt to maintain good practices, while not letting excessive red-tape to change and improve the program we were developing. We maintained throughout the project that we would require at least one approval when making changes on the software side, which allowed us to have high quality code while still being able to quickly make improvements and changes. We attempted to split all the information on the frontend from the information on the backend of the software, which would allow, should we have had the time, to make a Linux or Mac distribution of the final software product.

We decided on C# for the frontend, which has great testing libraries, great UI, and cross-platform support. The reason for C# over Java was because C# could more easily interface with drivers, which ended up being useful for the later stages of the project when we made some design decisions regarding the user inputs. We decided on C++ for the backend because of familiarity versus Rust along with the prior knowledge of how to handle hardware I/O with C++ interfacing.

## Testing
Much of the testing we performed was on the frontend, and as the project got more complex, we did not sufficiently update many of our initial tests. We did build the program to be testable, with mock databridges using good practices of dependency injection (DI), along with splitting up the showing of the data from the actual data. This approach may have impacted the quality of the code as we had relatively low test coverage, it promoted good design practices and testable interfacing between each layer of the application.

## Tools
During the project, we used quite a few tools to plan, design, and implement our solution.

For the planning, we mainly used Microsoft Teams and Microsoft Word. We used Azure DepOps for our repository, documentation, and storage location for project backlog items (PBIs). During the implementation, we used various technologies including JetBrains CLion, JetBrains Rider, Visual Studio 2019, and Windows Subsystem for Linux 2 (WSL-2).

Hardware tools that were used for design include various software and tools. Multi-Sim was used to design circuitry and the keyboard matrix. Kicad was used to design the PCB. 3D printers were used to make the enclosure and the protective covers for the OLED screens. Additional tools were used for troubleshooting hardware, such as analog discovery kits and digital multimeters. 

## Architecture
### Software Design
The software has two components. The main computer-side software is a Windows Presentation Foundation (WPF) program coded in C#. It uses the DOTNET 6.0 runtime to execute. The purpose of the frontend is to provide a visual interface for interacting with the OLED screens at various levels. The frontend links to a C# backend that attempts to store, transform, and send the information. In this backend, we have various functions to allow sending and receiving information from the Raspberry Pi, along with permanent local storage that can be transferred between computers if necessary.

Included in this information sent between the Pi and the Windows application is the information about when a specific key was pressed. This key-press information is handled within the C# program by sending a message to a Windows driver that the specific key was pressed. This is strictly different from most keyboards, which use a driver to send and receive that information.

On the Raspberry Pi, we have a program that performs two main actions. This program was coded in C++ and was cross-compiled using WSL-2 onto the ARM architecture of the Raspberry Pi. The first action is the communication with Windows. The Pi program communicates with the C# program on the Windows machine about which key is pressed at any given moment. On the split side, it receives information regarding what the user of the keyboard wishes to show on each individual OLED.

The second main function is to handle the information from the mechanical switches, and handle changing and altering the information to the OLEDs on each key. The Pi program handles keypresses from the mechanical keyboard switches, decoding the information provided by the hardware into a usable format for the software on Windows. The second main function is handling the various inputs necessary to change, modify, and alter the individual OLEDs to get the desired image to appear on the screen.

### Hardware Design 
The hardware design was focused on producing the number pad itself. This included the integration of the OLEDs, switches, and diodes onto a PCB. There were steps leading up to the final PCB, which was designed using Kicad. The switches were first tested on a breadboard to insure that an input could be received from the switches to the software, and thus to other programs and software. Power distribution was analyzed, and it was determined that an external power source was not necessary, specifically because of how little power (less than 0.05 Watts) is needed to operate the OLED screen. 

A microcontroller needed to be selected for the design as well. There were several specifications that needed to be followed, such as clock speed, serial peripheral interface, availability of GPIO pins, embedded C integration, and an amount of internal memory. The micro controller that was initially chosen was the MSP-430FR2355 by Texas Instruments. However, there were concerns as far as the capabilities of this micro controller, so the team decided to make a swap to a Raspberry Pi Zero 2 W. The main reasons for the change was because the Pi has a higher clock speed, and the team had more experience working with this type of micro controller. 

Hardware tools that were used for design include various software and tools. Multi-Sim was used to design circuitry and the keyboard matrix. Kicad was used to design the PCB. 3D printers were used to make the enclosure and the protective covers for the OLED screens. Additional tools were used for troubleshooting hardware, such as analog discovery kits. 



## Third-Party Components
We used multiple technologies we did not create. Windows Presentation Foundation (WPF) was the main UI frontend we used. We used multiple libraries within the Windows application including Aspose and some windows libraries to interact with windows for information retrieval and sending. We used PIGPIO and wiringPi for various GPIO operations on the Raspberry Pi. We used WSL-2 and a specific cross-compiler toolchain to cross compile for the Pi. 

## Documentation
### Representative Samples
#### Sprint Retrospectives and Planning: 
[Sprint 9 Retro](https://dev.azure.com/MSOE2022SeniorDesignProjects/OLED_Keyboard/_wiki/wikis/OLED_Keyboard.wiki/317/Sprint-9-Retro)
[Sprint 11 Planning](https://dev.azure.com/MSOE2022SeniorDesignProjects/OLED_Keyboard/_wiki/wikis/OLED_Keyboard.wiki/363/Sprint-11-Planning)
#### PBI Completion Crtieria
#1383
#### Meeting minutes
[Sprint 9 Standup 2](https://dev.azure.com/MSOE2022SeniorDesignProjects/OLED_Keyboard/_wiki/wikis/OLED_Keyboard.wiki/316/Sprint-9-Standup-2)
#### Code reviews / Pull requests:
[Add help tooltips and about page branch into dev](https://dev.azure.com/MSOE2022SeniorDesignProjects/OLED_Keyboard/_git/OLED_Keyboard/pullrequest/290)

#### Project Presentations
[Presentation](https://dev.azure.com/MSOE2022SeniorDesignProjects/OLED_Keyboard/_wiki/wikis/OLED_Keyboard.wiki/430/Presentation)
#### Project Poster
[Poster](https://dev.azure.com/MSOE2022SeniorDesignProjects/OLED_Keyboard/_wiki/wikis/OLED_Keyboard.wiki/428/Poster)
#### User-Facing Documentation
[Instructions](https://dev.azure.com/MSOE2022SeniorDesignProjects/OLED_Keyboard/_wiki/wikis/OLED_Keyboard.wiki/432/Program-Instructions)

#### Developer-Facing Documentation
[Pi Zero Cross Compiling Intro](https://dev.azure.com/MSOE2022SeniorDesignProjects/OLED_Keyboard/_wiki/wikis/OLED_Keyboard.wiki/171/Pi-Zero-Cross-Compiling-Intro)
[Pi Zero W Serial and Ethernet Info](https://dev.azure.com/MSOE2022SeniorDesignProjects/OLED_Keyboard/_wiki/wikis/OLED_Keyboard.wiki/348/Pi-Zero-W-Serial-and-Ethernet-Info)

### Datasheets: 
[OLED](https://www.buydisplay.com/download/manual/ER-OLED0.60-1C_Datasheet.pdf)
[ZIF Connector](https://www.buydisplay.com/download/connector/ER-CON20HT-1.pdf)
[MX Switches](https://cdn.sparkfun.com/datasheets/Components/Switches/MX%20Series.pdf)
[1N4148 Diodes](https://us.rs-online.com/m/d/a8484ddbc7ecbdc5c10b6858ac480b07.pdf)
[Raspberry Pi Zero 2 W](https://datasheets.raspberrypi.com/rpizero2/raspberry-pi-zero-2-w-product-brief.pdf)
[MX Breakout Board](https://cdn.sparkfun.com/datasheets/BreakoutBoards/SparkFun-Cherry-MX-Switch-Breakout.pdf)




# Project Postmortem
The project we created used skills we developed during our time at MSOE to an extensive degree. Many of the technologies we had either rarely used, or have never used. In that way, we developed and used a significant amount of skill in learning new technologies then implementing it in a new context.

Our original concept was ambitious, and we still have those ambitions, but due to the extensive time used to R&D the new technologies, we were not able to get to that end goal. But the core of what we wanted to do with the keyboard never changed, and even though we changed and evolved, we still stayed true to the original goal.

The planning during the project was a mixed bag. We had a lot of PBIs that we thought were out of reach at first inception of the project, but our work went smooth and quick, so we ended the project up with even a lack of work on the software side. This time could have been devoted to connecting the hardware and software sides, but due to some of the slowness of the Hardware R&D, our software work got completed extremely quickly.

At various times, we had points of people not doing work. While we may have our own opinions as to why this happened, the way we fixed these periods was a short conversation at standup or teams, and individuals modifying their own work habits to better suit progress on the project.

Throughout our sprints, we spent time during retrospectives to find things we could improve upon. We found that we often left work for the weekends, meaning large amounts of development were happening at once. This slowed us down and left any potential problems for last minute, which was not ideal. We worked hard to spread the work more throughout the week. We also improved our communication as to when we were available to work in person and collaberate.
