KiCad Libraries for Sensible People
===================================

This is a set of KiCad libraries which can be used by sensible people who want
to have a set of schematic symbols and layout footprints which are consistent,
high quality, and community validated.

This set of libraries has come about because other library sets for KiCad are
extremely inconsistent, often low quality, and sometimes just plain wrong.


## Schematic Symbol Style Guide

All schematic symbols **must** follow these guidelines:

1. There shall be one schematic symbol library per manufacturer.  If a
manufacturer is a second source for another (ie: both make the same part number
with the same function and packaging) then the perceived larger manufacturer
takes precedence (ie: Maxim parts which are second sourced by Touchstone go in
the Maxim library).

2. Using a 100 mil grid, pin ends and origin shall lie on-grid.

3. The origin shall be placed in the middle of the symbol.

4. Field texts shall use a size of 50 mils and should use only upper case
letters.

5. Pins shall have a length of 200 mils.

6. Whenever possible, pins shall be grouped logically (ie: by function set or
port).

7. Pins shall have both a name and a number assigned and visible which
correspond to the manufacturer's naming convention in the data sheet.  Pins
which are multiplexed should only contain the pin name and not a full list of
all possible multiplex options.

8. Whenever possible, inputs shall be on the left and outputs are on the right.

9. Whenever possible, power input (ie: VCC) shall be at the top and power return
(ie: VSS) shall be at the bottom of the symbol.

10. Symbols shall be named by the full manufacturer part number.  If there are
variants of the part which would have the same exact symbol, [bash regular
expressions][bash regex] may be used to substitute for a portion of the part
number.

11. For parts which have a thermal or ground pad (such as QFN package parts),
the thermal or ground pad shall be the highest numbered pin and if the
manufacturer does not provide a name for this pin it shall be called "THERMAL
PAD".

12. Pins which are asserted low shall use a top-bar over their name (ie: pin
name starts with a "~" character).

[bash regex]:http://www.tldp.org/LDP/abs/html/x17129.html


## Power Symbol Style Guide

All power symbols, which are automatically global nets in a schematic, **must**
follow these guidelines:

1. All power symbols must reside within the `power.lib` schematic symbol
library.

2. There shall be only 1 pin per power symbol for DC voltages and 1 pin per
phase per power symbol for AC voltages (single phase AC is 2 phases!).

3. Pins shall have a length of 0, so there is no confusion as to its location
and orientation.

4. Pins shall have their type set to "Power Input".

5. Pin names and numbers shall not be visible but must be set and use the name
which corresponds to the power symbol name.  For AC symbols, the names end in
"P" and "N".

6. The reference designator must start with the "#" character.

7. The "Power Symbol" box must be checked under the Component Properties/Options
Dialog.

8. Power symbols for common voltage levels which indicate a voltage value shall
denote if the voltage is AC or DC, and if AC then also indicate if RMS, the
frequency, and the phases (ie: 3.3 VDC, 120 VAC RMS 60 HZ L-N, 208 VAC RMS 60 HZ
L-L 3PH DELTA).  Ranges are allowed to be specified (ie: 90-264 VAC RMS 47-63 HZ
L-L).

