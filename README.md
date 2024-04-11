# cosmic_pca
Performing PCA on data from The Sloan Digital Sky Survey

# Data Information
CONTEXT - The Sloan Digital Sky Survey or SDSS is a major multi-spectral imaging and spectroscopic redshift survey using a dedicated 2.5-m wide-angle optical telescope at Apache Point Observatory in New Mexico, United States. SDSS has gathered image and spectroscopic data of millions of celestial objects spanning the entire night sky. Each object is classified in one of the eight categories by help of their optical and spectroscopic properties.

My partner Gayla Hess and I performed principal component analysis on a subset of data originally from a data set which included 4,000,00 observations across 52 variables.
The variable explanations are as followed:

objID: Unique SDSS identifier composed from [skyVersion,rerun,run,camcol,field,obj]. 
run: Run number <br />
camcol: Camera column 
field: Field number
type: Type classification of the object (star, galaxy, cosmic ray, etc.)
rowv: Row-component of object's velocity (deg/day)
colv: Column-component of object's velocity (deg/day)
psfMag_u: PSF magnitude (mag)
psfMag_g: PSF magnitude (mag)
psfMag_r: PSF magnitude (mag)
psfMag_i: PSF magnitude (mag)
psfMag_z: PSF magnitude (mag)
petroRad_u: Petrosian radius (arcsec)
petroRad_g: Petrosian radius (arcsec)
petroRad_r: Petrosian radius (arcsec)
petroRad_i: Petrosian radius (arcsec)
petroRad_z: Petrosian radius (arcsec)
q_u: Stokes Q parameter 
q_g: Stokes Q parameter
q_r: Stokes Q parameter
q_i: Stokes Q parameter
q_z: Stokes Q parameter
u_u: Stokes U parameter
u_g: Stokes U parameter
u_r: Stokes U parameter
u_i: Stokes U parameter
u_z: Stokes U parameter
expRad_u: Exponential fit scale radius, here defined to be the same as the half-light radius, also called the effective radius (arcsec)
expRad_g: Exponential fit scale radius, here defined to be the same as the half-light radius, also called the effective radius (arcsec)
expRad_r: Exponential fit scale radius, here defined to be the same as the half-light radius, also called the effective radius (arcsec)
expRad_i: Exponential fit scale radius, here defined to be the same as the half-light radius, also called the effective radius (arcsec)
expRad_z: Exponential fit scale radius, here defined to be the same as the half-light radius, also called the effective radius (arcsec)
expAB_u: Exponential fit b/a
expAB_g: Exponential fit b/a
expAB_r: Exponential fit b/a
expAB_i: Exponential fit b/a
expAB_z: Exponential fit b/a
modelFlux_u: better of DeV/Exp flux fit (nanomaggies)
modelFlux_g: better of DeV/Exp flux fit (nanomaggies)
modelFlux_r: better of DeV/Exp flux fit (nanomaggies)
modelFlux_i: better of DeV/Exp flux fit (nanomaggies)
modelFlux_z: better of DeV/Exp flux fit (nanomaggies)
ra: J2000 Right Ascension (r-band) (deg)
dec: J2000 Declination (r-band) (deg)
b: Galactic latitude (deg)
l: Galactic longitude (deg)
u: Shorthand alias for modelMag (mag)
g: Shorthand alias for modelMag (mag)
r: Shorthand alias for modelMag (mag)
i: Shorthand alias for modelMag (mag)
z: Shorthand alias for modelMag (mag)

During the data cleaning process, the variables objID, run, camcol, field, and type were all dropped and they were not relevant for our analysis. Loading the data and working with this large of a data frame results in long processing time in R. For this demonstration, the training set was randomly sampled to collect 10,000 observations. The sample file is included with this demo.

Our primary goal was to allow individuals to walk through our PCA demo and gain a better understanding of its processes and functions. The demo can either be viewed and worked through in the .rmd file or simply viewed in the Word document. Our secondary goal was to assess which variables have the largest loadings in the principal components that explain the most variance. 

# Summary

The first principal component accounts for 23.1% of the explained variability in the data while the second principal component accounts for 8.7%. Looking at the biplot and the loading values in PC1 we see that expAB, psfMag, and modelMag (u, g, r, i, z) have the largest contributions to the first principal component, while PC2 is represented primarily by modelFlux measures.  

The same measurements with different filters tend to load together across PC1 and PC2. This indicates that these PCs are associated with different measurement types opposed to the different filters. Furthermore, variables of similar measurement type cluster together in the initial PCs. For example, the variables u, g, r, i, z and psfMag_u, psfMag_g, psfMag_r, psfMag_i and psfMag_z cluster together as they are all magnitude measures of brightness in the celestial object.
