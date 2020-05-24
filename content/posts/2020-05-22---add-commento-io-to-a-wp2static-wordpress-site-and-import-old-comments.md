---
title: "Add Commento.io to a WP2Static Wordpress site and import old comments"
date: "2020-05-22T00:23:24.000Z"
template: "post"
draft: false
slug: "add-commento-io-to-a-wp2static-wordpress-site-and-import-old-comments"
category: "Dev web"
tags: 
  - "Français"
  - "Uncategorized FR"
  - "Dev web"
  - "JAMstack"
  - "Sites statiques"
description: "How to setup commento.io to get comments on a WP2static'ed Wordpress website"
---



First we will hide the Wordpress native comments. Add this the style.css of the child theme. Or to the "Custom CSS" of your theme.

```css
/* Hide comment box because Wordpress options don't work and I don't want to search for hours */
div.comment-entry.post-entry {
    display: none;
}
```



Sign up for commento : [https://commento.io/signup](https://commento.io/signup)



Create a child theme if you don't already have one and add this to your functions.php file

```php
function load_commento( $content ) {    
    if( is_single() ) {
        $content .= '<script defer src="https://cdn.commento.io/js/commento.js"></script><div id="commento"></div>';
    }
    return $content;
}
add_filter( 'the_content', 'load_commento' );
```

The `is_single` will make sure we only load commento on single post types

On the dev domain, a message will be displayed 
>This domain is not registered with Commento.

This is ok, it's just because of dev. but it will display fine on the live domain

You can get rid of the warning by adding the dev domain as a new domain on commento

![Wordpress WP2Static Commento.io and dev domain](/media/2020-05-22---add-commento-io-to-a-wp2static-wordpress-site-and-import-old-comments/2020-05-21-at-11.55.10.png)

We can now go on with the general settings configuration on the commento website

By default the text area height was not enough because of my theme (enfold)
added to Enfold settings -> General styling -> Quick CSS

![Wordpress WP2Static Commento.io enfold theme textarea too small](/media/2020-05-22---add-commento-io-to-a-wp2static-wordpress-site-and-import-old-comments/2020-05-21-at-11.57.57.png)

```css
/* Commento text area input wasn't tall enough by default. 
Because of Enfold theme's base.css. This will fix it */
#commento-textarea-root {
    min-height: 130px !important;
}
```

`130px` is the default that should have been loaded by commento's css

I personaly turned moderation settings -> Email Schedule -> Whenever a new comment is created as new comments do nothappen too often and I'm happy to know whenever there's a new one.

We may now test the install by posting a new comment on an article

And this will be also usefull for exporting comments , we will modify the json file, add our old worpdress comments and import them to commento

Go to General -> Export data tab -> Intiate data export. You will receive an email form commento. Click on the link. unzip the file. Open the json

Commento does not support importing wordpress comments we wil have to use a workaround. Check if this feature has been developed first [https://gitlab.com/commento/commento/-/issues/202](https://gitlab.com/commento/commento/-/issues/202)

Go ahead, signup for Disqus, select I want to install Disqus on my site. Select the basic plan and configure your Disqus account.

In wordpress admin go to Tools -> Export, select posts [https://dev.gaelbillon.com/wp-admin/export.php](https://dev.gaelbillon.com/wp-admin/export.php)

![Wordpress WP2Static Commento.io export Wordpress comments XML](/media/2020-05-22---add-commento-io-to-a-wp2static-wordpress-site-and-import-old-comments/2020-05-21-at-12.50.59.png)

Go to https://import.disqus.com/group/gaelbillon-com/19991XXXXXXXXXXXXXX/ and import the xml file.
More info here : https://help.disqus.com/en/articles/1717131-importing-comments-from-wordpress#automatic

![Wordpress WP2Static Commento.io import Wordpress xml comments to Disqus](/media/2020-05-22---add-commento-io-to-a-wp2static-wordpress-site-and-import-old-comments/2020-05-21-at-12.54.19-1030x671.png)

You should now see the imported comments here [https://gaelbillon-com.disqus.com/admin/discussions/](https://domain-com.disqus.com/admin/discussions/)
Click on export on the left sidebar

You will recevie ane mail with a link. Paste the link in the commento's import comment's Disqus tab. Commento will load the comments.

I met an `SSL ERR_CERT_DATE_INVALID` error following this link so i downaled the gz file, uploaded it to the root of my website and pasted this url in commento's import field : [http://dev.gaelbillon.com/domain-com-2020-05-21T10\_57\_32.690107-all.xml.gz](http://dev.gaelbillon.com/domain-com-2020-05-21T10\_57\_32.690107-all.xml.gz)

Commento should now display the imported comments. Go to a post where you know there are comments and check if they are correctly displayed. in my case : [https://gaelbillon.com/posts/prendre-des-photos-en-dng-raw-avec-le-parrot-anafi-et-pix4d-capture/](https://gaelbillon.com/posts/prendre-des-photos-en-dng-raw-avec-le-parrot-anafi-et-pix4d-capture/)

It works !

![Wordpress WP2Static Commento.io comments username fixed](/media/2020-05-22---add-commento-io-to-a-wp2static-wordpress-site-and-import-old-comments/2020-05-21-at-14.45.01.png)

Import the comments also to the live domain.

When I first imported the xml/gz file to commento the comments showed up on the dev site but every comment was made by anonymous. 
So we'll need to edit the xml file. 
Prettify it first because it's a bit flat right now : https://www.samltool.com/prettyprint.php

Search and replace `<isAnonymous>true</isAnonymous` to `<isAnonymous>false</isAnonymous`
In each every `<author>` tag, make sure there is a `<username>` tag. Add it if not present. It must look like this :
```
    <author>
      <name>Ben</name>
      <isAnonymous>false</isAnonymous>
      <username>Ben</username>
    </author>
```

When all changes are done, gzip the file. On a mac :

```bash
gzip -c domain-com-2020-05-21T10\_57\_32.690107-all.xml > domain-com-2020-05-21T10\_57\_32.690107-all.xml.gz
```

Then reupload it to the website root 
[https://dev.gaelbillon.com/domain-com-2020-05-21T10\_57\_32.690107-all.xml.gz](https://dev.gaelbillon.com/domain-com-2020-05-21T10\_57\_32.690107-all.xml.gz)

You can go to danger zone and delete all comments, and re-import as much as you want

And re-import the comments

That's it for the dev site. On to the live site
We need to modify again the xml file. Change the link tags in each thread tag in the xml to change the dev url to live. Search and replace
`<link>/posts/ -> <link>https://domain.com/`

Not sure if this is really required is but better be safe.

![Wordpress WP2Static Commento.io import xml disqus search replace](/media/2020-05-22---add-commento-io-to-a-wp2static-wordpress-site-and-import-old-comments/2020-05-21-at-14.44.37-1030x666.png)
