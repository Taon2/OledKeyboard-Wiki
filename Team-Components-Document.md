______
[[_TOC_]]
From: https://csse.msoe.us/srdsgn/grading/
______
# Team Components
May 19th 2023 

OLED Keyboard Team:
- Christian Doughty
- Zachary Kangas
- Muize Rahman
- Jaden Rogel
- Noah Stiemke

Advisors:
Dr. Walter Schilling and Dr. Sohum Sohoni

# Requirements 
- Definition and analysis including selecting at least one stakeholder. You will need to become familiar with the domain.

We needed to design our system, which required a lot of research and development, within the school year limit confines. To some respect, we were succesfull, however much more could be expanded on in this project given we follow through past our schooling with it.

###Major Features Requirements of the companion software.
- Users will be able to create/delete layouts (or presets) that can be applied to the keyboard and will adjust the way it looks.
- User have the ability to customize these layouts.
- Layouts will be persisted on the local machine storage and will be reloaded into the program upon launch.
- A default loadout will be applied to keyboard when no layout is selected or when the program is unavailable.
###Major Features Requirements for C Programming Controlling the Hardware
- Applies the pictures included in the layout, received from the companion software, to the OLED screens.
- Defaults to default layout when no other layout is provided by the companion software.
- Relay key presses from hardware back to the companion software.
### Stakeholder: Keyboard Owner/User
* Our biggest stakeholder is the purchaser/user of the OLED keyboard, all features and qualities of our software and hardware had to be designed with them in mind. 
* This stakeholder can be broken down into categories of how they plan on using the keyboard. 
  * Users who want to use this program to allow them to type multiple in languages that have different alphabets or characters using the same keyboard, saving them the hassle of buying multiple keyboards.
  * Users who would like to use the customizable screens for gaming purposes, such as assigning pictures of abilities to the various screens on the keyboard.
  * Other users who just want greater customization control over their keyboard.


#Software Architecture and Modeling 
 - It should involve some interesting elements of software system design, including thoughtful exploration of the architecture to support iterations.

The frontend and the application side of our system is entriely done in C#. The reasons for this is that it was similar to a technology we had already used, Java, but had a little better support for more low-level functions than java. The communication with the keyboard itself was done through a TCP connection over a serial COM port. This was done mostly because it was the easiest and safest option. On the Pi we used C++, which was cross-compiled with WSL-2, to run the program on the keypad itself. The reason we chose C++ was for it's light footprint and low level abstractions.
 

# Design 
- Strategies employed, such as the use of patterns and allowances for evolution of the product.

Much of our design was setup during the inception phase of the project to attempt to maintain good practices, while not letting excessive red-tape to change and improve the program we were developing. We maintained throughout the project that we would require at least one approval when making changes on the software side, which allowed us to have high quality code while still being able to quickly make improvements and changes. We attempted to split all the information on the frontend from the information on the backend of the software, which would allow, should we have had the time, to make a Linux or Mac distribution of the final software product.

## More needs to be added here

# Testing 
- Building it to be testable and testing it. How good is the automation of the testing and was it considered from the beginning?

Much of the testing we performed was on the frontend, and as the project got more complex, we did not sufficiently update our initial automated tests. We did build the program to be testable, with mock databridges using good practices of dependency injection (DI), along with splitting up the showing of the data from the actual data. This approach may have impacted the quality of the code as we had relatively low test coverage, it promoted good design practices and testable interfacing between each layer of the application.

Adding automated integration tests and end-to-end tests would have allowed us to catch certain bugs that we ended up having to manually fix down the line due to our low test coverage.

However, we did perform a lot of manual testing, especially when it came to the hardware and software integrations. The end-to-end tests performed on the live hardware were extremely important to making sure the final product ran as intended.


# Security and Privacy 
- How are you addressing security and privacy? Are you using best practices?

Only one security aspect of our program can be considered unsecure. When typing on the physical keyboard, a TCP packet is sent from the Pi Application to the PC Application with the keypress. This is then enacted in the PC Application. To ensure the security of this functionality, we do not store the keypress anywhere after it is enacted. Therefore, we are not “keylogging” any of the keystrokes entered. 

No other parts of the project have security or privacy concerns. As this project is not connected to the internet, there is no risk of outside threats to our application. 

 

#Tools 
- Good use of development, testing, and management tools (including GitLab).

Using Azure, we enforced a structure for our repos and branches. We set up a Dev branch to ensure that the integrity of the main branch was maintained. All development branches from dev follow the naming scheme of PBINUMBER-DESCRIPTION. This allowed the developers to easily understand which task was being completed in which branch.  

Merge requests always required the review of one additional developer. Merge requests from Dev into Main requires the review of all developers. This ensured that all code was being evaluated by more than just the writer. Outside eyes on code can spot glaring issues which could have caused problems in the future. 

 

# Experimentation and Prototyping 
- Applied to unknown technology to improve knowledge and reduce risks. As the architecture is developed and key mechanisms are determined, what risks arise and how will you address them in the development process?
 
The biggest risk we expected to encounter was trying to link together our 2 systems, the layout software/companion app, and the software which controls the keyboard and OLED screens, this is because they will be quite difficult to test until we had working version of the hardware. We intend to address this risk by testing with our various prototype versions of the keyboard until the final version is completed.

Another concern of this project was having to create drivers for the keyboard as none of our team members have experience with process of creating new ones from scratch. We found a way to neutralize this risk by using a different method, simulating key presses using the desktop software after the hardware relays which key has been pressed.
 

# Third Party Components 
- Demonstrate your skill in discovering and employing third party components.

We used multiple technologies we did not create. Windows Presentation Foundation (WPF) was the main UI frontend we used. We used multiple libraries within the Windows application including Aspose and some windows libraries to interact with windows for information retrieval and sending. We used PIGPIO and wiringPi for various GPIO operations on the Raspberry Pi. We used WSL-2 and a specific cross-compiler toolchain to cross compile for the Pi.

Our PCB boards were designed by our team, but were sourced from a different company.

# Documentation 
- This takes many forms including continuous documentation such as, notes associated with tasks that our updated regularly, weekly reviews, sprint reviews, and other artifacts such as a technology report, discussions of where you achieved specific course outcomes, project presentations, poster, and final report.

There are many examples of documentation for this project. From sprint retros to planning, to inception phase documents, to developer or user facing documentation, we extensively documented each step of the process. At the beginning of the project we used almost exclusively MS Teams. As we worked more on the project, more documents ended up on the Wiki instead. Linked below is a representative sample of some of our documentation

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

# Managing Risks 
- Strategies employed to manage risk.

The biggests risks to the project were hardware related. This comes from multiple sources, but the largest of which were: obtaining componants, breaking componants, and then physical limitations regarding location of parts or power management.

To the first two risks, we made sure to order componants in bundles larger than one, and much before we actually needed them. However, at certain times we could not feasibly do that, such as when we bought the Raspberry Pi or the PCB boards. One of the ways we mitigated those cases is having alternatives able to be used.

Our project used a Raspberry Pi Zero 2 W. However, we were only able to obtain one of these. As an alternative, we decided to rent out MSOE Raspberry Pi's so that we could have a development environment to work and test on without having the Pi Zero 2 W that we intended to use on our final prototype.

Another risk was power consumption. In our inception phase we were worried about the total power consumption of the system. We did two major things to eliminate this risk, the first was downsizing the project as a whole, which was for multiple reasons, and the second was to calculate power need so we knew what we had to work with, and what we had spare. We even created potential designs which included battery packs, so if our initial calculations were incorrect, we could have a fallback.


# Standards Used 
- Identify industry standards used in the project.

On the software side, we employed good use of dependency injection (DI) to make our program modular and testable. We also employed good practices of CI/CD in some very basic ways. Our codebase was locked down by requiring multiple developers to approve a change before it went to dev or master, which made sure other developers knew changes occuring and the final code was of high quality.