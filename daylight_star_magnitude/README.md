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

It is said that during the day (assume midday) sky magnitude is around 4, which means: weakest star that can be seen in this conditions is more than 4 mag (not fainter than sky brightness). Stars brighter than 4 mag means lower value (1 mag is 2.5x brighter than 2 mag).

What is magnitude: [https://en.wikipedia.org/wiki/Magnitude_(astronomy)](https://en.wikipedia.org/wiki/Magnitude_(astronomy))

Simply: 1 mag star is 2.5x brighter than 2 mag. -1 mag star is 2.5^2^ brighter than star of 1 mag.

----

### Spica
Max magnitude: 1.05

Can be seen clearly.

[https://www.youtube.com/watch?v=FvOjC0Y2S94](https://www.youtube.com/watch?v=FvOjC0Y2S94)
[![YT vid pic](https://img.youtube.com/vi/FvOjC0Y2S94/0.jpg)](https://www.youtube.com/watch?v=FvOjC0Y2S94)

### Alphecca
Max magnitude: 2.2

Hands down can be seen.

[https://www.youtube.com/watch?v=f45soKC15Fk](https://www.youtube.com/watch?v=f45soKC15Fk)
[![YT vid pic](https://img.youtube.com/vi/f45soKC15Fk/0.jpg)](https://www.youtube.com/watch?v=f45soKC15Fk)

### Kornephoros
Max magnitude: 2.7

Also can be seen clearly.

[https://www.youtube.com/watch?v=WVGfy0PbjGg](https://www.youtube.com/watch?v=WVGfy0PbjGg)
[![YT vid pic](https://img.youtube.com/vi/WVGfy0PbjGg/0.jpg)](https://www.youtube.com/watch?v=WVGfy0PbjGg)

### Kappa Ophiuchi
Max magnitude: 3.19

Can be seen but it's hard to differentiate from noise.

[https://www.youtube.com/watch?v=vwwhWxhhzVk](https://www.youtube.com/watch?v=vwwhWxhhzVk)
[![YT vid pic](https://img.youtube.com/vi/vwwhWxhhzVk/0.jpg)](https://www.youtube.com/watch?v=vwwhWxhhzVk)

----

### Conclusion

ASI120MC-S is very noisy camera (read noise in gain 0 around 7.0e) and dynamically rather poor (FW=13000). I've use generic UV/IR block filter. Both of this conditions results with rather worse ability to see stars around theoretical 4mag limit.

