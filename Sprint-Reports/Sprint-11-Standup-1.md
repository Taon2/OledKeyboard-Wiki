## 4/14/2023

**Software Progress**
The Software team worked on several things this week. USB COM serial communication was found to have a persistent issue that prevented us from transferring information between the PC and Pi consistently. Work is being done to convert this to using a TCP Socket. The Software team also worked on general system health, both part of PBIs and not part of PBIs

**Hardware Progress**
The Hardware team worked on the keycap design and the power output analysis from the USB and through an external source. 
___
### Jaden Rogel
Hours: 5
Self Rating: 4
### Worked on:
- Altering keycap design
- Printing keycaps
- Had to wait for PCBs to arrive and now have started to assemble them.
- Worked on the poster as a group

___

### Zach Kangas
Hours: 6
Self Rating: 6
#### Worked on:
- Minor non-PBI related changes to improve backend
- Async config save setup, no longer blocks UI when being called
- Currently has potential to cause concurrency issues
- Worked on the poster as a group

___

### Noah Stiemke
Hours: 7
Self Rating: 6 
#### Work Done: 
- Merge request resolution
- Started #1378
- Worked on the poster as a group

___
### Muize Rahman 
Hours: 4
Self Rating: 5
#### Worked on:
- Power analysis: output form a USB was compared to what was needed to power the system as a whole.
- Worked on the poster as a group

___
### Christian Doughty
Hours: 14
Self Rating: 10
#### Worked on: 
- Ran into a very persistent issue with USB COM that prevents us from sending images to the pi
- Began working to convert away from USB COM and use a TCP Socket instead. I have code prepared for this to work on over the weekend and next week. Communication between the Pi and PC through this method will be completed next week.
- Worked on the poster as a group
