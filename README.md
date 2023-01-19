# Share-on-Mastodon-Easily

[ [GO DIRECTLY TO BUTTON CONFIGURATOR](https://kmhcreative.github.io/Share-on-Mastodon-Easily/button_configurator.htm) --> ]

There are literally THOUSANDS of different Mastodon websites on different servers and each is called an “instance.”  Most of them are “federated” with each other, and other platforms that support the AcitvityPub protocol, because the entire thing is decentralized by design.  But that means you have no way to guess which “instance” any visitor to your website might be on.  So, before they can share anything to their Mastodon account you have to FIRST ask them which instance they use.  That’s primarily what this “Share On Mastodon Easily” (S.O.M.E.) script does.  It lets you share some link somewhere. 

This script converts an HTML element with the class name "mastodon" into a share button.  When a visitor presses it a pop-up/tab is created on the fly to ask them what Mastodon instance they are on, and gives them an option to remember it so when they return to your site they are not asked again.

<img src="https://kmhcreative.github.io/Share-on-Mastodon-Easily/Mastodon_Instance_PopUp.png" width="400"/> <img src="https://kmhcreative.github.io/Share-on-Mastodon-Easily/Mastodon_Instance_PopUp2.png" width="400"/> <img src="https://kmhcreative.github.io/Share-on-Mastodon-Easily/Mastodon_Publish_Window.png" width="400"/>

## HOW TO USE THIS SCRIPT    

1. ***LOAD THE SCRIPT***

Include the "some.js" script on your website, preferably in the `<HEAD>` block, but anywhere should still work.

  a. ***LOAD USING CDN*** (_RECOMMENDED_)   
  
  The following will load the script using [jsDelivr CDN](https://www.jsdelivr.com/):   
  
  `<script type="text/javascript" language="javascript" src="https://cdn.jsdelivr.net/gh/kmhcreative/Share-on-Mastodon-Easily@main/some.js"></script>`   
  
  The server cache is updated every 12 hours, but any cached version of the script in a user's browser won't expire for a full week.  If you're not planning on modifying the script and don't mind not getting updates immediately, please use the CDN.   
  
  b. [Download](https://github.com/kmhcreative/Share-on-Mastodon-Easily/archive/refs/heads/main.zip) and install the script on any website:   
  
  `<script type="text/javascript" language="javascript" src="/your/path/to/some.js></script>`   
  
  c. Enqueue in WordPress    
  
  [Download](https://github.com/kmhcreative/Share-on-Mastodon-Easily/archive/refs/heads/main.zip) and install the script on your WordPress site, or link to the script using the CDN, by adding the following to your theme's ***functions.php*** file:    
  
  `wp_enqueue_script( 'share-on-mastodon-easily', 'path/to/some.js', '', '1.0', true );`    
  
  _Change "path/to/some.js" to either your local path, if you downloaded and installed the script locally, or to the CDN URL to load it remotely._


2. ***MAKE A BUTTON***

Include an element in your page with the class name "mastodon" and it will be converted into a share button by the "some.js" script.

  a. ***Default Buttons***  
  
  Add an element to be turned into the Mastodon Share button using the "data-style" attribute:  
  
  `<div class="mastodon" data-style="word"></div>`  
  
  `<div class="mastodon" data-style="icon"></div>`  
			
  b. ***Customized Button***   
  
  THERE IS A [***BUTTON CONFIGURATOR***](https://kmhcreative.github.io/Share-on-Mastodon-Easily/button_configurator.htm) FOR THIS, or you can do it manually. Add an element to be turned into the Mastodon Share button:    
  
  `<div class="mastodon" data-logo="white" data-color="black" data-size="48"></div>`  	
  
  ***Parameters:***   
    
  `data-logo : black|full-black|full-white|purple|white|wordmark-black-text|wordmark-white-text`  
    
  `data-color: black|white|midnight|blurple|darkblue|lightblue`   
    
  `data-size : (any numerical value, this is the pixel height of the button)`    
     
  c. ***Bespoke Button***   
    
  i. Link to this script through the [CDN](https://cdn.jsdelivr.net/gh/kmhcreative/Share-on-Mastodon-Easily@main/some.js) or [download](https://github.com/kmhcreative/Share-on-Mastodon-Easily/archive/refs/heads/main.zip) and install it on your website.    
    
  ii. Add an element to be turned into the share button with the class name "mastodon" like so:  
    
  `<div class="mastodon">Share on Mastodon</div>`    
    
  iii. Style the button as you please in your website's stylesheet, for example:    
	
  ```css    
    .mastodon {    
	display: inline-block;   
	font-size: 14px;   
	color: white;   
	background-color: lightblue;   
	border-radius: 4px;   
	border: 1px solid darkblue;   
    }   
  ```

3. ***CUSTOMIZE SCRIPT***_(Optional)_    

Just about all the internals of the script are exposed and can be manipulated after the script has loaded. 

For example, let's say you want the share window to open in a new tab instead of a pop-up window, and you want it to ask visitors for their instance every time they visit your site instead of offering to store it.  Somewhere AFTER the "some.js" script was loaded include a script block like this:   

  a. ***CHANGE SETTINGS***   
	
  ```javascript
  <script type="text/javascript">
     some.settings.openapopup = false;
     some.settings.rememberme = false;
  </script>
  ```   
	
  b. ***CHANGE COLORS***   
  
  Let's say you decide to add a color option for the holidays:   
  
  ```javascript
   <script type="text/javascript">
     some.color.xmas = ['red','green','white'];
   </script>
  ```   
	
  Then you'd just need to include `data-color="xmas"` in your button element attributes.  You could also redefine an existing color.   
	
  c. ***CHANGE LANGUAGE***   
	
  The share window is constructed "on-the-fly" so all the text used in it can be changed as well.  For example you could change it Spanish like this:
	
  ```javascript
  <script type="text/javascript">
    some.text.heading = “Compartir en Mastodonte”;
    some.text.label = “URL de su instancia”;
    some.text.checkbox = “Recordar mi instancia en este sitio web”;
    some.text.close = “Cerrar”;
    some.text.share = “¡Cuota!”;
    some.text.whatis = “¿Qué es Mastodonte?”;
    some.text.github = “Mastodonte en GitHub”;	
  </script>
  ```
	
  d. ***CHANGE BUTTON IMAGES***
	
  The script comes pre-loaded with the SVG images for all the official Mastodon logo and icon variations. But if you wanted to define something else you could do it like this:
	
  ```javascript
  <script type="text/javascript">
    some.logo['dot-dot-dot'] = '<svg width="75" height="75".....></svg>
  </script>
  ```
  
  e. ***CHANGE BUTTON & POPUP FOR OTHER PLATFORMS***
  
  In theory the Share Button *should* work with ANY social media platform that supports the ActivityPub protocol. Visitors to your website should be able to enter the instance URL for any ActivityPub site, whether it's Mastodon, Plemora, Misskey, Freindica, etc.
  
  The "[activitypub.js](https://github.com/kmhcreative/Share-on-Mastodon-Easily/blob/main/activitypub.js)" modifier script is in the main repository that changes the buttons and pop-up, in this case to show "ActivityPub" (yes I know it's a *protocol* not a *platform*, it's just a generic proof-of-concept to show you how to do it).
  
  f. ***FULL CUSTOMIZATION***
  
  If you download the script to do a local installation you can, of course, customize it any way you like.  Including all of the aforementioned customization, which could be done in the "some.js" script if you liked.
	
### NOTES:
* If you are defining new keywords with dashes in the names you need to do it inside quotes (as shown above for "Change Button Images") because trying to define that name in dot notation will throw an error.

* Your link/button elements does not have to have an href, the script will get the current window location if no usable href is found on the element itself.

* Do not encode the URL before sending it to this script, it will result in an unusable link on Mastodon.

* Button Configurator translations were done with Google Translate, they may not be accurate.  If you can fix any of them please do and submit a pull request for your changes.	

### CODE:

Get the code for this project, submit bugs, issues, suggestions, fork it, whatever!

[https://github.com/kmhcreative/Share-on-Mastodon-Easily](https://github.com/kmhcreative/Share-on-Mastodon-Easily)
  
## Changelog
Version 1.4
* Made the footer links customizable as well to support...
* Optional "ActivityPub" modifier script, if you want your share buttons to be platform agnostic.

Version 1.3
* Made share window text into variables so they can be localized.
* Added multiple language options to the Button Configurator.

Version 1.2  
* Changed `window.onload` to `window.addEventListener('load'..)` to prevent conflicts with any other onload events.
* Removed instructions from the script it self and placed them in this README file.
* Moved from Gist to GitHub Repository so JSDelivr CDN can be used to load script.

Version 1.1
* Added code to generate buttons with SVG images based on HTML element `data-` attributes.

Version 1.0
* Initial release, attaches click event listener to any HTML element with 'mastodon' class name to launch instance question pop-up window.
  
## Contributors
  
Author: 	 K.M. Hansen <software@kmhcreative.com>
Author URI:  http://www.kmhcreative.com
	
## License: 	 
***GPLv3*** - License URI: [http://www.gnu.org/licenses/gpl-3.0.html](http://www.gnu.org/licenses/gpl-3.0.html)

The Mastodon logos and icons are the property of [Mastodon gGmbH](https://joinmastodon.org/about), a German non-profit company.  

This is not an official Mastodon project.
