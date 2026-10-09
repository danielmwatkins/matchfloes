# matchfloes: test cases for ice floe matching algorithms

Sequences of satellite images of Arctic waters often display clear motion of sea ice floes. Tracking ice floes poses different set of challenges than tracking central Arctic pack ice. Ice floes span scales from meters to 10s of kilometers, so one matching template size is not sufficient, and floes are constantly rotating, fracturing, and colliding. 

This repository includes two cases, one from Baffin Bay and one from Fram Strait, each with a mixture of ice floes which are visible in both images and some which are visible only in one.

The notebook "matchfloes.ipynb" extracts estimated floe shapes and properties from the image sequences. The resulting labeled images are saved in data/labels, the source color images in data/iamges, and the feature property tables in data/features.