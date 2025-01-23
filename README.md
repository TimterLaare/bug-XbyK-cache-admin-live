# XbyK Dancing goat with no caching available bug when running live site and admin in separate domains

This project demonstrates that cache doesn't work when running a live site instance without admin and running an admin instance.

## Installation and setup

1. Create database cmd: `dotnet kentico-xperience-dbmanager -- -s . -d "XbyK.DancingGoat.Admin.Live" -a "Pass@12345" --recreate-existing-database`
2. In visual studio or Rider, go to Properties/launchSettings.json and start profiles 'XbyK_dancing_goat_admin' and 'XbyK_dancing_goat_live'
3. In [admin](http://localhost:65527/admin/) Login with user 'administrator' and password 'Pass@12345' 
4. Set license key via  the URL http://localhost:65527/admin/
5. In Admin -> Configuration -> Channel management -> Dancing Goat Pages: Set website domain to 'localhost:65526'

## Reproduce bug

1. In [admin](http://localhost:65527/admin/webpages-1/en_3/content), make a change in the page builder on the home page
2. Go to the [live site](http://localhost:65526), the change is not visible.
3. Go to Configuration -> Settings -> System and clear cache
4. Change is still not visible on the live site.
5. Restart live site or wait for 5 minutes.
6. Now the change is visible on the live site.

