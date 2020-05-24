---
title: "Intercepter un évènement swipe sur un panel avec Sencha Touch"
date: "2013-12-19T18:21:06.000Z"
template: "post"
draft: false
slug: "intercepter-un-evenement-swipe-sur-un-panel-avec-sencha-touch"
category: "Applications mobiles"
tags: 
  - "Applications mobiles"
  - "event"
  - "Français"
  - "sencha architect"
  - "sencha touch"
  - "swipe"
  - "touch"
description: ""
socialImage: "/media/2013-12-19---intercepter-un-evenement-swipe-sur-un-panel-avec-sencha-touch/swipe-sencha.jpg"
---


```javascript
element.on({
     swipe: function(e, node, options){
         if(e.direction == "left") {
              console.log('swipe left');
         } else if(e.direction == "right"){
              console.log('swipe right');
         }
     }
 });
```

Et avec Sencha Architect, il faudra utiliser au préalable l'évènement onPanelPainted :

[![sencha architect listen swipe event](/media/2013-12-19---intercepter-un-evenement-swipe-sur-un-panel-avec-sencha-touch/Screen-Shot-2013-12-18-at-12.38.56.png)](/posts/wp-content/uploads/2013/12/Screen-Shot-2013-12-18-at-12.38.56.png)
