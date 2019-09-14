## Bundle Adjustment for 3D Reconstruction from Multi-Date Satellite Images

Roger Mari, Carlo de Franchis, Enric Meinhardt-Llopis, Gabriele Facciolo


#### Abstract

The generation of up-to-date accurate 3D models from multiple satellite images has recently become a hot topic of research.
A well-known challenge of this problem is to set all cameras in a common frame of reference, since depending on the satellite
geopositioning equipment these may contain errors up to tens of meters on the ground. In this context, bundle block adjustment
strategies, relying on the identification of a set of tie-points and the correction of the camera models to make them coincident, have become a generally accepted practice. However, new approaches capable of producing state-of-the-art results without the use of bundle adjustment priors have been proposed. This work aims to assess the practical impact of using bundle adjustment for a multi-view stereo pipeline for 3D reconstruction from multi-date satellite images.


#### Instructions

- Run `pipelineA.ipynb` to test *Multi-view Stereo without Bundle Adjustment* (correlation based model alignment)

- Run `pipelineB.ipynb` to test *Multi-view Stereo with Bundle Adjustment* (adjustment of camera rotations)

- Run `pipelineC.ipynb` to test *Multi-view Stereo with Bundle Block Adjustment* (adjustment of correction offsets)

Each pipeline is explained in the corresponding section of the report (see part *II-Methodology*).

Set the output directory and the cirterion of selection for the input stereo pairs before running each notebook (2nd cell).

The geotiff file `gt_dsm.tif` contains the lidar ground truth Digital Surface Model (DSM).

The text file `raw_sift_tracks.txt` contains the pre-computed feature tracks found across the set of input images.

Directory `pairs` contains the lists of input stereo pairs given by the ORACLE or SIFT selection criteria.

Directory `exp` contains the output of the experiments. In each subdirectory you can find:

- `dsm` contains the raw DSMs obtained from each stereo pair
   
- `cdsm` contains the DSMs after post-processing 1 (closing)
    
- `mcdsm` contains the DSMs after post-processing 2 (minimum interpolation) - only used in pipeline A

- `ncc_transform` contains the transformations used for DSMs alignment - only used in pipeline A

- `rcdsm` contains the co-registered DSMs - only used in pipeline A

- `output/fused_dsm.tif` is the reconstructed DSM after the fusion step

- `output/t_sol.txt` is the transformation used to register the reconstructed DSM to the GT frame of reference

- `output/sol_dsm_registed.tif` is the reconstructed and registered output DSM
    

#### Experiments

Experiments `exp/pipelineA_oracle`, `exp/pipelineB_oracle` and `exp/pipelineC_oracle` correspond to runs (1), (6) and (7) from Table I of the report. Experiments `exp/pipelineA_sift`, `exp/pipelineB_sift` and `exp/pipelineC_sift` correspond to runs (1), (2) and (3) from Table II of the report.
