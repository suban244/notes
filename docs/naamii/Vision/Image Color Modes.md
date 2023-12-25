Yanked from here: https://stackoverflow.com/questions/52307290/what-is-the-difference-between-images-in-p-and-l-mode-in-pil

- Normally, images are RGB, which means they have 3 channels, one for red, one for green and one for blue. That normally means that each pixel takes 3 bytes of storage, one for red, one for green and one for blue.
- If you have a `P` mode image, that means it is palettised. That means there is a palette with up to 256 different colours in it, and instead of storing 3 bytes for R, G and B for each pixel, you store 1 byte which is the index into the palette. This confers both advantages and disadvantages. The advantage is that your image requires 1/3 of the space in memory and on disk. The disadvantage is that it can only represent 256 unique colours - so you may get [banding](https://en.wikipedia.org/wiki/Colour_banding) or artefacts.
- If you have an `L` mode image, that means it is a single channel image - normally interpreted as greyscale. The `L` means that is just stores the Luminance. It is very compact, but only stores a greyscale, not colour.

View to mode using 
`image.mode`