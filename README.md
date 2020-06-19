<h1 align="center">A Garden Irrigation System for Home Assistant (Version2)</h1>

<h2>MOST IMPORTANT</h2>

__This is NOT quite a '*pick-it-up-and-drop-it-in*' solution. There are a few idiosyncracities which require some understanding of Home Assistant in general and of Lovelace in particular.__

__Be prepared to spend some time setting it up if you choose to try it out__


<h2>Prerequisites</h2>

There are some [prerequisites](https://github.com/kloggy/HA-Irrigation-Version2/blob/master/prerequisites.md) to setting this up. PLEASE READ THEM. Any questions posted that look like they haven't been read may be ignored.


Please note that as it stands this assumes that you are using `yaml` mode for Lovelace because that is what I use.


<h2> Also Important</h2>

I am posting this project *purely as a way to share it* because people showed an interest in Version 1. It is not presented as a 'turn-key' solution. It is purely *my personal solution* which I am more than happy for anyone to use in any way they see fit. Please understand that Version 2 will require some configuration and customisation on your part to make it work. I am prepared to help people get it working but only if you have shown that you have tried more than just copying the files. The prerequisites are documented and must be followed.

I am only using GitHub literally as a repository. What that means is I just copy my code from my PC to here so that it can be shared. There is no formal version control here other than that inherent in the Github editing history.

One day maybe I'll delve further into how GitHub works but for now I'm afraid that is the situation.


<h2>Background</h2>

__IMPORTANT__ - This is now a *__beta__* of Version 2. For anyone who was using the 'Preview' it has a few cosmetic improvements (IMO) and I have completely restructured the Lovelace code. I think it might now be more efficient and also every section is in its own file so that should make it easier if you wish to change anything.

As far as I know, and no one who used the preview told me otherwise, it works perfectly. If you decide to use it in any way be sure to read ALL of this page.

-----

I wrote this package mainly because Version 1 of my irrigation package worked so well for me that the 'chief gardener' in this house (my wife!) decided she would really like to expand it from four zones to eight so as to include the flower beds as well as the lawn.

Whilst I believe that Version 1 could easily cope with this by the careful use of copy and paste I decided to do a complete rewrite.

One reason for this decision was that Version 1 had been one of the first things I did with HA and I always thought that there were things I could have done better. Furthermore, Lovelace appeared since then so there is scope to do much more with the user interface.

Also, being early 2020 many of us found ourselves with too much time on our hands due to the Corona virus so it seemed like a perfect project to pass some of the time.

All that time did not necessarily work in its favour though and this project has possibly ended up growing organically rather than through good design. Furthermore as I learnt new techniques in Lovelace this became as much a project about the user interface as it did about the irrigation.

I am by no means a Javascript or CSS programmer so there may well be things I (or you) can improve on at some point in the future. 

Version 1 was designed around a Sonoff 4ch but for Version 2, I will use an 8 relay board controlled with an ESP32.
This in itself should make little difference as ultimately all the package does is turn switches on and off.

This package has been designed with two scheduled cycles per day with each cycle having up to eight zones. The number of zones can be configured from the UI and like Version 1, if more zones are needed some of the 'globals' need to be replicated (but I have not tried this).

Both scheduled cycles can be set to run at any time on any day(s) of the week.

A manual cycle is also provided.

The watering times can be automatically adjusted based on rainfall and temperature and whilst I think this has been improved in Version 2, as in Version 1 this is quite experimental. It is different to (better than) Version 1 in that both the rainfall and temperature adjustments can be turned on or off independently of each other and separately for each cycle.

Almost everything can be set from the UI including the friendly names of cycles and zones. Tap/click on most fields to change them in a pop-up (but remember that if you have several browser tabs open the pop-ups may appear on a different tab!). 

__Note -__ Extensive use is made of `!include` to avoid code repetition. You need to replicate the folder structure in order for it to work. You can change the lovelace code if it suits you and so have your own folder structure but I can't help if you choose to do that.

As it stands you need a `lovelace` folder and the folder that your packages are in.

--------------

__Disclaimer__ - This has __NOT__ been extensivley tested. In fact as of now it has only been used on my desk! Feel free of course to use, adapt or change it in any way you see fit. But if you do find errors I'd be interested to know so I can look at it although no promises can be made regarding how or when I will get to fix anything.


Likewise if you come up with any improvements also please tell me!


<img src="https://github.com/kloggy/HA-Irrigation-Version2/blob/master/screenshots/screenshot-v2.jpg">

CHANGES by JP:

- Use switch names properly.
- Add Evaporation mode via SmartIrrigation Integration (https://github.com/jeroenterheerdt/HASmartIrrigation)
- In Evaporation mode:
    - Times are set by % of smart daily irrigation rate.
    - Evaporation and estimated irrigation shown.

Requisites:
- SmartIrrigation with auto update disabled.
- Template sensors:
    - smart_irrigation_hourly_netto_precipitation
    - smart_evapotranspiration