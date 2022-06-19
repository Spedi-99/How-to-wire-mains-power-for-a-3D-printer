<b><i> 
  - Do you want your printer to be unreliable because the fuse blows every now and then?<br>
  - Do you want to electrify yourself on your printer?<br>
  - Do you want to melt down some cables and/or connectors mid printing?<br>
  - Or do you even want to burn down your house with your printer?
</b></i><br><br>

If your answer is no, then you might find my guide helpful.<br>
I'm an electrical engineer working in industrial areas for decades now, so I will show you a safe way how to wire mains voltage to your printer that you don't risk hurting someone or even start a fire.<br><br>

I know this isn't a short description, but this is a very serious topic and to be honest almost all of you wouldn't be legally allowed to wire this up. So if something bad happens, you could be in legal trouble. If you follow my guide, you should at least have the proper items that nothing goes up in smoke or hurts someone. (Tho you could still mess things up, so I'm not responsible for any of your actions)<br><br>

!! Working with mains voltage is a job for professionals because your life depends on it !!<br>
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

# Lets crunch some numbers

There are some key numbers for the project we need to clarify first.<br><br>
<b>Voltage</b><br>
If you live in Europe you will certainly have 230V as a mains voltage. Other countries may have 120V or in some special cases in the USA even 240V. I assume you set the general voltage on the PSU accordingly to 120 or 230V, and all other components are fitting as well (like the heatbed).
<br><br>
<b>Power</b><br>
Getting the power isn't that easy, because we have to do some math now.<br>
There are 2 different type of loads here. Every PSU has electronics inside that will adapt to certain voltage levels and the rated power stays the same. So a 250W PSU will have 250W no matter if it is connected to 110V or 120V (respectively 230V or 240V).<br>
The other type of loads are the heaters (heatbed and space heater if you fancy an enclosure). Those behave differently if they are connected to a higher voltage than they are rated. Basically, you can't connect a 120V heater to 230V or it will just burn off immediately.<br>
Take a look at the following table to get to correct power draw:<br><br>
![PowerTable](https://user-images.githubusercontent.com/98351572/173236779-0bd5e3bf-637a-4ede-b13c-76b2af682bcf.PNG)<br><br>
To calculate the power of a heater if you have other mains voltage, the formula is:<br>
Power = RatedPower * (YourVoltage)² / (RatedVoltage)²<br><br>

<b>Current</b><br>
Having the power consumption of the printer, we now need to calculate the current with the following formula:<br>Current = TotalPower / MainsVoltage<br>
As for example 1: 1370W/230V = 5.95A<br>
As for example 2: 2040W/120V = 17.0A<br><br>

Now that you know the current you need to check the fusebox of your apartement/house if your power outlet even supports that much. (Remember that there might be other devices also be connected to the same fuse!)<br>
Those with 120V mains voltage might already spot the problem, that the circuit-breaker only delivers a maximum of 15A in most cases as well as the power outlet is only to 15A max.<br>
Hopefully you haven't already ordered the printer, because you should check if you have the possibility for 240V. The higher the current the more difficult it gets with wiring!<br><br>
The last possibility if you simply have no other choice is to limit the heater power by software. Klipper and RRF offer the possibility to max-limit the heater to a certain percentage (like 75%). Just check the documentation on how this is done. It would be good if you leave about 10 to 15% margin to the trip value of the fuse.<br><br>

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
<b>Second:</b> In 99% of the cases, the switch is only a 1pole switch and we don't want this one on an open device like our printer!<br>
This is a more hidden flaw often overseen. The problem is the following: In many countries, there are no regulation on wether the phase is on the left or on the right side of the power outlet. So you never know, if your 1pole switch is really cutting the phase and not the neutral wire. This means you think you turned off you printer and easily can mess around with the wiring, but there could still be mains voltage on it! This brings me back to my first rule: Always unplug the printer before working on the wiring!<br>
It is always adviceable to have a 2pole switch (DPST) to cut phase and neutral. (or both phases if you have 240V)<br>
<b>Third:</b> Is not that much of a problem, but normally there is only 1 fuse inside. You can go for a single fuse, but if you can get you hands on one with 2 fuses for almost the same price, than go for it.<br><br>
Those cheap all-in-one devices should only be used, if ALL mains voltage parts are consealed within an isolating casing and you have a low voltage heatbead (like an Ender)! Since our printers have an open mains powered heatbed, this is anything but a good idea!<br>
However, there are a few high priced options which combine all needed features and even add a filter. But they cost 25 to 50 bucks. Nothing you will find on Ali.<br><br>
![connectors-switch](https://user-images.githubusercontent.com/98351572/172691900-a946d6f4-73c4-4e63-bac9-3af48b9e2023.png)<br><br>
Make sure the connector, the switch and if you fancy the filter (recommended) are rated for your maximum current. Some filters are only rated for 4A or even less.

### The fuse
The example printer from above has a maximum current of nearly 6A. <br>
Next fuse size would be 6.3A which might be a bit too close, so maybe take the next one higher up with 8A.<br>
For anything more than 10A you might consider using a 13A breaker instead (characteristic B13 if you live in Europe).<br>
Keep in mind, that if the breaker in your fuse box doesn't have a 1.6 times higher tripping current than the fuse on your printer, there is a high chance that the breaker in the fuse box will pop first, because of missing selectivity.<br>
Having a fuse directly on the printer is helpful (more for smaller printers), but it is not super mandatory. At a certain level it doesn't make sense and you just use the breaker in the fuse box.<br>

### Terminals of the items above
Make sure your items all have the same terminal connector, so you only have to buy a single set of cable shoes.<br>
Best way are the 6.3mm flat connectors.<br>
![Flachstecker](https://user-images.githubusercontent.com/98351572/172694695-a6d2c2ea-8162-457a-99a0-ef8db383a4d5.PNG)<br><br>
Buy some isolated crimp connectors and the fitting tool. You probably already know those from your local hardware store.<br>
![Flachsteckerhülse](https://user-images.githubusercontent.com/98351572/172697080-6881d7d3-22e0-4f6e-b61d-ba2aed932da2.PNG)<br>
The right ones will be used to connect the PSU.<br><br>

# Lets start the wiring

Take your first spare cable cut off the connectors and strip the mantle of it.<br>
You should then have 3 isolated wires with different colors. Brown (phase), blue (neutral) and yellow-green (earthing). The colors may vary depending on where you live. Just search for color code mains wiring for your country.<br>
Please, please, PLEASE.... I can't stress this enough! Stick to the corrct color code, especially for grounding!<br> 
One should always be able to identify what is earth, what is a life wire and what is low voltage at a short look on the wiring.<br><br>

I'm not going to describe how to crimp different wires/connectors, because there are already tons of videos out there.<br>
Please keep an eye where I put which crimp-connector on. If you don't see one (orange blocks in the biddle - WAGO 221), then just strip the insulation.<br>
Be aware that you are only allowed to put blank wires in there with no ferrules on it, otherwise they have bad contact resulting in overheating and possible fire.<br><br>

![wiring01](https://user-images.githubusercontent.com/98351572/174494953-424f4dde-58b5-417d-9522-99965efe8803.PNG)
<br><br>
Consider also connecting the frame to earth, as well as DIN-rails, your metal back-plate, or your space heater.<br><br>
# Prestartup checklist
- use a multimeter and check continuity of all connections, and that you have none like from phase to the frame.<br>
- Are all covers of connectors closed? (PSU, SSR,...)<br>
- Are all mains voltage conections points isolated so you can't touch them? Otherwise you need to isolate them so you can't touch them by accident!<br>
- Are the voltages of the PSUs set correctly to your voltage level?<br>
- Did you put in the correct fuses?<br>
- Is the power switch still off?
<br>

# Power up

If you completed the checklist, connect the power cord to the printer, keep your hands off the printer and plug it in your power outlet.<br>
Now try to keep as far away as possible, keep your eyes on the electronics and switch on the printer. Keep your finger on the switch so you can immediately can switch it off again if you can see some magic smoke appear.<br>
Best case: the LED of the PSU lights up and stays lit.<br><br>
Congrats! you are now clear to start with your printer setup.<br><br>
Last word: ALWAYS switch off the printer and pull the plug if working on the wiring!<br><br>

HAPPY PRINTING!
