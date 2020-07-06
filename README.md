# Modelling the wave overtopping flow over the crest and the landward slope of grass-covered flood defences.

We have developed a numerical model in the open source software OpenFOAM to simulate the overtoppign flow over grass-covered flood defences.
Our paper on the validation of the model is freely available at https://doi.org/10.3390/jmse8070489.

Van Bergeijk, V.M.; Warmink, J.J.; Hulscher, S.J.M.H. Modelling the Wave Overtopping Flow over the Crest and the Landward Slope of Grass-Covered Flood Defences. J. Mar. Sci. Eng. 2020, 8, 489.

Please reference to it probably when using this model.

This examples computes the flow for the Millingen a/d Rijn case for an overtopping volume of 2000 l/m.
The model is run using the Allrun script, which generates the mesh, solves the flow and computes the post process functions.

## Generation of the mesh
- The background mesh is generated using blockMesh with a horizontal grid size of 5 cm and a vertical grid size of 3 cm for the first block and 6 cm for the second block.
- The dike profile is located in the file constant/triSurface/stlDefinitions. This file is changed to a .stl file using the function faceSetToSTL from the [waves2Foam](https://github.com/ogoe/waves2Foam) toolbox and a .emesh file using the surfaceFeatureExtract function.
- The dike profile is cut out of the background mesh using snappyHexMesh.

## Post processing
- The shear stress on the dike profile is computed using the wallShearStress function in OpenFOAM that calculates the shear stress in cartesian coordinates.
- The water fraction and flow velocity are sampled at the measurement locations M2-M8.
- The pressure on the dike cover is sampled using the samplePressureSurface file.
