### Connect to Pi via ssh
- Copy rsa pub keys of your machine to the pi to be able to connect via fingerprint
- On the host machine type:
```bash
hostname -I
```
in order to find the IP address of the pi.
- Connect from the main machine with one of the following commands:
```bash
ssh hostname.local
#or
ssh username@hostname
#or
ssh username@IP
``` 
