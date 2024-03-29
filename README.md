# Dogecoin Core in Docker optimized for Unraid
Dogecoin is an open source peer-to-peer digital currency, favored by Shiba Inus worldwide.

You can find the full source code here: https://github.com/dogecoin/dogecoin

ATTENTION: Please keep in mind that your wallet is stored in the created folder in your appdata directory/.dogecoin/wallet.dat - I strongly recommend you to backup this file on a regular basis!

IMPORT: If you are already using Dogecoin Core you can import your existing wallet by placing the WALLETFILE in the appdata directory for dogecoin/.dogecoin/wallet.dat and then choose to use a existing wallet.

## Env params
| Name | Value | Example |
| --- | --- | --- |
| DATA_DIR | Please keep in mind that your wallet is stored there and I strongly recommend you to backup that path (the wallet is stored in your Dogecoine appdata directory/.dogecoin/wallet.dat). | /dogecoin |
| UID | User Identifier | 99 |
| GID | Group Identifier | 100 |
| UMASK | Umask value | 000 |

## Run example
```
docker run --name Dogecoin-Core -d \
	-p 8080:8080 \
	--env 'UID=99' \
	--env 'GID=100' \
	--env 'UMASK=000' \
	--env 'DATA_PERM=770' \
	--volume /path/to/dogecoin:/dogecoin \
    --restart=unless-stopped \
	ich777/dogecoin-core
```
### Webgui address: http://[IP]:[PORT:8080]/vnc.html?autoconnect=true

## Set VNC Password:
 Please be sure to create the password first inside the container, to do that open up a console from the container (Unraid: In the Docker tab click on the container icon and on 'Console' then type in the following):

1) **su $USER**
2) **vncpasswd**
3) **ENTER YOUR PASSWORD TWO TIMES AND PRESS ENTER AND SAY NO WHEN IT ASKS FOR VIEW ACCESS**

Unraid: close the console, edit the template and create a variable with the `Key`: `TURBOVNC_PARAMS` and leave the `Value` empty, click `Add` and `Apply`.

All other platforms running Docker: create a environment variable `TURBOVNC_PARAMS` that is empty or simply leave it empty:
```
    --env 'TURBOVNC_PARAMS='
```

This Docker was mainly edited for better use with Unraid, if you don't use Unraid you should definitely try it!

#### Support Thread: https://forums.unraid.net/topic/83786-support-ich777-application-dockers/
