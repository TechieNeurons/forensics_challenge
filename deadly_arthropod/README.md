1. We get a pcap with USB in it
2. Take a look at how to transform usb in letters
3. https://github.com/carlospolop-forks/ctf-usb-keyboard-parser
4. the data is in ``` usbhid.data ```, the final command was :

```
tshark -r deadly_arthropod.pcap -Y 'usb.data_len == 8' -T fields -e usbhid.data | sed 's/../:&/g2' >> usbhid_keys.txt

# Then

python ./ctf-usb-keyboard-parser/usbkeyboard.py ./usbhid_keys.txt # If error delete first blank line in the txt file
```

5. Flag !
