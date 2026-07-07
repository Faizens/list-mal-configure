#Custom MAL Theme

A customizable MyAnimeList profile theme based on Grid Style 5 (2023 Update), originally created by Takana_no_hana, with edits by Shishio-kun and Valerio_Lyndon.

Learn more about customizing this layout style on the official MAL thread.

Setup


Copy the contents of theme.css.
Paste it into your MyAnimeList profile's custom CSS box (Profile → Edit Profile → CSS).
Save.


Fix sharper / brighter preview pics

At the top of theme.css, replace USERNAME in the first two @\import lines with your own MAL username:

css@\import "https://malscraper.azurewebsites.net/covers/anime/USERNAME/presets/dataimagelinkbefore";
@\import "https://malscraper.azurewebsites.net/covers/manga/USERNAME/presets/dataimagelinkbefore";

Layout problems

If you run into layout issues, check this troubleshooting thread: https://myanimelist.net/forum/?topicid=439897

Customization Guide

Wallpapers

To change a background image, delete the URL inside the url(...) parentheses for the relevant status section, upload your new background to Imgur (or similar), and paste the direct image link (or the original GIF link if animated) in its place, then save.

Each list status has its own wallpaper rule:


All Anime/Manga
Currently Watching
Completed
On Hold
Dropped
Planned


Preview pics / covers

To customize an individual title's preview image:


Find the anime or manga's ID number from its MAL URL (e.g. Code Geass is /anime/1575/).
Copy this block, swap in the ID and your image link, and paste it under the "PREVIEW PICS / COVERS" section:


css.data.image a[href^="/anime/YOUR_ID/"]:before {
	background-image: url(YOUR_IMAGE_LINK);
}


Repeat for each title you want to customize (use /manga/ instead of /anime/ for manga entries).


Banner avatar

Under Banner Avatar, adjust:


background-position — change center to left or right to reposition the image.
background-size — change cover to contain, or remove it, to change how the image fills the space.


Banner quote

Edit the text inside the content: "..." value under the Banner Quote section to change the quote shown on your profile banner.

Banner backgrounds & height

Each status section (All, Watching, Completed, On Hold, Dropped, Planned) has its own banner background image and height. If the full image isn't visible, increase the height and/or change cover to contain.


Tip: You may want to adjust the cover pic vertical offset (below) after changing banner heights.



Cover pic / header vertical position

The rule under Cover Pic / Header Vertical Offset (top: 0px) moves the anime preview pics and status headers (Completed, etc.) up or down:


Increase the value (e.g. 100px) to move them down.
-480px moves them up flush against the banner buttons.


To apply this only to a specific status list instead of all of them, prefix the selector with a status query, e.g.:

css[data-query*='"status":1'] .list-unit .list-status-title .text,
[data-query*='"status":1'] .list-item {
	top: 0px;
}

Status number reference: 1 = Watching, 2 = Completed, 3 = On Hold, 4 = Dropped, 6 = Planned, 7 = All.

Banner button backgrounds

Each status button has two images:


The first (background-image) is the default black & white image.
The :hover / .on variant is the animated (GIF) image shown on hover or when selected.


Swap either link to use your own art.

Side renders (left & right)

For each status section's footer:before (left) / footer:after (right) rules:


left / right — position, accepts negative values.
width — resizes the render; set to 0% to remove it entirely.
background-image — swap in your own render.


Container colors

Colors are set using rgba(). Generate custom colors with a tool like hexcolortool.com, then replace the values below:

SelectorAffects.list-unitEntire table.status-menu-containerBanner.list-table .list-table-dataDefault container behind an anime/manga entry.list-table .list-table-data:hoverContainer on hover.list-menu-float .icon-menuUpper-left menu.headerTop header gradient

Set the last value (alpha) to 0 to make a layer fully transparent.

Custom cursor

See more custom cursor options here: https://myanimelist.net/forum/?topicid=1903808

Greyscale category buttons

The status buttons are greyscale by default and turn to color on hover/selection. Delete the Greyscale Custom Category Buttons block entirely if you'd rather keep them in color at all times.

Adding your own CSS

Add any additional custom rules at the very bottom of theme.css, below the ADD NEW CODE BELOW THIS LINE marker.

Credits


Original layout: Takana_no_hana
Edits: Shishio-kun, Valerio_Lyndon
Preview pic scraper: malscraper.azurewebsites.net
