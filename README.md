##Setup

Install Node and git for your operating system. If you're running Debian/Ubuntu, you can run the following two lines:
```
sudo apt-get install build-essential libavahi-compat-libdnssd-dev git
curl -sL https://deb.nodesource.com/setup_0.12 | sudo bash -
```

Next, run the following lines to install the bridge

```
git clone --recursive https://github.com/Hackworth/VeraHomeKitBridge.git
cd VeraHomeKitBridge
npm install
cd lib/HAP-NodeJS
npm install
cd -
```

Edit `config.json`, enter your Vera's IP address as well as the names of your garage doors, if any. This is case sensative.

Finally, run the following to start the HomeKit bridge:
`npm run start`

There are several applications in the iOS App Store you can use to add HomeKit devices, MyTouchHome and Eve are known to work. The PIN code for adding devices is listed in the config file you edited earlier.

##Scenes

VeraHomeKitBridge will treat Vera pairs of scenes as binary switches.
For example, if you have two scenes named *Media Center - On* and
*Media Center - Off*, it will expose that to HomeKit as *Media Center*
and inteligently run the correct scene if you asked it to turn on or
off.

##Upgrading

Periodic updates of HAP-NodeJS are required for new versions of iOS,
here are complete instructions for upgrading.

```
git pull
git submodule foreach git pull
rm -rf persist
```
On your primary iOS device, Settings -> Privacy -> HomeKit -> Reset
HomeKit Configuration...

Re-add all your HomeKit devices

##Credits
Most of this is just [HAP-NodeJS](https://github.com/KhaosT/HAP-NodeJS)
and the rest was made by user Albeebe on the Vera forums. I just made it
suck slightly less.
