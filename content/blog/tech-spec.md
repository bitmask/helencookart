
---
title: "Tech spec"
date: 2022-07-17T14:26:52Z
draft: true
image: blog/new-beginnings.jpg
---


##### Technical spec

Now let's get into the weeds of what this should look like.  

Happy path: upload an image and see the colour distribution in the browser.


Display upload form

On upload:

- Process image
- Plot points

Process image:

- Input: image file
- Extract a sample of pixels from the image
- Get the colour of each pixel
- Map the colour onto the nearest point that is defined in the Munsell space
- Lookup the xyz coords for that point 
- Return: xyz coords

Plot points:

- Input: list of xyz coords
- Plot 3D
- Plot Hue vs Value
- Plot Hue vs Chroma
- Plot Value vs Chroma

Any plot function:
- Input: list of xyz coords
- Plot a point of that colour at xyz, if a point is already there, increase the size of it
 
3D image functions:

- On click and drag, rotate the image in 3D

2D image functions:

- Change the range of the slice (third variable not in plot) to display
- This generates a new set of xyz coords to plot which is passed to the previous plot function
- Hopefully this reduces the problem of overplotting 



##### Future Extensions

Run the above over a collection of work by an artist and compare colour use between paintings.  

I would like to be able to plot the colours you can make from a tube of watercolour.  Add another to make a mixing pair, and plot the colours between the two tube colours that can be generated.  Then add a third paint and plot all the points in the space that can be made by mixing together three paints (the gamut of the triad).

From any starting point, and a given step size generate a helix through the space to generate a palette.Plot the path of this palette in the 3D space and show the steps/colours generated with their hex values etc so they can be exported.



This could later be expanded to plot the location of a pigment in the space, then add another pigment to see the path that blending the two will take through the space. Then, add a third to see the whole gamut that could be mixed by these three paints.  

Or, this space could be used to generate palettes that are more interesting than your standard split complementary harmony, which again disregards value.  It would be very interesting to me to analyse the works of an artist and see how their use of colour was consistent or not across their works, and if the patterns of colour use were consistent or not.  That can all come later, first we just need the bare minimum.

Maybe in the far future, we could look at extracting different types of information from the paintings such as the sizes of continuous colour regions (some painters use large areas of flat colour, the impressionists do not), and the lengths of the boundaries between regions, proportions of colours.  Would need to know exactly what to do with this information, but this could be a way to find similar painters.

