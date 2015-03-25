Zen Cart Echo Throttled Image Loader v1.0
Version Release Date: 3/19/2015
Publisher: PRO-Webs, Inc
Released for Zen Cart v 1.5.4, but should work with all versions if manually 
installed by file merging.

This installation is considered a beginner level Zen Cart module installation.

Lazy-loading works by only loading the assets needed when the elements 
'would' be in view, which it'll get from the server for you upon request, 
which is automated by simply changing the image src attribute. 
This is also an asynchronous process which also benefits us.

This implementation is a VERY simple usage of echo intended to use Lazy Load
to load Zen Cart product images in indexes and such more effeciently. 
The basis is easily adapted to 
other images by tagging the image like below...

More information on this excellent script is here
http://toddmotto.com/echo-js-simple-javascript-image-lazy-loading/

<img src="blank.gif" data-echo="blank.gif" />


This is fairly browser friendly and should work with most, if not all.


INSTALLATION INSTRUCTIONS
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

1. FIRST MAKE A FULL BACKUP OF YOUR WEBSITE'S FILES AND DATABASE!


***Note, there are 2 versions of the html_output. One (html_output_1.php) is as 
   the script author used to load the loader image, the second (html_output_2.php) 
   does NOT have the loader image. If you choose the second, you can do without
   the loader image or work out how to load in in your CSS such as below.
   
[data-echo]{background:url(../images/spinner.gif) no-repeat center}

No whining and no we cannot work out the CSS for you, sorry.
   

2. Merge the file your selected version of includes\functions\html_output.php.

You will find 2 changes noted with the following text.

//EDITED FOR ECHO

3. Upload the javascript files to your custom template directory in to the
   jscript folder.
   
4. Now add the following to your-template/common/main_page.tpl near the bottom, 
   before the closing body tag to trigger the script.

<?php echo '<script type="text/javascript" src="' .  $template->get_template_dir('.js',DIR_WS_TEMPLATE, $current_page_base,'jscript') . '/echo.js"></script>'."\n";     ?>
    <script>
    echo.init({
      offset: 100,
      throttle: 250,
      unload: false,
      callback: function (element, op) {
        console.log(element, 'has been', op + 'ed')
      }
    });
    </script>
   
** Feel free to play with the options such as the trottle as you wish =)
*Refer to doc here (http://toddmotto.com/echo-js-simple-javascript-image-lazy-loading/) by Todd Motto for more info
      

INFORMATION
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
Core file Edits: Yes
Template Override Changes Yes: addition of jscript_echo.min.js, echo.js and spinner.gif
Database Changes: None


UNINSTALL
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
Remove the package files and file edits in overrides. Removal of the database 
entry is not required to remove this module from use.


SUPPORT
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
Please use the PRO-Webs helpdesk https://pro-webs-support.com/


LICENSING
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
Echo.js (c) Todd Motto
Zen Cart integration module (c) 2015 PRO-Webs, Inc.


VERSION HISTORY
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

1.0 Zen Cart Echo Throttled Image Loader initial release 03/19/2015