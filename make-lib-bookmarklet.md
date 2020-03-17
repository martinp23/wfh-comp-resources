UNSW has a proxy through which logged-in users can access journal articles off-site.

This page describes how to make a button for your bookmarks bar which will reload the active tab using the proxy.

### Instructions for Chrome

1. Right click on the Bookmark Bar and press 'Add page...'
2. Change the name to: "Reload using UNSW lib"
3. Change the path to `javascript:void(location.replace('http://'+location.host+'.wwwproxy1.library.unsw.edu.au'+location.pathname))`
4. Press save
5. To test: go to a journal article and click the button. The page should reload using the UNSW proxy, and you may be asked to log in. You should then have access to the full article, if UNSW has a subscription.
