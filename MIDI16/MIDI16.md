[Back](../README.md)

# MIDI16

A MidiFighter inspired midi controller made with arduino.

---

## TO DO

- [x] Prepare multiplexer
- [x] Learn screen
- [ ] Plan menus UML
- [ ] Plan playing modes
  
## Image Showcase

### AllView

![AllView](/MIDI16/all.png)
---

### TopView

![TopView](/MIDI16/TopView.jpg)
---

### FrontView

![FrontView](/MIDI16/FrontView.jpg)
---

### InsideView

![InsideView](/MIDI16/InsideView.jpg)
---

### InsideCloseUp

![InsideCloseUp](/MIDI16/InsideCloseUp.jpg)

---

## Pin Table

| Arduino | Multiplexer | Jack  | Switch | Screen | Encoder |
| ------- | ----------- | ----- | ------ | ------ | ------- |
| 2       |             |       |        | SDA    |         |
| 3       |             |       |        | SCK    |         |
| 4       |             |       | R      |        |         |
| 5       |             |       | L      |        |         |
| 6       |             |       |        |        |         |
| 7       |             |       |        |        |         |
| 8       |             |       |        |        |         |
| 9       | Sig         |       |        |        |         |
| 10      | S3          |       |        |        |         |
| 16      | S2          |       |        |        |         |
| 14      | S1          |       |        |        |         |
| 15      | S0          |       |        |        |         |
| A0      |             | Point |        |        |         |
| A1      |             |       |        |        |         |
| A2      |             |       |        |        |         |
| A3      |             |       |        |        |         |

## Button Mapping
![Button Mapping](/MIDI16/Button_Mapping.png)

## Menu Diagram

![Menu Diagram](/MIDI16/Menu_Diagram.png)
