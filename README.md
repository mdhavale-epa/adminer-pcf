# adminer-pcf
A copy of adminer for an easy push to PCF. 


Adminer is a PHP web front end for mysql databases.  You can push this directory to PCF to perform a database import from within PCF itself.

Here’s the process for using adminer:
1)	Replace adminer.sql with your mysql dump.  Note:  LOCK TABLE and UNLOCK TABLE commands won’t work, so you’ll need to strip those out of your dump.  You can remove those like so:

```
sed -i 's/^LOCK\ TABLES/\-\-\ LOCK\ TABLES/g' adminer.sql
sed -i 's/^UNLOCK\ TABLES/\-\-\ UNLOCK\ TABLES/g' adminer.sql
```

2)	Take a look at deploy.sh; it contains the push command you’ll use to push to PCF.  Update the app name as desired.
3)	Push the app.  When it’s successful, the URL will be:  
http://[YOUR_URL]/adminer-4.3.0-en.php
