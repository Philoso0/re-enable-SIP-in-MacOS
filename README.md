# re-enable-SIP-in-MacOS
if follow the guidance of playCover to disable SIP from Recovery Mode, there are some problems to re-enable SIP

The Code below in playCover guidance is to stop system from checking binary files
so that users can get a higher degree of custom in the cost of descend security of system

```
sudo nvram boot-args="amfi_get_out_of_my_way=0x1 ipc_control_port_options=0"
```

When you try to re-enable SIP in Recovery Mode, terminal will throw an error saying

```
Failed to update security configrations for 'macintosh hd' because xxx
```
if xxx infers internet connection error, 
  check top-right corner to ensure your wifi is well-connected
else xxx infers "cann't create new local policy ...", maybe, 
  this is exactly the outcome of 
```
sudo nvram boot-args="amfi_get_out_of_my_way=0x1 ipc_control_port_options=0"
```
this pecie of code

you can just type `sudo nvram -d boot-args=`, which will helps it works when you re-enable SIP

BTW, it's not quite nccessaray to go back Recovery Mode to re-enable SIP,
you can just use `sudo csrutil clear` and input your usr name and pw, then restart,
everything goes normal and you can verify the by `csrutil status`
