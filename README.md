# Mains power for the printer
An almost long guide on how you connect mains voltage to your printer the safe way. <br>

You came here because you need some specific information.<br>
Lets make a deal first!<br>
I give you the information you come for, but you promise to read everything and not jump anywhere and skip some very important advice.
It is essential because I'm not responsible for your actions and if someone gets hurt or you burn something down, YOU are in trouble!<br><br>
!! Working with mains voltage is normally a job for professionals because your life can depend on it !!


# Introduction
Wiring the 24VDC on your printer is mostly straight forward.
Getting something wrong results more or less in a blown fuse or an electronic part goes up in smoke.
Nothing that couldn't be fixed with a few bucks.

BUT

Wiring mains voltage is a complete other topic and errors could result in a burnt down house or an electrocuted/dead person, so this is a VERY serious topic!
If you don't find information about wiring mains voltage in the documentation/channels of your favorite brand like Voron, Ratrig,... you name it, it's because those guys can't be held responsible since you build the printer by yourself.
YOU are responsible to build your machine in a way it is safe to operate and no hazards result that could harm your family/friends/pets.<br>
The risk is real!<br>
Some of you guys already learnt it with a burnt down power connector/switch.<br>


So, what are we gonna do about it?

I'm going to show you a way how you can wire your printer safely to enjoy eons of print time, but since you guys come from all over the world I can't go into all details of your local regulations.
What I can give you is a guideline on how to do it as safe as possible and where you have to pay attention.
Who am I that I can give you such information? I'm an electrical engineer working in industrial environment (oil&gas).

I'm NOT responsible for your actions! If you have absolutely no idea of what is going on, then please consult someone who speaks mains voltage fluently!

# SAFETY!
First of all, there are the 5 golden rules for electrical safety you should obey when working with mains voltage.

1) ALWAYS unplug your device before working on any mains voltage related part!
2) Ensure no one can replug it or turn the voltage back on.
3) Check if voltage is really off.
4) Ground the installation ... not applicable in our case
5) Confine the working area ... not applicable in our case

I'll add another rule:

6) If you can't do it safe, don't do it at all!

Getting electrocuted is a serious thread, and even if it "bites you" and you feel fine right after, a cardiac arrhythmia can show up to 24h later!
So there is a chance you go to sleep, get an cardiac arrest and never wake up again.
Go and see a doctor!
<br>
# Enough talk
![enough-talk](https://user-images.githubusercontent.com/98351572/172455935-11f3f568-7cac-4458-9d8f-6c5202baf823.jpg)

# Lets start with some outlines

There are some key numbers for the project we need to clarify.
First of all is the mains voltage.
If you live in Europe you will certainly have 230V as a mains voltage. Other countries may have 110V (or 120V) or in some special cases in the USA even 240V. I assume you set the general voltage on the PSU accordingly to 110 or 230V, as well all other components are fitting as well (like the heatbed).
Second number you need is the maximum power consumption of your printer.
You sum up the heatbed, the PSU and maybe an additional PSU for your Raspberry PI.
Typical values are 250W for a PSU, and 650W (like for a VCore3 300) to 1500W (like a VCore 3 500).
<br><br>
Higher voltage means less current, lower voltage means higher current.
<br><br>
My VCore3-300 will therefore have a maximum power consumption of around 900W at 230V.<br>
Since electronics are not straigth forward, you need a special formula to calculate the maximum current.
![01_calcCurrent](https://user-images.githubusercontent.com/98351572/172469113-f9aa93c4-296a-4d89-8ff9-6b9ae922e3db.PNG)



morgen gehts weiter.... vielleicht...
