# TCA

Arduino Library for TCA Family I2C multiplexer.

## Description

Library for the TCA family I2C multiplexer.
The library allows you to enable 0 to 7 I2C channels (ports) uniquely or simultaneously.
This is especially handy if you have multiple devices/sensors that have a fixed address.

**Warning**
The library is not tested extensively.

I2C address is 0x70 .. 0x77.

The library caches the channels enabled, and if a channel is enabled,
it will not be enabled again (low level) to optimize performance.

## Interface

### Constructor

- **TCA(const uint8_t deviceAddress, TwoWire \*wire = &Wire);)** Constructor, Address = 0x70 .. 0x77, wire = Wire or WireN.
- **bool begin(uint8_t sda, uint8_t scl, uint8_t mask = 0x00);**  Set I2C pins for ESP32 alikes, set mask of channels to be enabled.
- **bool begin(uint8_t mask = 0x00);**  set mask of channels to be enabled.
- **bool isConnected()** retuns true if address of the multiplexer itself is found on I2C bus.


### Find device

- **bool isConnected(uint8_t addr)** retuns true if arbitrary address is found on I2C bus.
This can be used to verify a certain device is available (or not) on an enabled channel.


### Channel functions

- **void enableCh(uint8_t channel)** enables channel 0 .. 7. Multiple channels can be enabled in parallel.
- **void disableCh(uint8_t channel)** disables channel 0 .. 7. Will not disable other channels.
- **void selectCh(uint8_t channel)** enables a single channel 0 .. 7 uniquely. All other channels will be disabled, although these can be set again with enableChannel.
- **bool isEnabled(uint8_t channel)** returns true is a channel is enabled.
- **void setChMask(uint8_t mask)** enables 0 or more channels simultaneously with a bitmask.
- **uint8_t getChMask()** reads back the bitmask of the channels enabled.
- **void setResetPin(uint8_t resetPin)** sets the pin to reset the chip. (tested on TCA9548A only, further testing need.)
- **void reset()** trigger the reset pin.
- **uint8_t getCh()** Gets actual cahnnel
- **uint8_t SetNextCh()** Sets next cahnnel of actual
- **uint8_t SetPrevCh()** Sets previous channel of actual
- **uint8_t SetNextCh()** Gets Max channel number on device (tested on TCA9548A only, further testing need.)
 

## Operation

See example (not uploaded yet)


## Future

- test test and test
