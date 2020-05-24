---
title: "Photogrammetry with Parrot Anafi and Pix4D Capture"
date: "2018-11-21T17:42:22.000Z"
template: "post"
draft: false
slug: "photogrammetry-with-parrot-anafi-and-pix4d-capture"
category: "Uncategorized"
tags: 
  - "Anafi"
  - "English"
  - "Pix4D"
  - "pll_5cdae292741fc"
  - "Uncategorized"
description: "One of the simplest, most intuitive and compact solution for photogrammetry at the moment. A very good volume/weight/price/image quality ratio."
---

## Flight preparation

Flight planning is very simple thanks to the intuitive interface ofPix4D Capture. The flight plan is ready in a few minutes and all the necessary settings are present.

![Photogrammetry with Parrot Anafi and Pix4D Capture flight plan on iPhone 5S](/media/2018-11-21---photogrammetry-with-parrot-anafi-and-pix4d-capture/Photogrammetry-with-Parrot-Anafi-and-Pix4D-Capture-flight-plan-on-iPhone-5S-1030x580.jpg)

It is possible to download maps (Mapbox or Apple) for offline use once on site in case there is no internet access. To do this, simply open Pix4d and go to the area you want to cache and wait until the map is correctly loaded (until all the tiles on the map have appeared in their best possible resolution)

## During the flight

The flight went very well and even if the UAV did not go very far (no more than 300 meters) the video feedback was quite stable despite some one-second freezes when the UAV passed behind the building and a very low definition video feedback from time to time (better than freezes), overall the flight went perfectly, it's easy to switch between the map and the video feedback to see the progression of the UAV and any obstacles that would appear on the road. Especially since the Anafi is programmed by Pix4D to keep the "nose" facing forward.

> You will still have to be careful not to touch the radio control sticks when touching the phone screen, which would result in switching back to manual piloting mode and pausing the mission. Not a major problem since you simply have to press "Resume" to continue the automatic flight.

The video feedback does not make a black screen with each trigger but Pix4D indicates the pictures taken on the card, well almost, Pix4D displays the position at which the trigger command was sent but the app does not receive any feedback confirming that the picture was taken.

![Photogrammetry with Parrot Anafi and Pix4D Capture video feedback](/media/2018-11-21---photogrammetry-with-parrot-anafi-and-pix4d-capture/Photogrammetry-with-Parrot-Anafi-and-Pix4D-Capture-video-feedback-1030x580.jpg)

> Upon landing, you must remember to point the camera towards the sky to protect it from everything that will fly when the drone lands, especially if it is on sand or gravel. Pix4D does not add a "Camera at +90°" waypoint before landing. Even if you touch the gimbal's tilt trigger, the landing will continue and the Anafi will not return to manual piloting mode.

During the flight you can follow all the information on the status of the Anafi: Percentage of the battery, speed, altitude, number of satellites, space available on the SD card and distance to the home or smartphone point. To display all this information it is preferable to have a screen larger than 4", it is a bit narrow on an iPhone 5S and some information is hidden.

![Photogrammetry with Parrot Anafi and Pix4D Capture flight hidden informations on iPhone 5S](/media/2018-11-21---photogrammetry-with-parrot-anafi-and-pix4d-capture/Photogrammetry-with-Parrot-Anafi-and-Pix4D-Capture-flight-hidden-informations-on-iPhone-5S-1030x580.jpg)

## After the flight

The Anafi landed with 23% of battery power after a 19 minutes and 51 seconds flight at 3°c

With the default settings of Pix4D Capture, uploading photos to the phone is automatically started as soon as you land. There was a slight bug during the download of the images but it resumed on its own afterwards and all the images were copied.

> Remember to keep some battery for photo transfer. For 359 photos (1.96 GB, average 5.46 MB / photo) with an iPhone 5S it takes about 20 minutes. It should be enough most of the time, but if you land at 2% not sure. Automatic photo transfer can be disabled in the application settings.

![Photogrammetry with Parrot Anafi and Pix4D Capture downloading images after flight](/media/2018-11-21---photogrammetry-with-parrot-anafi-and-pix4d-capture/Photogrammetry-with-Parrot-Anafi-and-Pix4D-Capture-downloading-images-after-flight-1030x580.jpg)

The images downloaded by Pix4D Capture and saved on the phone are correctly geotaged. On the SD card of the Anafi we find almost exactly the same thing, the geotagged JPG photos. Only one small difference, on the SD card there are 3 more pictures, including 2 taken after the flight, during the transfer of the pictures and the third additional, well I don't know... Probably during the flight, it may be due to the involuntary pause during the automated flight when I accidentally touched a stick on the radio control. Not a big issue anyway. The pictures will just need to be discarded, be it manually, or by the photogrammetry software.

The photos can then be uploaded to the Pix4D cloud to perform the calculations and rendering directly on pix4D servers. Uploading photos to the Pix4D cloud requires a valid license. It is possible to get a 15-day trial license by creating a Pix4D account here: [https://account.pix4d.com/signup](https://account.pix4d.com/signup). Then download the Pix4D software and click on the "Click for trial" button at the top right of the interface.

\[caption id="attachment\_1043" align="aligncenter" width="750"\]![Photogrammetry with Parrot Anafi and Pix4D Capture upload images Pix4D cloud](/media/2018-11-21---photogrammetry-with-parrot-anafi-and-pix4d-capture/Photogrammetry-with-Parrot-Anafi-and-Pix4D-Capture-upload-images-Pix4D-cloud-1030x580.jpg) With the default settings, downloading photos from the Anafi starts immediately after landing\[/caption\]

## No RAW

Pix4D only backs up JPGs, the Pix4d Mapper software does not know how to use RAW. It's a shame we would have liked to be able to recover the DNGs from the Anafi and convert them into geotagged TIFFs that Pix4d Mapper can read. It seems to be the same thing with DJI drones.

But even if it were possible, we would have to make sure to have an SD card with a good capacity since for this flight of 359 photos, if we consider that the DNGs are on average 48 MB it would take 17.2GB to store the photos. And the flight could even have lasted a few minutes longer.

RAW recording is a feature that has not yet been developed and may not be used if you consider that it takes between 4 to 5 seconds for the Anafi to record a DNG photo (~48 MB), so you should decrease the flight speed, decrease overlap or increase altitude and therefore decrease GSD. Not to mention that it would take a lot of extra time to download the photos from the drone as well as upload the photos to Pix4D cloud.

Update: there is actually a way (not official) to [record DNGs with Pix4D Capture](/posts/en/shooting-in-raw-dng-with-the-parrot-anafi-and-pix4d-capture/).

## Photo quality

There is a little motion blur in most of the pictures. The flight was made at about 2.7m/s but the proximity of the ground (30 meters) and the low light on that day did not help.

According to the Exif, it seems that Pix4D leaves the shutter speed and ISOs free, the focal length being fixed (f/2.4) on the Anafi. This is very good since we prefer to block the aperture for photogrammetry anyway in order to minimize lens distortion variations between each picture.

- Focal length: f/2.4
- Shutter speed: between 1/25 and 1/100
- ISO: between 103 and 206

![Photogrammetry with Parrot Anafi and Pix4D Capture photos EXIF geotagged](/media/2018-11-21---photogrammetry-with-parrot-anafi-and-pix4d-capture/Photogrammetry-with-Parrot-Anafi-and-Pix4D-Capture-photos-EXIF-geotagged-1030x604.png)

\[caption id="attachment\_1045" align="aligncenter" width="750"\]![Pix4D Parrot Anafi photogrammetry photo JPG](/media/2018-11-21---photogrammetry-with-parrot-anafi-and-pix4d-capture/P0770078-1030x774.jpg) Open the [full resolution image](/media/2018-11-21---photogrammetry-with-parrot-anafi-and-pix4d-capture/P0770078.jpg) (5344 × 4016 | 5.6 MB) in a new tab\[/caption\]

## Conclusion

The application is really very well designed and pleasant to use, without reading the instructions, without creating an account without struggling to create a mission on a small 4" screen you can easily get a correct result. In fact, I don't think I've ever planned a flight so simply. The switch from the video feedback screen to the map view is seamless and that' s good because it's something frequently required during the flight, you just have to be careful not to touch the radio control sticks. It would have been nice to be able to record the raws, the only thing to blame on Pix4D Capture. The Anafi is also very pleasant to use, it is very compact, light, we are really not afraid to take it anywhere and considering the place it takes it would be a shame not to. The possibility of charging the battery on a USB cigarette lighter socket or an external battery is also a plus. The drone is very quiet a few dozen meters from the ground.

It is for me the simplest, most intuitive and portable solution available on the market today for taking photos and photogrammetry. The drone weighing less than 800 grams also helps to avoid a lot of administrative hassle and is also more reassuring to fly, especially since it is not excessively expensive. It remains a 1/2.4" sensor that will clearly not stand up to the cameras on heavier drones, but let's say it's a solution that offers a very good volume/weight/price/image quality ratio.

## Flight Plan add-on for FreeFlight

I was hoping for this "in-app purchase" to make flight plans but even if this add-on Flight Plan from the FreeFlight application which allows you to plan flights seems rather well designed for automated videos, it will be useless for photogrammetry. You would need to create every waypoints manually, which would be a bit tedious in the case of a grid with 200 waypoints or even a circular flight plan with 30 waypoints.

## Precautions

- Plan several or a large SD card if you want to make several flights, it fills up very quickly (~2GB / flight).
- Do not press the home button on the phone (at least not on iOS). Even if you restart Pix4D quickly, the application will have lost the connection with the drone and you will have to disconnect and reconnect the USB cable that connects the phone and the radio control to restore it.

## Result

580,000 polys. Texture 8192x8192.

<iframe width="640" height="480" align="center" src="https://sketchfab.com/models/c34666babe56402495f023eb263cf583/embed" frameborder="0" allow="autoplay; fullscreen; vr" mozallowfullscreen="mozallowfullscreen" webkitallowfullscreen="webkitallowfullscreen"></iframe>
