# Board FRAM - Board Farm Remote Access Management

## FEATURES

  - FRAM provides access to a single board from a remote location:
      - Board control
          - Power
	  - Reset
	  - Optional accessory switch
	  - Optional wake-up key and/or Wake-on-LAN
      - Board monitoring
	  - Serial console
          - Power consumption
      - Board management
	  - Kernel and DTB upload
	  - Automatic board user environment setup
	  - Multi-User access locking
	  - Restricted administration mode

  - FRAM needs no special tools on the client, just ssh and rsync

    `ssh <board>@<remote> <command> ...`

  - FRAM provides a convenience wrapper, to simplify access to remote boards in
    multiple farms:

    `fram <nickname> <command> ...`

  - FRAM can be made to work with any backend that you use to control your
    board farm.

  - FRAM has a builtin help command.


## DESIGN DECISIONS

  - Each development board has its own UNIX user (cfr. Android apps).

  - Authentication is provided by SSH

    `~/.ssh/authorized_keys` should contain only lines of the form:

	restrict,pty,command="/path/to/fram-server $user" ssh-rsa $key $keyid

  - Separation between remote access and board farm infrastructure: Actual
    board control operations are performed by shell functions, scripts, and/or
    external tools, to be provided by you.

  - KISS, easy to review for correctness and security.

  - Simple configuration file


## INSPIRATION

  - https://gitolite.com
  - https://github.com/kbingham/lab
