# Micropillar-dislocation-estimation
An automated method for estimating micropillar dislocation induced by _C. Elegans_ worms using bright-field videos &amp; image processing

## To install Python dependencies
    pip install -r dependencies.txt

## How to run  
    python pillar_dislocation.py

## **Dataset** 
Bright-field microscopy videos of _C. Elegans_ worms traversing through a microfluidic chamber, consisting of a micropillar array. The pillars are not rigid but deformable since the devices are made from PDMS.  

## **Objectives**
[1] Detect micropillars contacted by worms along with “duration” of contact.  
[2] Generate dislocation profiles along all frames of interest for all detected pillars.

## **Methodology**
The algorithm can be broken down into the following steps -   
[1] Read video into 3D image stack.  
[2] Detect circular pillars using first frame only to speed up computation.  
[3] Next, on the 5x spatial down-sampled frame, first a binary pillar stack is created with 1's corresponding to all center locations. This is followed by segmentation, cleaning and dilation to obtain the dilated worm mask.  
[4] Worm-contacted pillar stack is generated from the dilated worm mask and the binary pillar stack.  
[5] Pillars which the worm contacted for <5 frames are eliminated and pillar coordinates as well as frame ids are stored in a ".csv" file.  
[6] For each pillar image, center coordinated of fit circle are obtained at each frame of interest. By constructing a vector from the initial center to frame center, dislocation magnitude & direction can be computed.  
[7] Dislocation magnitude + direction are generated for all detected frame ids.

## **Results**  
Animation below shows the dislocation profile (magnitude + direction) for one of the pillars contacted by the worm. The two red, vertical lines indicate the first and last frames the particular pillar was contacted by the worm. In general, it is not necessary that the worm contacts the pillar for all frames between the first and last. 

![Pillar_44](https://github.com/Anivader/Micropillar-dislocation-estimation/assets/33497062/8bb9f1c6-d3ce-4e02-9c34-299f20a22141)


