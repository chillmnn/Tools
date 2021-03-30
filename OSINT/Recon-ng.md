# Recon-ng

## The use of syntax for this tool is very similar to Metasploit.

### Launch Recon-ng from a terminal.
```
recon-ng
```

### Displays the help menu.
```
help
```

### This will perform a quick search of tools in the marketplace.
```
marketplace search
```

### This will perform a search for tools relating to keyword IP in the marketplace.
```
marketplace search IP
```

### This will install the tool recon/hosts-hosts/resolve from the marketplace that was populated from out keyword search of IP.
```
marketplace install recon/hosts-hosts/resolve
```

### List the modules that are installed, at this point recon/hosts-hosts/resolve should be listed.
```
modules search
```

### This will create a workspace.
```
workspaces create example
```

### This display workspaces that have been created.
```
workspaces list
```

### This select a previously added workspace.
```
workspaces load <name of workspace>
```

### This will load a module that we can use in our selected workspace.
```
modules load recon/hosts-hosts/resolve
```

### Once a module is loaded, this will display info and the needed requirements that need to be specified for the tool to run.
```
info
```

### This will set the requirements.
```
options set source <domain.com>
```

### This will run the module.
```
run
```
