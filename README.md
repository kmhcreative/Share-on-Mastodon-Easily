# Share-on-Mastodon-Easily

[ [GO DIRECTLY TO BUTTON CONFIGURATOR](https://kmhcreative.github.io/Share-on-Mastodon-Easily/button_configurator.htm) :arrow_right: ]

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

   b. Download and install the script on any website:

   `<script type="text/javascript" language="javascript" src="/your/path/to/some.js></script>`

   c. Download and install the script on your WordPress site by adding the following to your theme's ***functions.php*** file:

   `wp_enqueue_script( 'share-on-mastodon-easily', 'path/to/some.js', '', '1.0', true );`
   
   _Change "path/to/some.js" to either your local path, if you downloaded and installed the script locally, or to the CDN URL to load it remotely._


2. ***MAKE A BUTTON***

   a. ***Use a default share button***  

      Add an element to be turned into the Mastodon Share button:

      `<div class="mastodon" data-style="word"></div>`

      `<div class="mastodon" data-style="icon"></div>`
			
   b. ***Customize a Button***

      THERE IS A [***BUTTON CONFIGURATOR***](https://kmhcreative.github.io/Share-on-Mastodon-Easily/button_configurator.htm) FOR THIS, or you can do it manually like this:   
      
      Add an element to be turned into the Mastodon Share button:  
      
      `<div class="mastodon" data-logo="white" data-color="black" data-size="48"></div>`   
      
      ***Parameters:***
       
      `data-logo : black|full-black|full-white|purple|white|wordmark-black-text|wordmark-white-text`
			
      `data-color: black|white|midnight|blurple|darkblue|lightblue`
			
      `data-size : (any numerical value, this is the pixel height of the button)`

   c. ***Completely Custom Button***   
  
      1. Link to this script on GitHub or download and install it on your website.

      2. Add an element to be turned into the share button with the class name "mastodon" like so:
      
         `<div class="mastodon">Share on Mastodon</div>`

      3. Style the button as you please in your website's stylesheet, for example:
      
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
		
   d. ***Customize This Script***

      1. Download and EDIT this script, then install it on your website.

         Look at the descriptions next to each option in "settings" below.
         
         ```javascript
          /* Settings */   
          some['settings'] = {   
               queryobj    :   '.mastodon',// query to find mastodon share elements   
               titletoo    :   true,       // whether to include the page title and URL   
               rememberme  :   true,       // whether to offer to remember instance or not  
               skipdialog  :   true,       // whether to skip the instance dialog if remembered  
               openapopup  :   true,       // whether to open in a pop-up window, false opens in new tab   
          };
          // if this script is also styling the share button   
          some['logo'] = {    // SVG Mastodon icons/logos using the file names from joinmastodon.org  
               'black'           : '<svg width="74" height="79" viewBox="0 0 74 79". [truncated]...></svg>',  
               'full-black'          : '<svg width="313" height="80" viewBox="0 0 313 80"..[truncated]..></svg>',   
               'full-white'          : '<svg width="313" height="80" viewBox="0 0 313 80"..[truncated]..></svg>',   
               'purple'          : '<svg width="75" height="79" viewBox="0 0 75 79"..[truncated]...></svg>',  
               'white'           : '<svg width="74" height="79" viewBox="0 0 74 79"..[truncated]..></svg>',   
               'wordmark-black-text' : '<svg width="314" height="80" viewBox="0 0 314 80"..[truncated]..></svg>',  
               'wordmark-white-text' : '<svg width="313" height="81" viewBox="0 0 313 81"..[truncated]..></svg>'  
           };
           some['color'] = {   // main color, rollover color, text color (taken from joinmastodon.org examples)  
                'black'    : ['#000000','#333333','#ffffff'],  
                'white'    : ['#ffffff','#f6f6f6','#000000'],   
                'midnight' : ['#17063b','#000000','#ffffff'],  
                'blurple'  : ['#6364ff','#563acc','#000000'],  
                'darkblue' : ['#2f0c7a','#17063b','#ffffff'],  
                'lightblue': ['#858afa','#6364ff','#000000']  
           };
         ```
		
      2. Create your button element(s) in your site code.
	
### NOTES:

Your link/button elements does not have to have an href, the script will get the current window location if no usable href is found on the element itself.

Do not encode the URL before sending it to this script, it will result in an unusable link on Mastodon.	
  
## Changelog
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
