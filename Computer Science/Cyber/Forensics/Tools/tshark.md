A command line tool for Wireshark.
Good for extracting and processing packet data. 
Note that [[scapy]] might be a better option for automation.
Usage: `tshark -r file <options>`
## Filtering
Use `-Y "a.b==c"`.
The same as a Wireshark filter.
## Extracting a field
Use `-T fields -e field.name`.
Will extract all the data of the field, of all relevant packets, separated by newline.
The field name is the same as in filter.