# Govee H5075 Bluetooth Client

A library to listen for the BLE (Bluetooth Low Energy) broadcasts from Govee H5075 Thermometer Hygrometer. Requires a compatible bluetooth module and operating system (see [prepequisites](https://github.com/abandonware/noble#prerequisites)).

## Installation

`npm install govee-bt-client`

## API

* `startDiscovery: (callback: (reading: GoveeReading) => void)` 
    * Starts listening to broadcasts and pass decrypted data into the callback function.
* `stopDiscovery()`
    * Stops listening to broadcasts from Bluetooth 
* `debug: (on: boolean)`
    *  Function to enable debugging of bluetooth advertisements and peripherals.

## Example

```
import { startDiscovery, stopDiscovery, debug } from "./index";

debug(true);

console.log("=== start discovery");

startDiscovery((reading) => {
    console.log(reading);
});

setTimeout(async () => {
    await stopDiscovery();
    console.log("=== stop discovery");
}, 30000);
```

## Credits
Credits and thanks to

* [Thrilleratplay/GoveeWatcher](https://github.com/Thrilleratplay/GoveeWatcher) for explanation and examples of how to decode advertisement data for Govee G5075.
* [@abandonware/noble](https://github.com/abandonware/noble) for a great BLE library for node