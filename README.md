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
The risk is real! Mains voltage is not a joke!<br>
Some of you guys already learnt it with a burnt down power connector/switch.<br>


So, what are we gonna do about it?

I'm going to show you a way how you can wire your printer safely to enjoy eons of print time, but since you guys come from all over the world I can't go into all details of your local regulations.
What I can give you is a guideline on how to do it as safe as possible and where you have to pay attention.
Who am I that I can give you such information? I'm an electrical engineer working in industrial environment (oil&gas).

I'm NOT responsible for your actions! If you have absolutely no idea of what is going on, then please consult someone who speaks mains voltage fluently!<br><br>
I simplyfied some formulas to make it not too confusing, so please don't come to me "ohh, you forgot the power-factor" or so. But then you won't need my help anyway ;-)

# SAFETY!
First of all, there are the 5 golden rules for electrical safety you should obey when working with mains voltage.

1) ALWAYS unplug your device before working on any mains voltage related part!
2) Ensure no one can replug it or turn the voltage back on.
3) Check if voltage is really off.
4) Ground the installation ... not applicable in our case
5) Confine the working area ... not applicable in our case

I'll add another rule:

6) If you can't do it safe, don't do it at all!

Getting electrocuted is a serious thread, and even if it "bites" you and you feel fine right after, a cardiac arrhythmia can show up to 24h later!
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
You sum up the heatbed, a space heater if you fancy an enclosure, the PSU and maybe an additional second PSU for your Raspberry PI.
Typical values are: 250W for a PSU, and 650W (like for a VCore3-300) to 1500W (like a VCore3-500) for the heatbed, 400W space heater,...
<br><br>
Higher voltage means less current, lower voltage means higher current.
<br><br>
My VCore3-300 will therefore have a maximum power consumption of around 900W at 230V.<br>

Dividing the power through the voltage gives you the amps. In my case: 900W/230V = ~4.2A

Connecting a VCore3-500 to 110V will result in 1750W/110V= ~16A!
Your normal power outlet won't support that!

## Get the power to the printer

### The cable
If your maximum current is below 10A you can use a C13 cable. (like for a normal PC)<br>
If your maximum current is between 10A and 16A you have to go for a C19 cable.<br>
<b>Warning:</b> Don't overrun the cable/connector or otherwise you risk a burning cable/connector!<br>
If you need more than 16A you either need to split the load or consult a professional to help you out.<br><br>

Get two of those cables, because we are gonna cut and strip one of them for the wiring on the printer.<br><br>
Here you can see the difference between the connectors.<br>
![C13-C19](https://user-images.githubusercontent.com/98351572/172686941-9025ef9e-7612-464f-ac4a-17ee5e3df9fd.png)<br>

### The connector

Accordingly to you cable, you need C14 or C20 connector.<br>
There are many all-in-one solutions on the market, especially cheap ones.<br>
I do NOT reccomend buying one of these for some reasons.<br>
<b>First:</b> often the connector is rated correctly at 10A, but the switch can only manage 5 to 6A.<br>
This is the most common mistake. Overrunning the current will cause a burned down switch causing a fire hazard!<br>
<b>Second:</b> the switch is to 99% a 1pole switch and we don't want this one on an open device like our printer!<br>
This is a more hidden flaw often overseen. The problem is the following: In many countries, there is no regulation of wether the phase is on the left or on the right side of the power outlet. So you never know, if your 1pole switch is really cutting the phase and not the neutral wire. This means you think you turned off you printer and easily can mess around with the wiring. There could still be mains voltage on it! This brings me back to my first rule: Always unplug the printer before working on the wiring!<br>
Nevertheless, it is always adviceable to have a 2pole switch to cut phase and neutral.<br>
<b>Third:</b> Is not that much of a problem, but normally there is only 1 fuse inside. You can go for a single fuse, but if you can get you hands on one with 2 fuses for almost the same price, than go for it.<br><br>
Those cheap all-in-one devices should only be used, if ALL mains voltage parts are consealed within an isolating casing! Since our printers have a mains powered heatbed, this is not an option!<br>
However, there are a few high priced options which combine all needed features and even add a filter. But they cost 25 to 50 bucks. Nothing you will find on Ali.<br><br>
![connectors-switch](https://user-images.githubusercontent.com/98351572/172691900-a946d6f4-73c4-4e63-bac9-3af48b9e2023.png)<br><br>
Make sure the connector, the switch and if you fancy the filter (recommended) are rated for your maximum current. Some filters can only take 1 or 4A.

### The fuse

My example printer from above has a maximum current of 4.2A, so I take about the next size of fuse, which is 6A (slow-blow or medium-slow-blow).<br>
You got 8 to 9A, you take a 10A fuse.<br>
If you need anything above its likely, that your miniature circuit breaker in your fusebox will blow first.<br><br>

### Terminals of the items above

Make sure your items all have the same terminal connector, so you only have to buy a single set of cable shoes.<br>
Best way are the 6.3mm flat connectors.<br>
![Flachstecker](https://user-images.githubusercontent.com/98351572/172694695-a6d2c2ea-8162-457a-99a0-ef8db383a4d5.PNG)<br><br>
Buy some isolated crimp connectors and the fitting tool. You probably already know those from your local hardware store.<br>
![Flachsteckerhülse](https://user-images.githubusercontent.com/98351572/172697080-6881d7d3-22e0-4f6e-b61d-ba2aed932da2.PNG)<br>
The right ones will be used to connect the PSU.<br><br>

