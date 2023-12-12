# Domain Setup Example   
   
![[files/image.png]]
I make my tree roots based on the game server so `mc` for Minecraft, `astro` for Astroneer, `factorio` for ya know….
If your stuff is setup differently like maybe its multiple servers across different machines hosted by different people
Then it would be more vertical. A lot more A records defining IP's with SRVs for each server running on those hosts.
It also kinda comes down to how the game server itself deals with domains.   
Minecraft can parse SRV records
Terraria doesnt like any domains whatsoever
Factorio couldnt give a shit either way
   
Simply put, it just gives nice human words for your IP. It hides it from retards but anyone smart enough to know what Ping does aside from just pinging for connection, can find your IP.   
Hence Cloudflare. This will help stop the baddies if there are any. Hiding your IP is a lot more complicated as it requires proxies and you're not gonna wanna deal with that.   
ah   
   
