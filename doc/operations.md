# Board operations to be implemented locally

The actual operations to control a board in your farm are farm and/or board
specific.  Hence these operations have to be provided by you.

They can be provided as shell functions (in "$BOARD.cfg"), or as scripts or
other executables (in $HOME/bin, or in the system's default $PATH).

All operations are of the form "$VERB-$NOUN" or "$VERB-$NOUN-$OPTION", with
"$NOUN" the name of the board.

See examples/h3-salvator-xs.cfg for an example.


## Mandatory Operations

### Serial Console Access

  - "console-$BOARD"

    Connect to the serial console of the board.  This is typically implemented
    using e.g. GNU Screen or Picocom.

    See examples/screenrc for an example screenrc file, which prohibits the
    user from performing unsafe operations (e.g. spawning an interactive
    shell).


### External Power Control ###

These operations are intended for controlling and monitoring external power
input to the board.  Please see "Accessory Switch Control" for controlling an
optional on-board power-switch.

  - "power-$BOARD-on"

    Power the board on.

  - "power-$BOARD-off"

    Power the board off.

  - "power-$BOARD-status"

    Show the board's power status.


### Reset Control ###

  - "reset-$BOARD"

    Reset the board.

    If no reset control is available, this can be implemented by cycling
    accessory switch or external power control (with a board-specific delay in
    between).


## Optional Operations

### External Power Measurement ###

  - "power-$BOARD-sample"

    Show current power consumption of the board.


### Accessory Switch Control ###

These operations are intended for controlling and monitoring an on-board
power-switch.  If such a switch is present, all three operations below must be
implemented.

  - "acc-$BOARD-on"

    Set accessory switch on.

  - "acc-$BOARD-off"

    Set accessory switch off.

  - "acc-$BOARD-status"

    Show the board's accessory switch status.


### Wake-Up Control ###

  - "wake-$BOARD"

    Wake the board using a key or GPIO.

  - "wol-$BOARD"

    Wake the board using Wake-on-LAN.


## User Environment Set-Up ###

  - "setup-$BOARD" "$USER"

    Set up a proper environment for the user.  This can be used to e.g. provide
    a user-specific NFS root file system.
