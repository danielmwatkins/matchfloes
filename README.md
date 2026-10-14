# matchfloes: test cases for ice floe matching algorithms

Sequences of satellite images of Arctic waters often display clear motion of sea ice floes. Tracking ice floes poses different set of challenges than tracking central Arctic pack ice. Ice floes span scales from meters to 10s of kilometers, so one matching template size is not sufficient, and floes are constantly rotating, fracturing, and colliding. 

This repository includes a selection of cases from the (Ice Floe Validation Dataset)[https://github.com/danielmwatkins/ice-floe-validation-dataset]. Each case contains true color, false color, and labeled images. True color images use red, green, and blue channels to approximate what is seen by the human eye, while false color images use a mixture of other wavelengths to highlight features of interest. The MODIS False Color 7-2-1 images used here make it easier to discern differences between clouds and snow or ice. We also include a land mask for reference. The manual labels are saved as TIFF files where each connected component has a unique integer label.

The notebook "matchfloes.ipynb" extracts floe properties from the images sequences. The resulting data tables are saved in data/property_tables. 

The property tables are saved for each image and contain the following columns in alphabetical order:
1. `area` = Number of pixels in the labeled object
2. `circularity` = $4 * \pi * A / P^2$, where $A$ is the area and $P$ is the perimeter
3. `col_centroid` = $x$-coordinate of the object centroid
4. `convex_area` = Area of the minimal enclosing convex polygon
5. `label` = Integer label of object in the corresponding labeled image TIFF
6. `major_axis_length` = Length of the major axis of the best-fit ellipse
7. `max_col` = Right boundary of the bounding box
8. `max_row` = Lower boundary of the bounding box
9. `min_col` = Left boundary of the bounding box
10. `min_row` = Upper boundary of the bounding box
11. `minor_axis_length` = Length of the minor axis of the best-fit ellipse
12. `row_centroid` = $y$-coordinate of the object centroid
13. `solidity` = Ratio of the area to the convex area
14. `passtime` = Estimated time that the satellite passed the image location
15. `matched_label` = Label of object in paired image

Some important notes: note that image coordinates are the reverse of Cartesian coordinate conventions in the $y$-axis, so row 1 is the top left corner. Images are composites, and have some artifacts where images from multiple passes overlap. Labels are manually drawn, and may contain errors where images were ambiguous.

The file `setup.jl` initializes the Julia environment. Prior to running this, install Julia version 1.12 or higher. To run the notebooks, you'll need to install and instantiate the `IJulia` package.

## Questions?
Contact Daniel Watkins at `daniel_watkins@brown.edu`