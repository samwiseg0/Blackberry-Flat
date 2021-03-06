# Blackberry Flat Themepack (BBF)
CSS changes to many popular web services. Flat and minimal, cleans up unneeded clutter, and fixes many UI issues on desktop/mobile. Custom Icons for Organizr are available within the `Icons` folder. These are not required, but may prove useful.<br/>

## Theme/Icon Requests<br/>
Requests can be made through [Feathub](https://feathub.com/Archmonger/Blackberry-Flat)! <br/>

## Screenshots<br/>
Images are available within the `Screenshots` folder.<br/>

## Installation<br/>
### [Plex](https://www.plex.tv/), [Synclounge](https://github.com/samcm/synclounge), [Deluge](https://deluge-torrent.org/), [Jackett](https://github.com/Jackett/Jackett)<br/>
For services that don't allow native CSS themes you must use Nginx to run these services behind a reverse proxy, then edit your configuration to inject CSS. This can be accomplished with sub_filter (http_sub_module). Replace the `XXXXX` with the name of the theme you are using, which can be found by looking through this repository.<br/>
```
proxy_set_header Accept-Encoding "";
sub_filter '</head>' '<link rel="stylesheet" type="text/css" href="https://archmonger.github.io/Blackberry-Flat/bbf_XXXXX.css"> </head>';
sub_filter_once on;
```
### [Ombi](https://github.com/tidusjar/Ombi)<br/>
1) Navigate to Settings > Configuration > Customization > Custom CSS Link.<br/>
2) Paste in `https://archmonger.github.io/Blackberry-Flat/bbf_ombi.css`.<br/>

_Note: Make sure to have Settings > Configuration > Customization > Preset Themes set to `Please Select` (disabled)._<br/>

### [Filebrowser](https://filebrowser.github.io/)<br/>
1) Navigate to Settings > Profile Settings > Custom Stylesheet.<br/>
2) Paste in `@import "https://archmonger.github.io/Blackberry-Flat/bbf_filebrowser.css";` at the **top** of the text box.<br/>

### [Organizr V2](https://github.com/causefx/Organizr)
1) Navigate to Settings > Customize > Custom CSS.<br/>
2) Paste in `@import "https://archmonger.github.io/Blackberry-Flat/bbf_organizr.css";` at the **top** of the text box.<br/>
3) Navigate to Settings > Customize > Colors and Themes.<br/>
4) Ensure Theme is set to `Organizr` and Style is set to `Dark`.<br/>

**_Optional:_ Better Styling**<br/>
1) Navigate to Settings > Customize > Login Page.<br/>
2) Enable `Minimal Login Screen`.<br/>
3) Navigate to Settings > Customize > Options.<br/>
4) Enable `Alternate Homepage Titles`.<br/>
5) Navigate to Settings > Customize > Notifications.<br/>
6) Change type to `lzi`.<br/>
7) Consider adding `@import "https://archmonger.github.io/Blackberry-Flat/Extras/bbf_organizr_remove_logout_button.css";` to Custom CSS as seen in steps 1 and 2. This is recommended as it is expected that users will log out by clicking on their profile. This is **not** required.<br/>

### [Organizr V2 On Top of Burry](https://github.com/Burry/organizr-v2-plex-theme)<br/>
1) Navigate to Settings > Customize > Marketplace.<br/>
2) Install `Plex Theme` by Grant Burry.<br/>
3) Navigate to Settings > Customize > Colors & Themes > Theme.<br/>
4) Select `Plex`.<br/>
5) Navigate to Settings > Customize > Custom CSS.<br/>
6) Paste in `@import "https://archmonger.github.io/Blackberry-Flat/bbf_organizr_on_top_of_burry.css";` at the **top** of the text box. <br/>
7) Consider adding `@import "https://archmonger.github.io/Blackberry-Flat/Extras/bbf_organizr_remove_logout_button.css";` to Custom CSS as seen in steps 5 and 6. This is recommended as it is expected that users will log out by clicking on their profile. This is **not** required.<br/>

_Note: Make sure NOT to change i=40 to i=60, as Burry recommends. If you have done so already, please revert. Docker users must use `organizrtools/organizr-v2:latest` and install Burry's theme from the marketplace._<br/>

### [Organizr](https://github.com/causefx/Organizr) [Custom Icons](https://github.com/Archmonger/Blackberry-Flat/tree/master/Icons)<br/>
1) Navigate to Settings > Tab Editor > Tabs<br/>
2) On each individual tab, click `Edit`.<br/>
3) For `Tab Image`, paste in `https://archmonger.github.io/Blackberry-Flat/Icons/bbf_XXXXX.png`. Replace the `XXXXX` with the name of the icon you are using, which can be found by looking through this repository's `Icons` folder.<br/>

**_Optional:_ Stylized Logout Button**<br/>
1) Navigate to Settings > Customize > Custom CSS.<br/>
2) Paste in `@import "https://archmonger.github.io/Blackberry-Flat/Extras/bbf_organizr_logout_button.css";` at the **top** of the text box. <br/>

## More Information<br/>
**What is "in Organizr"**<br/>
Most BBF themes come in a In Organizr variant, which allows them to seemlessly fit in to the Organizr theme `bbf_organizr.css` and `bbf_organizr_on_top_of_burry.css` without appearing as if they are an iFramed service. This is accomplished by removing logos, modifying the navbar, as well as other miscellaneous in-site tweaks depending on the specific service. On occasion, some functionality may be removed in order to maintain theme consistency and be optimized for SSO-only usage. For example in the case of Ombi, this can be seen with the removal of the login screen's rotating backgrounds, smaller navbar, deletion of the loading bar, removal of the current user's username, and removal of the log out menu.<br/>

**Subfilter is set up exactly as above, but themes are not working!**<br/>
Subfilter will not function while gzip is enabled. Please confirm whether or not gzip is enabled within nginx. If so, disable gzip.<br/>
_Note to Deluge users when subdir reverse proxying on a Windows host machine:_ Deluge on Windows currently has issues with reverse proxies. If you wish to keep deluge on your domains subdir, you will need to copy the code found in `bbf_deluge.css` to the end of deluge's default CSS file. This can be found in `C:\Program Files (x86)\Deluge\deluge-1.3.15-py2.7.egg\deluge\ui\web\css`. Alternatively, you can move Deluge to a subdomain and use subfilter as demonstrated in the [installation instructions](https://github.com/Archmonger/Blackberry-Flat#plex-synclounge-deluge-jackett) above.<br/>

**Other themes not working?**<br/>
Please clear browser cache. If using Cloudflare, also clear Cloudflare cache.<br/>

**BBF Plex**<br/>
For those who do not want OrganizrV2 specific view enhancements in `bbf_plex.css`, such as hiding the user icon, please use [Improved Plex Mobile CSS](https://github.com/Archmonger/Improved-Plex-Mobile-CSS).<br/>

**Upcoming**<br/>
_Theme Queue:_ Tautulli, Transmission, Sonarr/Radarr/Lidarr/Logarr/*-arr*, Flood (rTorrent WebUI), Rutorrent.<br/>
_Mobile Queue:_ Jackett mobile, Deluge mobile.<br/>
_Icon Queue:_ Handled via popularity on Feathub.

**Last Tested**<br/>

| Service | Last Tested Version | Requires Nginx Subfilter |
| ------------- | :-------------: | :-------------: |
| Plex | 1.13.9.5456 | YES |
| Ombi | 3.0.3919 | NO |
| Synclounge | 2.0.0 | YES |
| Filebrowser | 1.9.0 | NO |
| Deluge WebUI | 1.3.15 | YES |
| Jackett | 0.10.504.0 | YES |
| Organizr | 2.0.0-beta.800 | NO |

## Feathub Requests<br/>
[![Feature Requests](http://feathub.com/Archmonger/Blackberry-Flat?format=svg)](http://feathub.com/Archmonger/Blackberry-Flat)<br/>

## **Credits**<br/>
Special thanks to [@Leram84](https://github.com/leram84) and [@goldenpipes](https://github.com/goldenpipes)<br/>
Jacket, Calendar day 15 icon, Security Camera, Piggy bank with Dollar Coins, Multiple users silhouette, Television, Submarine, Crane, Books stack of three, Home Icon Silhouette, Avocado, Newsletter, 3D, Open book, Open book top view, Music, Headphones with music, and Raindrop made by [Freepik](https://www.flaticon.com/authors/freepik) from www.flaticon.com is licensed by [CC 3.0 BY](https://creativecommons.org/licenses/by/3.0/)<br/>
Folder made by [Kiranshastry](https://www.flaticon.com/authors/kiranshastry) from www.flaticon.com is licensed by [CC 3.0 BY](https://creativecommons.org/licenses/by/3.0/)<br/>
Headphones made by [Pixel Buddha](https://www.flaticon.com/authors/pixel-buddha) from www.flaticon.com is licensed by [CC 3.0 BY](https://creativecommons.org/licenses/by/3.0/)<br/>
Down arrow, Bitcoin Logo, and Utorrent made by [Dave Gandy](https://www.flaticon.com/authors/dave-gandy) from www.flaticon.com is licensed by [CC 3.0 BY](https://creativecommons.org/licenses/by/3.0/)<br/>
RSS symbol made by [Pixel Perfect](https://www.flaticon.com/authors/pixel-perfect) from www.flaticon.com is licensed by [CC 3.0 BY](https://creativecommons.org/licenses/by/3.0/)<br/>
Screwdriver and Wrench Crossed made by [Elegant Themes](https://www.flaticon.com/authors/elegant-themes) from www.flaticon.com is licensed by [CC 3.0 BY](https://creativecommons.org/licenses/by/3.0/)<br/>
Sofa and Cloud made by [Smashicons](https://www.flaticon.com/authors/smashicons) from www.flaticon.com is licensed by [CC 3.0 BY](https://creativecommons.org/licenses/by/3.0/)<br/>
Video Camera and Support made by [Good Ware](https://www.flaticon.com/authors/good-ware) from www.flaticon.com is licensed by [CC 3.0 BY](https://creativecommons.org/licenses/by/3.0/)<br/>
Wireless connection made by [srip](https://www.flaticon.com/authors/srip) from www.flaticon.com is licensed by [CC 3.0 BY](https://creativecommons.org/licenses/by/3.0/)<br/>
Toolbox and Desktop Computer made by [itim2101](https://www.flaticon.com/authors/itim2101) from www.flaticon.com is licensed by [CC 3.0 BY](https://creativecommons.org/licenses/by/3.0/)<br/>
Check, Comment, Sign Out Alt, Cog, and Cogs made by [fontawesome](https://fontawesome.com/) from www.fontawesome.com is licensed by [CC 4.0 BY](https://creativecommons.org/licenses/by/4.0/)<br/>
Blur Light and Blur Noise made by [Plex](https://www.plex.tv/)<br/>
All logos found within `Archmonger/Blackberry-Flat/Icons` belong to their respective owners and Archmonger does not claim copyright, trademark, or ownership of these logos. Archmonger claims no endorsement or affiliation to the services, repositories, teams, groups, and/or companies referenced within `Archmonger/Blackberry-Flat`.<br/>
