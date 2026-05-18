BEFORE / AFTER PHOTOS — My Salon Suite Blaine
==============================================

Download the before/after photos from the client's Google Drive folder:
https://drive.google.com/drive/folders/1MwamZ_mAxqmdPjP0wJMcOqZLNbVLbdz7

Then place your images in this folder and update the two src attributes in
index-v2.html (search for "slot=first" and "slot=second" inside the
before-after-section).

Example:
  <img slot="first"  src="before-after/your-before-photo.jpg" alt="Before">
  <img slot="second" src="before-after/your-after-photo.jpg"  alt="After">

Multiple sliders: To show more than one before/after pair, duplicate the
<img-comparison-slider> block inside the .before-after-wrap div and point
each pair at different images.

Recommended image size: 900 x 480 px minimum, same dimensions for both
before and after in each pair so the slider aligns cleanly.
