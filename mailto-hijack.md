# brave mailto:url hijack


## email hiJacked by Tutanota !

When I click on a mailto url 
I am redirected to : <https://mail.tutanota.com/login?requestedPath=...>

the command ``ack -i tutanota -l`` gives me: 

```
.mozilla/firefox/ojv3m6li.default-release/blocklist.xml
.cache/gnome-software/odrs/ratings.json
.config/BraveSoftware/Brave-Browser/Default/Network Persistent State
.config/BraveSoftware/Brave-Browser/Default/Preferences
```

and here is the culprit :
```
cat .config/BraveSoftware/Brave-Browser/Default/Preferences | json_xs -t yaml | less
```

```
...
  - default: true
    last_modified: '13243178610227123'
    protocol: mailto
    url: https://mail.tutanota.com/mailto#url=%s
...
```

### Solution :

 * <https://community.brave.com/t/change-default-mailto-link-behvior/123117> or
 * for gmail <https://community.brave.com/t/how-do-i-set-mailto-to-gmail/68907>
 * go to  <brave://settings/handlers> and remove the wrong url handlers
 * set mailto protocol in
   brave settings handlers to "https://mail.google.com/mail/?extsrc=mailto&url=%s"
 * login to <https://gmail.com> and click on the handler icon in the address bar:

   ![runner](https://cloudflare-ipfs.com/ipfs/QmSBLLYHxm8dXaF4igg9ZHbnriZcApXBtFR3aNNSAjjY25/hdlr.png)

 * <brave://settings/content/siteDetails?site=https%3A%2F%2Fmail.google.com>
