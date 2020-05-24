---
title: "Shooting in RAW (DNG) with the Parrot Anafi and Pix4D Capture"
date: "2018-11-23T17:16:07.000Z"
template: "post"
draft: false
slug: "shooting-in-raw-dng-with-the-parrot-anafi-and-pix4d-capture"
category: "uav"
tags: 
  - "English"
  - "pll_5bf835d793813"
  - "uav"
description: "The Pix4D Capture application only records JPGs. Fortunately it is possible to bypass this limitation and record the pictures in DNG (RAW)"
---

> A word of caution ! 
> It is possible that switching applications and disconnecting the USB cable during flight may disrupt the proper operation of the drone. I didn't have a problem but use this method at your own risk. - These tests were performed with a Parrot Anafi 1.2.4, SkyController 1.2.0, an iPhone 5S on iOS 12, the FreeFlight 6.2.1 application. YMMV.

![Pix4D Parrot Anafi record RAW DNG FreeFlight reconnected](/media/2018-11-23---shooting-in-raw-dng-with-the-parrot-anafi-and-pix4d-capture/Pix4D-Parrot-Anafi-record-RAW-DNG-FreeFlight-reconnected-300x169.jpg)

The Pix4D Capture application is very well designed to prepare flight plans, whether grid, double grid, polygon or circular. Preparing a flight plan is very simple, even on a small smartphone and all the important settings such as camera coverage or tilt are present. The only downside when doing [photogrammetry with Parrot Anafi and Pix4D Capture](/posts/en/photogrammetry-with-parrot-anafi-and-pix4d-capture/), the app only records JPGs and this is also the case with other drones such as DJI's.

Fortunately, it is possible to overcome this limitation with the following steps:

1. Turn on Anafi and connect your smartphone to the SkyController3
2. Open Pix4D Capture and create a flight plan ![Pix4D Parrot Anafi record RAW DNG photos with Pix4D Capture](/media/2018-11-23---shooting-in-raw-dng-with-the-parrot-anafi-and-pix4d-capture/Pix4D-Parrot-Anafi-record-RAW-DNG-photos-with-Pix4D-Capture-1030x580.jpg)
3. Click on the "Start" button at the bottom right in Pix4D Capture. Skip the screen that asks you to connect to the drone. The checklist is shown, this is the moment when the app writes the flight plan on the Anafi. **Click on Cancel**.
  

![Pix4D Parrot Anafi record RAW DNG photos drone takeoff checklist](/media/2018-11-23---shooting-in-raw-dng-with-the-parrot-anafi-and-pix4d-capture/Pix4D-Parrot-Anafi-record-RAW-DNG-photos-drone-takeoff-checklist-1030x580.png)
<figcaption>Once "Mission uploaded to drone" is in green, press "Cancel</figcaption>

4. Launch the FreeFlight application and go to the "Fly" screen. ![Pix4D Parrot Anafi record RAW DNG FreeFlight Pix4D switch](/media/2018-11-23---shooting-in-raw-dng-with-the-parrot-anafi-and-pix4d-capture/Pix4D-Parrot-Anafi-record-RAW-DNG-FreeFlight-Pix4D-switch-e1542816095332-1030x580.jpg)
  

![Pix4D Parrot Anafi record RAW DNG FreeFlight not connected](/media/2018-11-23---shooting-in-raw-dng-with-the-parrot-anafi-and-pix4d-capture/Pix4D-Parrot-Anafi-record-RAW-DNG-FreeFlight-not-connected-1030x580.jpg)
<figcaption>FreeFlight will display this screen until the cable is reconnected</figcaption>

5. Reconnect the smartphone to the SkyController3 with the USB cable.
6. Modify the photo settings: DNG/JPG, Style, iso, shutter speed. You can choose all the parameters at your convenience, they will then be used during the automatic flight. ![Pix4D Parrot Anafi record RAW DNG choose photo settings](/media/2018-11-23---shooting-in-raw-dng-with-the-parrot-anafi-and-pix4d-capture/Pix4D-Parrot-Anafi-record-RAW-DNG-choose-photo-settings-1030x580.jpg)

7. Disconnect the USB cable that connects the smartphone to the SkyController3.
8. Switch back to the Pix4D Capture application
9. Reconnect the USB cable
10. Wait for pix4D to reconnect to the Anafi and then press "Start" again at the bottom right of the screen. And this time, on the "Drone take off checklist" screen, we will not click on Cancel but on Start. The Anafi takes off immediately and begin its automated flight. 

![Pix4D Parrot Anafi record RAW DNG photos drone takeoff checklist](/media/2018-11-23---shooting-in-raw-dng-with-the-parrot-anafi-and-pix4d-capture/Pix4D-Parrot-Anafi-record-RAW-DNG-photos-drone-takeoff-checklist-1030x580.png)

That's it! The Anafi will take all the following pictures in DNG+JPG with the settings you have chosen in FreeFlight.

![Pix4D Parrot Anafi record RAW DNG exif ISO 3200 shutter speed 1-4000](/media/2018-11-23---shooting-in-raw-dng-with-the-parrot-anafi-and-pix4d-capture/Pix4D-Parrot-Anafi-record-RAW-DNG-exif-ISO-3200-shutter-speed-1-4000.jpg)
<figcaption>We do have an exposure time of 1/400 and ISO at 3200 as previously defined in FreeFlight</figcaption>

![Pix4D Parrot Anafi record RAW DNG gallery](/media/2018-11-23---shooting-in-raw-dng-with-the-parrot-anafi-and-pix4d-capture/Pix4D-Parrot-Anafi-record-RAW-DNG-gallery-1030x580.jpg)
<figcaption>DNG photos in FreeFlight's SD card explorer</figcaption>

After the flight, it will not be possible to continue with the Pix4D workflow, the application will not be able to download the photos from the Anafi after the mission, which is quite normal since it was not designed to do so.

![Pix4D Parrot Anafi record RAW DNG photos arror when uploading images](/media/2018-11-23---shooting-in-raw-dng-with-the-parrot-anafi-and-pix4d-capture/Pix4D-Parrot-Anafi-record-RAW-DNG-photos-arror-when-uploading-images-1030x580.png)
<figcaption>Pix4D Capture will not be able to recover the photos if we force the Anafi in DNG, the application is not designed for that</figcaption>

But it will of course still be possible to retrieve the geotagged DNGs from the Anafi SD card, convert them to TIFF and then use them in Pix4D or any other photogrammetry software.

Unfortunately, the Anafi is not able to record DNGs as fast as JPGs, it will need between 4 and 5 seconds between each picture. It will therefore be necessary to modify some settings:

- Reduce flight speed (and therefore increase flight time and probably reduce the area covered)
- Reduce overlap (which is not recommended, the default settings of Pix4D 80% ↕ and 70%↔ are suitable for most projects, decreasing them could complicate or make it impossible for the photogrammetry software to do its job )
- Increase altitude (and therefore decrease GSD and slightly increase flight time)

Or a mix of the 3 that can be defined according to a careful calculation. We therefore lose some of the advantages of the Pix4D application, which in normal operation would completely abstract this type of problem.

![Pix4D Parrot Anafi record RAW DNG HoudaGeo Pix4D Capture](/media/2018-11-23---shooting-in-raw-dng-with-the-parrot-anafi-and-pix4d-capture/Pix4D-Parrot-Anafi-record-RAW-DNG-HoudaGeo-Pix4D-Capture.jpg)
<figcaption>24 photos were taken instead of the 44 initially planned because of the recording time of the DNG (4 to 5 seconds)</figcaption>

![Pix4D Parrot Anafi record RAW DNG HoudaGeo Exif timestamp](/media/2018-11-23---shooting-in-raw-dng-with-the-parrot-anafi-and-pix4d-capture/Pix4D-Parrot-Anafi-record-RAW-DNG-HoudaGeo-Exif-timestamp-1030x680.jpg)
<figcaption>Examining the exif, we can see that it takes between 4 and 5 seconds for the Anafi to save the pictures in DNG</figcaption>
