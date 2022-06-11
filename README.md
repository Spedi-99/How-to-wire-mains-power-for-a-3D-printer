<b><i> 
  - Do you want to electrify yourself on your printer?<br>
  - Do you want to melt down some cables and/or connectors mid printing?<br>
  - Or do you even want to burn down your house with your printer?
</b></i><br><br>

If your answer is no, then you might find my guide helpful.<br>
I'm an electrical engineer working in industrial areas for decades now, so I will show you a safe way how to wire mains voltage to your printer that you don't risk hurting someone or even start a fire.<br><br>

I know this isn't a short description, but this is a very serious topic and to be honest almost all of you wouldn't be legally allowed to wire this up. So if something bad happens, you could be in legal trouble. If you follow my guide, you should at least have the proper items that nothing goes up in smoke or hurts someone. (Tho you could still mess things up, so I'm not responsible for any of your actions)<br><br>

!! Working with mains voltage is a job for professionals because your life can depends on it !!<br>
So if you completely don't know what you are doing, I strongly advice you to consult professional help. Mains voltage is not a joke!<br><br>

I simplyfied some formulas to make it not too confusing, so please don't come to me "ohh, you forgot the power-factor" or something like that.

# SAFETY FIRST!
First of all, there are the 5 golden rules for electrical safety you should obey when working with mains voltage.

1) ALWAYS unplug your device before working on any mains voltage related part!
2) Ensure no one can replug it or turn the voltage back on.
3) Check if voltage is really off.
4) Ground the installation ... not applicable in our case
5) Confine the working area ... not applicable in our case

I'll add another rule:

6) If you can't do it safe, don't do it at all!

Getting electrified is a serious thread, and even if it "bites" you and you feel fine right after, a cardiac arrhythmia can show up to 24h later!
So there is a chance you go to sleep, get an cardiac arrest and never wake up again.
Go and see a doctor!
<br>
# Enough talk
![enough-talk](https://user-images.githubusercontent.com/98351572/172455935-11f3f568-7cac-4458-9d8f-6c5202baf823.jpg)

# Lets start with some outlines

There are some key numbers for the project we need to clarify.<br>
<b>Voltage</b><br>
If you live in Europe you will certainly have 230V as a mains voltage. Other countries may have 120V or in some special cases in the USA even 240V. I assume you set the general voltage on the PSU accordingly to 120 or 230V, and all other components are fitting as well (like the heatbed).
Second number you need is the maximum power consumption of your printer.<br><br>
<b>Power</b><br>
You sum up the heatbed, a space heater if you fancy an enclosure, the PSU and maybe an additional second PSU for your Raspberry PI.
Typical values are: 250W for a PSU, and 650W (like for a VCore3-300) to 1500W (like a VCore3-500) for the heatbed, 400W space heater,...<br>
Higher voltage means less current, lower voltage means higher current.<br>
My VCore3-300 will therefore have a maximum power consumption of around 900W at 230V.<br><br>
<b>Current</b><br>
Dividing the power through the voltage gives you the amps. In my case: 900W/230V = ~4.2A<br>
Connecting a VCore3-500 to 120V will result in 1750W/120V= ~14.6A!<br>
You better take a look into the fusebox of your apartement/house if your power outlet even supports that much.<br><br>

## Get the power to the printer

### The cable
If the maximum current your printer needs is below 10A you can use a C13 cable. (like for a normal PC)<br>
If your maximum current is between 10A and 16A you have to go for a C19 cable.<br>
<b>Warning:</b> Don't overrun the cable/connector or otherwise you risk a burning cable/connector!<br>
If you need more than 16A you either need to split the load or consult a professional to help you out.<br><br>

Get two or three of those cables, because we are gonna cut and strip one (two) of them for the wiring on the printer.<br>
You should NOT use cables like ones for speakers that you might have used for your 24V wiring, because the isolation is not rated for higher voltages!<br><br>
Here you can see the difference between the connectors.<br>
![C13-C19](https://user-images.githubusercontent.com/98351572/172686941-9025ef9e-7612-464f-ac4a-17ee5e3df9fd.png)<br>

### The connector
Accordingly to you cable, you need C14 or C20 connector.<br>
There are many all-in-one solutions on the market, especially cheap ones.<br>
I do NOT recommend buying one of these for some reasons.<br>
<b>First:</b> often the connector is rated correctly at 10A, but the switch can only manage 5 to 6A.<br>
This is the most common mistake. Overrunning the current will cause a burned down switch causing a fire hazard!<br>
<b>Second:</b> the switch is to 99% a 1pole switch and we don't want this one on an open device like our printer!<br>
This is a more hidden flaw often overseen. The problem is the following: In many countries, there are no regulation of wether the phase is on the left or on the right side of the power outlet. So you never know, if your 1pole switch is really cutting the phase and not the neutral wire. This means you think you turned off you printer and easily can mess around with the wiring, but there could still be mains voltage on it! This brings me back to my first rule: Always unplug the printer before working on the wiring!<br>
Nevertheless, it is always adviceable to have a 2pole switch to cut phase and neutral.<br>
<b>Third:</b> Is not that much of a problem, but normally there is only 1 fuse inside. You can go for a single fuse, but if you can get you hands on one with 2 fuses for almost the same price, than go for it.<br><br>
Those cheap all-in-one devices should only be used, if ALL mains voltage parts are consealed within an isolating casing (like an Ender)! Since our printers have an open mains powered heatbed, this is anything but a good idea!<br>
However, there are a few high priced options which combine all needed features and even add a filter. But they cost 25 to 50 bucks. Nothing you will find on Ali.<br><br>
![connectors-switch](https://user-images.githubusercontent.com/98351572/172691900-a946d6f4-73c4-4e63-bac9-3af48b9e2023.png)<br><br>
Make sure the connector, the switch and if you fancy the filter (recommended) are rated for your maximum current. Some filters are rated for 4A or even less.

### The fuse
My example printer from above has a maximum current of 4.2A, so I take about the next size of fuse, which is 6A (slow-blow or medium-slow-blow).<br>
You got 8 to 9A, you take a 10A fuse.<br>
If you need anything above its likely, that your miniature circuit breaker in your fusebox will blow first (because of missing selectivity).<br><br>

### Terminals of the items above
Make sure your items all have the same terminal connector, so you only have to buy a single set of cable shoes.<br>
Best way are the 6.3mm flat connectors.<br>
![Flachstecker](https://user-images.githubusercontent.com/98351572/172694695-a6d2c2ea-8162-457a-99a0-ef8db383a4d5.PNG)<br><br>
Buy some isolated crimp connectors and the fitting tool. You probably already know those from your local hardware store.<br>
![Flachsteckerhülse](https://user-images.githubusercontent.com/98351572/172697080-6881d7d3-22e0-4f6e-b61d-ba2aed932da2.PNG)<br>
The right ones will be used to connect the PSU.<br><br>

# Lets start the wiring

Take your first spare cable cut off the connectors and strip the mantle of it.<br>
You should then have 3 isolated wires with different colors. Brown (phase), blue (neutral) and yellow-green (earthing). The colors may vary depending on where you live. Just search for color code mains wiring for your country.<br><br>
