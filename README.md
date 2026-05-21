# SDSS-V LVM Helix Nebula Tutorial
## Auroral Lines and Direct-Method Abundances

This notebook is a tutorial for me and for other folks about measuring emission lines, especially weak auroral lines, and using them to estimate the physical properties of ionized gas. To do that, we'll use the prerelease data of the Helix Nebula (NGC 7293) from the SDSS-V Local Volume Mapper (LVM). 

I'll do two things: 
1. Analyze the integrated spectrum. Here, we'll combine the science fibers into one high-S/N spectrum, measure emission lines, make an extinction correction, and derive physical properties of the gas. 
2. Fiber-by-fiber analysis. Here, we'll repeat the same measurements for each individual fiber and map the results across the nebula. 

I stress that since this is prereleased data, it has not gone through detailed sky background subtraction, stellar continuum modeling, and more careful treatment of the sky lines. 

## 0. Setup

This notebook assumes you have the LVM file locally. If you do not have the file, you can download it [here](https://www.sdss.org/dr19/lvm/tutorials/). You can also find an SDSS tutorial there as well. 

The file is a `lvmSFrame` type, with row-stacked spectra: one spectrum per fiber, with associated fiber metadata in the `SLITMAP` extension. 

Required packages: 

```bash
pip install numpy scipy pandas astropy matplotlib pyneb tqdm
```

Optional but useful: 

```bash
pip install ipympl
```

