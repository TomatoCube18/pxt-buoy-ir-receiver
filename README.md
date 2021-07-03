# Buoy IR Receiver

MakeCode extension for TomatoCube* Infrared Buoy board. The extension should also work with other with NEC compatible IR remotes.

# Documentation

## connectIrReceiver

Connects to the IR receiver module at the specified pin and configures the IR protocol.

```sig
connectIrReceiver(DigitalPin.P0, IrProtocol.Keyestudio)
```

### Parameters

- `pin` - digital pin with an attached IR receiver
- `protocol` - the IR protocol to be detected, for example IrProtocol.Keyestudio or IrProtocol.NEC

## monIrButton

Do something when a specific button is pressed or released on the remote control.

```sig
onIrButton(IrButton.Ok, IrButtonAction.Pressed, () => {})
```

### Parameters

- `button` - the button to be checked
- `action`- the trigger action
- `handler` - body code to run when the event is raised

## irButton

Returns the code of the IR button that was pressed last. Returns -1 (IrButton.Any) if no button has been pressed yet.

```sig
irButton()
```

## onIrDatagram

Do something when a specific button is pressed or released on the remote control.

```sig
onIrDatagram(() => {})
```

### Parameters

- `handler` - body code to run when the event is raised

## irDatagram

Returns the IR datagram as 32-bit hexadecimal string. The last received datagram is returned or "0x00000000" if no data has been received yet.

```sig
irDatagram()
```

## wasIrDataReceived

Returns true if any IR data was received since the last call of this function. False otherwise.

```sig
mwasIrDataReceived();
```

## irButtonCode

Returns the command code of a specific IR button.

```sig
irButtonCode(IrButton.Number_9)
```

### Parameters

- `button` - the button

## MakeCode Example

```blocks
connectIrReceiver(DigitalPin.P0, IrProtocol.Keyestudio)

onIrButton(IrButton.Ok, IrButtonAction.Released, function () {
    basic.showIcon(IconNames.SmallHeart)
})

onIrButton(IrButton.Ok, IrButtonAction.Pressed, function () {
    basic.showIcon(IconNames.Heart)
})

basic.forever(function () {
    if (wasAnyIrButtonPressed()) {
        basic.showNumber(makerbit.irButton())
    }
})

```

## License

Licensed under the MIT License (MIT). See LICENSE file for more details.

## Supported targets

- for PXT/microbit
- for PXT/calliope
