Juniper MX's stateful-firewall and SRX's policy rules renumbering
- Input display set sytle config, Output stdout.
```
show configuretion | display set
```

- Automatic detecting MX's stateful-firewall or SRX's policy
  - outputs limited change

- MX sample

```
# before
set services stateful-firewall rule Untrust term Untrust-Trust-1 from ...
set services stateful-firewall rule Untrust term Untrust-Trust-2 from ...
set services stateful-firewall rule Untrust term Untrust-Trust-3 from ...

# after
rename services stateful-firewall rule Untrust term Untrust-Trust-1 to term Untrust-Trust-010
rename services stateful-firewall rule Untrust term Untrust-Trust-2 to term Untrust-Trust-020
rename services stateful-firewall rule Untrust term Untrust-Trust-3 to term Untrust-Trust-030
```

- SRX sample

```
# before
set security policies from-zone Untrust to-zone Trust policy Untrust-Trust-1 match ...
set security policies from-zone Untrust to-zone Trust policy Untrust-Trust-2 match ...
set security policies from-zone Untrust to-zone Trust policy Untrust-Trust-3-1 match ...
set security policies from-zone Untrust to-zone Trust policy Untrust-Trust-3-2 match ...

# after
rename security policies from-zone Untrust to-zone Trust policy Untrust-Trust-1 to policy Untrust-Trust-010
rename security policies from-zone Untrust to-zone Trust policy Untrust-Trust-2 to policy Untrust-Trust-020
rename security policies from-zone Untrust to-zone Trust policy Untrust-Trust-3-1 to policy Untrust-Trust-030-010
rename security policies from-zone Untrust to-zone Trust policy Untrust-Trust-3-2 to policy Untrust-Trust-030-020
```

- Default line count up 10 unit.
  - If you want another unit, please run with -v "unit=1" option
```
./junos-renumber -v "unit=1" show-configuration-display-set.txt
```

- If you conflicted exist rule#, please pipe to tac or tail -r.
```
./junos-renumber -v "unit=1" show-configuration-display-set.txt | tac
```

- Good luck :-)
