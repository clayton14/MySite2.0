---
title: "Send Sound Through Your Circuit Designs"
date: 2026-01-06T14:29:39-05:00
draft: true
searchHidden: false
ShowToc: true
author: Clayton Easley
tags: 
    - References
    - LTspice
    - audio
    - filters
description: Notes on how to send .wav files through simulated analog circuits in LTspice
categories: ["Electronics", "Simulation"]


editPost:
    URL: https://github.com/clayton14/MySite2.0
    Text: "Suggest Changes"
---

Wheather your a student, professional, or hobbyist, you will eventually come across [SPICE Software](https://en.wikipedia.org/wiki/SPICE) when desigining electronics projects. SPICE software, such as [LTspice](https://www.analog.com/en/resources/design-tools-and-calculators/ltspice-simulator.html), can be used to simulate your analog and digital designs without having to bust out a breadboard or soldering iron.

One of LTspice features I have found incredibly usefull it's ability to process `.wav` files as a voltage input and the write the voltage output of the circuit to a new file. 


## Audio Settings

To process audio files in the .wav file format it is important to make sure the file is encoded corectly. The .wav file is a just a [Container](https://en.wikipedia.org/wiki/Container_format) for raw uncompressed [Pulse-code modulation (PCM)](https://en.wikipedia.org/wiki/Pulse-code_modulation) data. 

So when importing your audio files into LTspice make sure you take note of the <span style="color:red">**audio encoding**</span>, <span style="color:red">**bit rate**</span>, <span style="color:red">**sample rate**</span>, <span style="color:red">**audio duration**</span> and make sure the audio channel is <span style="color:red">**monophonic**</span> 

Most audio recording software have the option to export wavefiles in some n-bit PCM format.


{{< details summary="See Audacity Export Example" >}} 

--- 

Open a new Audacity project and navigate to `Tracks > Add New > Mono Track`. Click on the newly added track and then navigate to `Generate > Pluck` to make a guitar plucking sound.


Take note that Audacity uses the [MIDI pitch number](https://studiocode.dev/resources/midi-middle-c/) which is diffrent than the key number when generating the pluck sound.    

{{< figure src="/notes/audicty_wav_encoding_settings.webp">}}

{{< /details >}}

## LTspice Circuit

Once you have your audio file you want to use, I would recomend moveing it into the root directory where your LTspice project is located. Otherwise you will have to provide the **full path** to your audio file. 

Each componet in LTspice has a name and a value. To discern between the two hover over each tag and look in the bottem left corner of your screen. 

{{< details summary="See Example Low Pass Filter Schmatic" >}}

---
Here is a simple low pass filter example with a cut off frequency of 10061 Hz (CHECK) 
f_c = 1 / 2pi * RC ADD Latex 
{{< figure src="/notes/lowpass_schematic.webp">}}


{{< /details >}}

### Input

Right click the value of your voltage source and put the folowing in the empty text box.

~~~
wavefile=path/to/your_audio.wav
~~~

This voltage source will now serve as your audio input in your circuit.

### Simulation settings

The next step is going to be to set up a [transient analysis](https://ltwiki.org/LTspiceHelpXVII/LTspiceHelp/html/DotTran.htm) equal to the duration of your audio sample.

This can be done by adding the flowing directive by pressing `.` on your keyboard. You can also use the GUI by naviagiting to `Simulate > Configure Analysis` and edit your settings in the `Transient` tab.  

In my case my directive looks like the flowing but you may need to change the duration of analysis.
~~~
.tran 0 1s 0s 0.1s
~~~


### output

The next step is going to be to add the output newtork by pressing KEY on your keyboard. Keep note of the name of this node as it acts as a varable for the output data. In the example image this is **V_Out**

Once you have your circuits input, output and simulation settings configured we need to use the [.wave](https://ltwiki.org) directive to output your audio file the circuit.

~~~
.wave <output.wav> <bit rate> <sample rate> V(<output node>)
~~~

**Example** 

~~~
.wave pluck_out.wav 16 44100 V(V_Out)
~~~


|Original  | LTspice output|
|----------|---------------|
|<audio controls src="/notes/pluck.wav"></audio>|<audio controls src="/notes/pluck_out.wav"></audio>|
| {{< figure src="/notes/peak_fft.webp">}} | {{< figure src="/notes/peak_out_fft.webp">}}  


https://www.digikey.com/en/maker/tutorials/2024how-to-simulate-an-rc-low-pass-filter-in-ltspice-and-analyze-frequency-response

https://www.allaboutcircuits.com/technical-articles/understanding-transfer-functions-for-low-pass-filters/


