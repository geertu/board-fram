# Board FRAM - Board Farm Remote Access Management

## DESIGN

  - Each development board has its own UNIX user
  - Authentication is provided by SSH

    `~/.ssh/authorized_keys` should contain only lines of the form:

	restrict,pty,command="/path/to/fram $user" ssh-rsa $key $keyid

  - Seperation between remote access and board farm infrastructure: Actual
    board control operations are performed by scripts, to be provided by you.


## TODO

  - Logging
  - Board locking/reservation
  - ...


## INSPIRATION

  - https://gitolite.com
  - https://github.com/kbingham/lab
