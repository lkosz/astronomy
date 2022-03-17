## Project: Determine star magnitude which can be seen during midday

- Timestamp: 05.09.2021 ~13:30
- Camera: ASI120MC-S
- Telescope: Achromatic refractor, aperture 90mm, focal 500mm
- Mount: SkyWatcher EQ5 with DIY GOTO [https://github.com/lkosz/eq5_diy_drive](https://github.com/lkosz/eq5_diy_drive)
- Postprocessing:
  - equalized histogram using `cv2.equalizeHist`
  - color inversion
  - combined into animation using `ffmpeg`

----

### Problem definition

It is said that during the day (assume midday) sky brightness is around 4<sup>m</sup> (assume +/- sea level), which means: weakest star that can be seen in this conditions is more than 4<sup>m</sup> (not fainter than sky brightness).

What is magnitude: [https://en.wikipedia.org/wiki/Magnitude_(astronomy)](https://en.wikipedia.org/wiki/Magnitude_(astronomy))

Simply: 1<sup>m</sup> star, which means star of magnitude=1, is 2.5x brighter than 2<sup>m</sup> star. -1<sup>m</sup> star is 2.5<sup>2</sup> brighter (sic!) than star of 1<sup>m</sup>.

----
### Observations

#### Spica
Max 1.05<sup>m</sup>

Can be seen clearly.

[https://www.youtube.com/watch?v=FvOjC0Y2S94](https://www.youtube.com/watch?v=FvOjC0Y2S94)

[![YT vid pic](https://img.youtube.com/vi/FvOjC0Y2S94/0.jpg)](https://www.youtube.com/watch?v=FvOjC0Y2S94)

#### Alphecca
Max 2.2<sup>m</sup>

Hands down can be seen.

[https://www.youtube.com/watch?v=f45soKC15Fk](https://www.youtube.com/watch?v=f45soKC15Fk)

[![YT vid pic](https://img.youtube.com/vi/f45soKC15Fk/0.jpg)](https://www.youtube.com/watch?v=f45soKC15Fk)

#### Kornephoros
Max 2.7<sup>m</sup>

Also can be seen clearly.

[https://www.youtube.com/watch?v=WVGfy0PbjGg](https://www.youtube.com/watch?v=WVGfy0PbjGg)

[![YT vid pic](https://img.youtube.com/vi/WVGfy0PbjGg/0.jpg)](https://www.youtube.com/watch?v=WVGfy0PbjGg)

#### Kappa Ophiuchi
Max 3.19<sup>m</sup>

Can be seen but it's hard to differentiate from noise.

[https://www.youtube.com/watch?v=vwwhWxhhzVk](https://www.youtube.com/watch?v=vwwhWxhhzVk)

[![YT vid pic](https://img.youtube.com/vi/vwwhWxhhzVk/0.jpg)](https://www.youtube.com/watch?v=vwwhWxhhzVk)

----

### Conclusion

ASI120MC-S is very noisy camera (read noise at gain 0 is around 7.0e), dynamically rather poor (FW=13000) and ADC have 12bit resolution, which not help. I've used generic UV/IR block filter. This conditions results with rather worse ability to see stars around theoretical 4<sup>m</sup> limit. Anyway **I was able to manually detect 3.19<sup>m</sup> star on picture which means that theoretical limit is correct**. With better camera (less noisy with better dynamics) at least 3.5<sup>m</sup> stars should be seen. With camera sensitive in IR band, without UV/IR filter, result should be even better (but have to remember that with IR band theoretical limit is different and star brightness in IR can be different than in visual band).

Anyway it is not so easy to find even -1<sup>m</sup> star in daylight thus I've used DIY GOTO for EQ5 mount which have accuracy up to 5-7 arcsec. I've calibrated mount on building corner at first (I know alt/az coords of it), then on Venus which is very bright and easy to find even in daylight, centered in frame, then I've tried to find stars. As you can see - frame in my camera is not equally bright, so I had to move star manually closer to left down corner (which even can be seen at first frames of Kornephoros), and it wasn't hard with first 3 stars. With last - Kappa Ophiuchi it was much harder and I was loosing her in the noise, thus I decided to leave her in that corner. 

Small appendix: what I mean by "can be seen" is: "can be differentiated from noise". What we see in pictures is few levels of pixel brightness stretched to full, to can be seen by human eye. I didn't make truly visual observations (using diagonal and eyepiece connected to scope), I've done it only via camera, which obviously differs from visual perception. Spica can be seen in uninverted and unstretched live view on computer monitor (on steady picture harder), but other stars brightnesses were too close to natural sky brightness to see it, thus I had to use histogram stretching and color inversion to catch it.

That's how it looks on raw, unprocesser 16-bit png raw frames:

Spica
![raw spica](raw_spica.png)

Kornephoros
![raw kornephoros](raw_kornephoros.png)

