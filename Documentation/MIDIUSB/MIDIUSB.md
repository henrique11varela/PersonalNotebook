# MIDIUSB

[Back](../Documentation.md)

This is a library to send and recieve MIDI information through usb.  

[MIDIUSB - Reference](https://www.arduino.cc/reference/en/libraries/midiusb/)

Each midiEventPacket is a struct with 4 parameters that must be instantiated:

```cpp
    midiEventPacket_t instanceName = {note on/off, note on/off | channel, pitch, velocity};
```

> - First parameter is the event type  
> (0x09 = note on, 0x08 = note off, 0x0B = control change).  
> - Second parameter is note-on/note-off, combined with the channel  
> (0x90 = note on, 0x80 = note off, 0xB0 = control change).  
> - Channel can be anything between 0-15. Typically reported to the user as 1-16.  
> - Third parameter is the note number  
> notes: (48 = middle C).  
> control change: (0-119).
> - Fourth parameter is the velocity  
> notes: (64 = normal, 127 = fastest).  
> control change (0-127).

Reading MIDI signal

```cpp
MidiUSB.read();
```

> This reads a MIDI signal and returns a *midiEventPacket_t*.
>

Sending MIDI signal

```cpp
MidiUSB.sendMIDI(midiEventPacket_t note);
```

> This sends the MIDI signal with the *note* data

Forcing signal transmition

```cpp
MidiUSB.flush();
```

> This flushes all the unsent messages by sending them.

---

This is an example of *noteOn*, *noteOff* and *controlChange* functions, instantiating and sending the midi information.

```cpp
void noteOn(byte channel, byte pitch, byte velocity) {
  midiEventPacket_t noteOn = {0x09, 0x90 | channel, pitch, velocity};
  MidiUSB.sendMIDI(noteOn);
}

void noteOff(byte channel, byte pitch, byte velocity) {
  midiEventPacket_t noteOff = {0x08, 0x80 | channel, pitch, velocity};
  MidiUSB.sendMIDI(noteOff);
}

void controlChange(byte channel, byte control, byte value) {
  midiEventPacket_t event = {0x0B, 0xB0 | channel, control, value};
  MidiUSB.sendMIDI(event);
}
```
