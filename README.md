# junos-renumber
Juniper MX's stateful-firewall and SRX's policy rules renumbering
- Input display set sytle config, Output stdout.
```
show configuretion | display set
```
- Automatic detecting MX's stateful-firewall or SRX's policy
 - - outputs limited change
- Default line count up 10 unit.
 - - If you want another unit, run with -v "unit=1" option
```
./junos-renumber -v "unit=1" show-configuration-display-set.txt
```
- Good luck :-)
