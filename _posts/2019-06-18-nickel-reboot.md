---
layout: git-wiki-post
title: Nickel Reboot Services Troubleshooting
---

I checked the web apps, open data page, and services this morning after last night’s Nickel reboot and noticed that some layers were not displaying in the web apps and they were also throwing errors in the open data page. So here’s a summary of what I did so we know for next time if any of you face this in the future and want to work through some of these steps during troubleshooting:

1.	Restarted the services in ArcCatalog (right-clicked them and chose restart), but that didn’t fix it.
a.	Initially thought it might be something with Web AppBuilder since I recalled something about having to add the service urls back into the config file in the past as well as sometimes having to download and repost the WAB files in some cases. I didn’t do anything with WAB though and moved onto other troubleshooting.
b.	I also tried clearing my web browser cache just in case it may have been that since that has fixed some issues in the past.

2.	Per Rachel’s suggestion, tried to republish the services since that has helped solve similar issues in the past for her. That did not fix it this time; however, it did give me the following error message when I tried to publish the geologic maps service by overwriting the service. I also was able to publish the same service with a new name without any problems, which said it published successfully instead of giving me this error message. However, the layer did not show up in the web app and I could not view it in the JavaScript or ArcGIS Online viewers on the REST directory so it didn’t really publish successfully after all.


3.	I then googled part of the error message (“the base table definition string is invalid” and it brought up an ESRI support page and a Geonet page as the first two search results that both said something about permissions:
https://support.esri.com/en/technical-article/000018274
https://community.esri.com/thread/58748

4.	At that point, I contacted Brett about it. Nothing jumped out right away as a problem on his end and he suggested a reboot of Placer. He also said he was seeing some errors come through from my failed publishing.

5.	Decided to go ahead and reboot Placer even at the risk of possibly breaking something else. Brett also changed the permissions for nbmgIISPlacer (the IIS Service Account that grabs files on Nicekl) to full permissions in the \Web share and he saw no permissions errors there. He did see many errors similar to the above error message on the layer I was trying to publish as well as at least one other layer.

6.	After this, all services on Placer were working again (yay!). Confirmed in the web apps, open data page, and REST directory Javascript and ArcGIS Online viewers. We were puzzled as to why permissions would have anything to do with it as the reboot of Nickel had nothing to do with permissions.

7.	Then checked the services on geyser in the web apps and REST directory viewers. Some were displaying and most were not.

8.	Before having Brett reboot Geyser, I tried restarting the services as I did in step 1 above. This time that fixed all of them except for one (the NBMG_COGS_Geology_WFS service), which gave me the same error message as above.

9.	I let Brett know about that one service being problematic. At this point he changed permissions on Nickel back to what they were originally (read/only) for security purposes, and read/write was granted in the arcgisoutput directory on Geyser for nbmgIISplacer. Brett was able to restart the NBMG_COGS_Geology_WFS service and it displays correctly now.

10.	A side note is Brett was having trouble testing the services in the ArcGIS Online viewer from the REST directory because his “cross site blocker” was preventing ArcGIS.com from loading information from gisweb. So that was another thing making it difficult for him to test but should be easier in the future.
