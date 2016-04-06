# BASH
### Zip all files in current directory
`for i in */; do zip -r "${i%/}.zip" "$i"; done`

### Remove all except <pattern>
`shopt -s extglob # If not enabled`
`rm !(<pattern>) # can be generalized for other commands obviously`

### SSH tunnel to server
`ssh -D <port> -C <user>@<host>`

### Add public key to server
`ssh-copy-id`

### Copy things to / from server
`scp <path-to-file> <user>@<host>:<path-to-dest>`

### SSH into another device and say stuff with speakers. 10/10
```
ssh macbook
say "HELLO I'M GHOST"
```
