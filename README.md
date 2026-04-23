# FreePBX / Asterisk Custom Dialplan Lab

This repository contains a custom Asterisk dialplan example for use with FreePBX in a controlled lab environment.

The purpose of this project is to demonstrate practical understanding of FreePBX and Asterisk dialplan development, including custom contexts, pattern-based routing, variable handling, conditional logic, and outbound trunk selection.

## Compatibility

- FreePBX 15
- FreePBX 16
- FreePBX 17 may require adjustments depending on how extension context assignment is handled in the GUI

## Project Goals

This lab is intended to demonstrate:

- Custom dialplan development in Asterisk
- Use of `extensions_custom.conf`
- Creation and use of custom contexts
- Pattern matching with Asterisk dialplan syntax
- String slicing and variable manipulation
- Conditional logic with `ExecIf()`
- Dynamic variable generation with `RAND()`
- Outbound routing through a named PJSIP trunk
- Basic call recording and logging behavior

## Repository Contents

- `custom_dialplan.conf`  
  Example custom dialplan context for lab testing and pattern-based call handling

## Setup Overview

1. Open **Admin > Config Edit** in FreePBX.
2. Review or edit `extensions_custom.conf`.
3. Copy the custom dialplan context from this repository into `extensions_custom.conf`.
4. Save the file and apply the configuration.
5. Create a test extension in **Connectivity > Extensions**.
6. If your FreePBX version supports custom extension contexts, assign the test extension to the custom context used in this project.
7. Confirm that the trunk name in the dialplan matches the exact trunk name configured in your FreePBX system.

## Important Configuration Note

The sample dialplan sends calls using a named PJSIP trunk. Update the trunk reference in the dialplan so it matches your own environment exactly.

Example:

`Dial(PJSIP/${CALLEDNUM}@YOUR_TRUNK_NAME,30)`

Replace `YOUR_TRUNK_NAME` with the exact name of your configured PJSIP trunk.

## What This Lab Demonstrates

This project shows how Asterisk dialplan logic can be used to:

- Process dialed input
- Normalize or transform values before routing
- Apply pattern-based logic to outbound calls
- Build dynamic variable values during call processing
- Route calls through a selected outbound trunk
- Record and inspect test calls in a lab environment

## Notes on FreePBX Versions

Behavior may differ between FreePBX versions.

In some versions, custom extension contexts can be assigned directly in extension settings. In others, this option may be limited or removed from the GUI, which may require adapting the dialplan structure to fit the default internal calling context.

## Testing and Safety

This project is intended for:

- Lab use
- Training
- Dialplan experimentation
- Authorized PBX testing

Always ensure your configuration, call routing, caller ID behavior, and trunk usage comply with applicable law, carrier requirements, and organizational policy.

## Skills Demonstrated

This repository can be used to showcase experience with:

- FreePBX administration
- Asterisk dialplan syntax
- Custom call routing
- PJSIP trunk usage
- Pattern matching
- PBX troubleshooting
- Telecom lab testing
