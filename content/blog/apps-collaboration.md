---
title: "Call for collaboration"
date: 2022-06-26T21:06:33+01:00
draft: false
image: apps/munsell.png
---

I'm looking for a web developer to collaborate with me on a client side browser based app that will take an uploaded image and then display the colours in the image in the 3D Munsell colour space.  

{{< asset src="apps/munsell.png" >}}

*Why?*

Getting to know the [Munsell colour space](https://en.wikipedia.org/wiki/Munsell_color_system) has helped me immensely with my understanding of colour.  The space is three dimensional (like any colour space) and is shaped approximately like a cylinder with the long axis representing value (how dark or light a colour is), the radial axis representing hue, and the distance from the central axis representing chroma (how saturated a colour is).  Black to white run up the central axis, and the brightest colours sit around the outside of the cylinder.  

This is a colour space based on perception, so the distance between 3 and 4 on the value scale looks the same as the distance between 6 and 7, and so forth for the other axes.  This consistency is very useful for painting where we never need to know the exact wavelength of the light, but whether a red is halfway between the bright highlight and the dark shadow is very important.

I think about moving around in this space when I'm mixing, and I'm now I'm more able to place the colour I've mixed in the space and to compare it to my target colour.  With the three dimensions clearly defined, it is easier to see if one colour is more saturated or more grey than the other, or lighter or darker in value, or warmer or cooler in hue.  I would like to be able to analyze the colours in a painting the same way by plotting them all in the Munsell colour space. 

To do this, I envision uploading an image and then getting a plot back that displays all the colours used in the Munsell colour space.  This way I could quickly see what the lightest colours in value in the image are, what the most saturated colours are.  What sort of colour bias there is in the image, what limited palette has been used, and so forth.  

This sort of information is usually displayed on the colour wheel, hue around the outside, and chroma decreasing towards the middle.  This depiction is fine, but it's only part of the picture because it leaves out value entirely.  A light red and a dark red would appear in the same place on the colour wheel, but are very different colours.  I think such a visualisation would be useful to more people than just myself, so I would like to have it on this site and make it available for folks to use.  

*How?*

To make such a tool available and to reduce the barrier to using it, it should be a browser based client side application.  Upload an image of an artwork, and the app will extract the colours in the image and display them in the 3D Munsell cylinder.  You'd be able to click and drag to rotate the 3D space to see all sides of it (and ideally, would also provide projections along two of the axes, hue, value, or chroma, to better see the space).

The catch is that although I used to do programming as a career, that was decades ago and I never really learned javascript.  And I'm so disconnected from tech these days that I don't even know if javascript is the right language to use anymore.  

So I'm putting out this call.  Would you like to work on this with me?  I'd like to structure the project such that you write the general framework, and then I'll implement an extension to it which will be a good way for me to learn the code.  

I think this tool would be useful to anyone trying to understand colour, anyone interested in art, anyone interested in making a fun little colourful online tool.  


*Technical spec*

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



Future Extensions

Run the above over a collection of work by an artist and compare colour use between paintings.  

I would like to be able to plot the colours you can make from a tube of watercolour.  Add another to make a mixing pair, and plot the colours between the two tube colours that can be generated.  Then add a third paint and plot all the points in the space that can be made by mixing together three paints (the gamut of the triad).

From any starting point, and a given step size generate a helix through the space to generate a palette.Plot the path of this palette in the 3D space and show the steps/colours generated with their hex values etc so they can be exported.



This could later be expanded to plot the location of a pigment in the space, then add another pigment to see the path that blending the two will take through the space. Then, add a third to see the whole gamut that could be mixed by these three paints.  

Or, this space could be used to generate palettes that are more interesting than your standard split complementary harmony, which again disregards value.  It would be very interesting to me to analyse the works of an artist and see how their use of colour was consistent or not across their works, and if the patterns of colour use were consistent or not.  That can all come later, first we just need the bare minimum.

Maybe in the far future, we could look at extracting different types of information from the paintings such as the sizes of continuous colour regions (some painters use large areas of flat colour, the impressionists do not), and the lengths of the boundaries between regions, proportions of colours.  Would need to know exactly what to do with this information, but this could be a way to find similar painters.

