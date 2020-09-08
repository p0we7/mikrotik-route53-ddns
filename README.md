# Mikrotik Router53 DDNS

## Add global variable
```
/system script add name=params source={
:global apiKey "you-api-key";
:global Secret "you-share-secret"
:global ddnshostname "example.com.";
:global ddnsserv "update.example.com"
}
```

## Add scheduler
```
/system scheduler add name=global-scripts start-time=startup on-event="/system script {run md5sum; run params; run ddns_route53;}"
/system scheduler add name=ddns-update interval=30m on-event="/system script run ddns_route53"
```


## Ref 
1. [Script MD5 Hash Generator](https://forum.mikrotik.com/viewtopic.php?f=9&t=62895)
2. [Dynamic DNS Update Script for Namecheap](https://wiki.mikrotik.com/wiki/Dynamic_DNS_Update_Script_for_Namecheap)