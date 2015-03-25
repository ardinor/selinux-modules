## Custom SELinux modules ##

Various SELinux modules I've created as needed

#### \*\* USE AT YOUR OWN RISK \*\* ####

### [Logspout Module](logspout/) ###

Logspout needs write access on the sock_file docker.sock and connectto access on the unix_stream_socket /run/docker.sock, the policy modules grant the required access.


To manually compile and load a policy module (.te)

    # Create a .mod file which is needed to make the compiled policy module
    checkmodule -M -m -o module.mod module.te
    # Turn the .mod into .pp
    semodule_package -o module.pp -m module.mod
    # Load the module
    semodule -i module.pp
