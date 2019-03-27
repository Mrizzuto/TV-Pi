# RETRO TELEVISION GRAPHICS PROJECT

Not too long ago I sourced a 36 year old Zenith travel television from a Goodwill in Journal Square. I plugged it in at the store and bought it after the screen sprung to life with static. The idea: return the analog television to its former glory. I didn’t want the TV to be a focal point in whatever space I put it in, rather I liked the idea of it being a peripheral, like a painting – a novelty item that speaks for itself and doesn’t interfere with conversation, contrary to a television's traditional effect on a space. It would be mute and autonomous, doing its own thing.
 
In the name of keeping it retro and relatively smooth running, lightweight processing sketches would be projected on the screen. With simplicity, the final product could remain casual and the visuals could stay engaging longer before getting old - not to mention operate within the humble Pi's (...) hardware limitations. So that's what I did.
  
![Sort of a Tesseract](http://i.imgur.com/387aQe2.jpg)
One of my favorite sketches running, this I feel embodies what the project is all about. 


# DESCRIPTION
At this time, the television operates as intended. A singular power supply provides power for the entire unit and all of its components, the case remains unmodified at this time with the exception of a small piece of plastic cut away to accommodate the auxiliary antenna input. Upon being plugged in, the Raspberry Pi boots and the tube spring to life. After the Pi completes all of its necessary start-up procedures it auto-starts a bash script that selects one of the 10 sketches and executes it. The sketches are all very simple, white on black, and optimized for the Pi and the television screen. Between sketches, the Pi shows an undecorated terminal window that prints information on the current sketch. Without some serious hacking, the Raspberry Pi Zero lacks any audio output, this is fine because the television was never intended to be a focal point. So at this time, the television is mute... sort of, some of the sketches create (what I surmise to be) ambient interference with the RF modulator and generate some eerie sounds. Not explicitly my intention but an interesting outcome nevertheless. At this time, the television operates without almost any user input, which I consider a relative success. Below are some pictures of the television running. 

![A Solid Sketch](http://i.imgur.com/eIXJeWU.jpg)
This is one of the optimized sketches. Previous iterations revolved around Sin and Cos functions, but they proved to be a bit too labor intensive for the small processor. I really like how this sketch looks on the screen.

![the screen between sketches](http://i.imgur.com/uRicO5k.jpg)
In between sketches, there is a small message echoed in an undecorated terminal window that displays the sketch number, this is what it looks like. 


 
# TECHNICAL NEEDS
At the back of the television there are posts for an “ANT INPUT” which was my way in, I used a "Compact RF Modulator" ($6.00 off amazon) to convert the Pi's composite video output to a radio frequency and then, connected the antenna cable to the television's auxiliary antenna nodes. The RF Modulator said to have needed 9 volts to operate, while the Pi Zero needed 5 volts, and the television demanded 12 volts. I figured I could get away with running the RF Modulator on 5 volts so I got a 3 amp power converter (I know, 3 amp) and soldered it straight to the television's board. I knew that I would need a new power supply so I bought one off amazon and planned to solder the television's existing power cable plug to the new power cord... but the one I bought fit just perfectly out of the box so that's cool. The RF Modulator worked just fine running on a lower voltage and although the circuitry wasn't ideal, it worked as planned. I had a good time worrying about the unit shorting and catching fire so I taped up all the possible culprits and fashioned some dividers for the RF Modulator and the Pi for the back of the box.

Below are some poorly screenshot images of the RF Modulator and the smaller components I had to pick up to get the signal to the TV, as well as a primitive wiring diagram for how all of the components will connect.

![](http://i.imgur.com/i0ECIHK.png)
![](http://i.imgur.com/EO5aWxP.png)
![](http://i.imgur.com/EsT9YwK.png)

This diagram includes an audio input, I had originally planned to integrate some sort of audio and using a "Phat Dac" (a Dac board for the Pi Zero) I could get 3.5mm out. This was scrapped for design reasons and time restraints.  

As for software needs, <s>I plan on using python as I already know a thing or two about it, and it would be a hell of a lot easier coding it on my laptop rather than on the Pi’s Linux terminal.</s> Although Python would have been a hell of a lot easier, I decided to torture myself and coded the Bash script on the television its self, why you ask? I have no idea. After teaching myself a little bit of bash I set about making the code. I'm not going to go into specifics about the sketches as they are fairly rudimentary. I will, however, share that there was far more hacking that I had previously imagined to get the Pi to auto-start my script. After scouring the internet I figured it out but it wasn't easy. Furthermore, I had to hide the mouse, which on startup is by default in the center of the screen. I found some config files to move it off screen which was nice. I also had to manually dial in the screen resolution, which was a pain and required countless restarts all in order to get the GUI to be hidden out of sight. I considered booting i3 (a tiled window manager) onto the Pi and forgoing a GUI altogether, but I figured it was more trouble than it was worth. I had to go into the LXDE config files to change the text and window colors to black as to appear invisible -- it's safe to say that right now I am the only person who knows how to navigate the computer because all of the menus are present, yet hidden. There was a lot of spam clicking throughout the duration of the build looking for buttons hidden off screen, or menus that needed to be dragged to be readable. I also had to keep the screen from falling asleep, this proved to be relatively simple.

Below are some pictures of the project in the works...
![back of the televion](http://i.imgur.com/vhsNegp.jpg)
Just a picture of the guts of the television, all of these components fit not so nicely in the back of the box. The repurposed battery compartment is something I think is really neat.
![~./config | grep "please work"](http://i.imgur.com/zRF69jO.jpg)
I was up late finalizing the sketches and system config, just a picture of what it looks like working on the television.
![Bash Code in Notepad++](http://i.imgur.com/KQpfPW5.jpg)
Just a screen cap of the bash code, it is pretty plain and simple. 
It sets the sketch to run "choice" to a random number 1 - 10 and echos the selection into the terminal and waits 150 seconds until terminating the script (150 seconds being the time I decided that each sketch should run).
A while loop calls the code and clears the screen. 
The TODO that I never got around to would have made it really easy for me to test the code on my Antegros partition but once I got it working I was too exhausted to even consider accommodating different operating systems.

# WHY?
Much of my interest in this project started with my interest in vintage technology at large, however it became a real possibility the moment I saw the CRT television in Goodwill. I really like the idea of giving the vintage tech new life. With no means of playing video as ‘they’ stopped broadcasting over the air years ago, I find myself with a fully functional piece of kit that has out lived the infrastructure that supported it. This of course saddened me, so I thought up a way to revive the old television. I like idea of the static and the glitches and the cheap vintage plastics, I like the idea of it being appreciated for what it was and what it continues to be. I like the form factor and space it takes up, and I really like the idea of it taking on a new role in a space, no longer as a means of viewing content, but as a holistic ‘piece’ unto its self – a medium that is just as much the subject as the media it plays. I like the idea of the television taking the place of a painting, or a statue - silently contributing to the space, a topic of conversation.

At the end of the day, I think my vision has been imagined. However I do not believe it is finished, there is still plenty more that I can do to refine and fine tune the television in the future, maybe make use of the GPIO pins on the Pi Zero. 

# ANYTHING ELSE
Using the Pi Zero to any capacity is really a chore. It's slow, as you would imagine, but it's also lacking enough power from its USB port (singular) to accept my USB Mouse without sapping itself dry of power and shutting down. The same happened when I tried to plug in a USB hub. After scouring around and borrowing some peripherals from some friends, I managed to get a working keyboard and mouse. 

In the future, if I do decide to add audio this is how Im going to do it. Rather than using a dac, this USB to 3.5mm audio jack could work nicely. I would need to solder straight onto the usb terminals to save space.
![USB to 3.5mm](http://i.imgur.com/GM9wm0k.jpg)
