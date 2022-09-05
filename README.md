# GPU_registration
this function perform drift correction of hyperstacks

 
# Parameters:
source   path of the directory containing all the stacks you want to process (will all be processed in batch)

destination path of the directory to save all the registered stacks

Precision=1 or 2;  % 1 means single precision for variables on the GPU, 2 means double precision. [double is useless here]

Cropmode=0 or 1;   % 1 means you don't want to use the full image for registration

boxsize=512;       % if Cropmode=1, select the size of the centered ROI to do the registration on

fourrier=0 or 1;   % 1 means cross correlation will be done in the fourrier space

gaussianfit=0 or 1; %1 means Gaussianfit of spot (for subpixel alignement). 

interpolate=0 or 1; % 0 means no rounding of offset before wraping

itter=0 or 1 ;      %1 means itterative mode: the frame n+1 is registered relatively to the frame n and not the first frame. 0 means registration from first frame

channel=1-nC;       % specify the channel to use for registration when stack is a hyperstack
 
# outputs
flag tells you if you ended up writing big tiff files and this should reopen the files with Fiji to increase read/write speed (the tiff library writes fine but files are slow to read);

# syntax
batchGPUalignfunc(source,destination,1,0,512,1,1,1,0,1); for non itterative

batchGPUalignfunc(source,destination,1,0,512,1,1,1,1,1); for itterative

Copyright (C) 2022, Derivery Lab - MRC LMB 
