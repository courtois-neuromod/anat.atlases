
Parcellations
==============

**Atlases and ROI masks in MNI and subject (T1w) space for the Courtois-NeuroMod project.**

This dataset includes standard and custom parcellations derived from functional data for each of the six CNeuroMod participants. The set of available parcellations is described below.

-------------------------

### 1. Standard parcellations

**MIST and BASC atlases**

* MIST and BASC parcellations are found under ``./tpl-MNI152NLin2009bSym``
* BASC parcellations are also under ``./tpl-MNI152NLin2009bAsym``

**Other standard atlases in MNI152NLin2009cAsym space**

* The Schaefer and DiFuMo parcellations are saved under ``./tpl-MNI152NLin2009cAsym``<br><br>

---------------------------------
### 2. Subject-specific custom parcellations

Individual ROI masks and parcellations in native subject space are saved under ``./tpl-sub0*T1w`` for each subject. The scripts used to produce most custom masks and atlases can be found [here](https://github.com/courtois-neuromod/cneuromod_extract_tseries/tree/main/timeseries/masks). Available files include:<br><br>

**2.1 Individual grey matter masks**

* Subject-specific masks that include cortical and subcortical grey matter were created from Freesurfer segmentation (aseg.mgz) in T1w space. E.g. ``./tpl-sub0*T1w/tpl-sub*T1w_res-func_label-GM_desc-fromFS_dseg.nii.gz``
* Individual grey matter masks warped to MNI space are also available as ``./tpl-MNI152NLin2009cAsym/tpl-MNI152NLin2009cAsym_sub-*_res-func_label-GM_desc-fromFS_dseg.nii.gz``
* Individual 10k-parcel parcellations performed with the Ward algorithm within individual grey matter masks in subject (T1w) or MNI space also provide features that cover the entire brain at a resolution lower than EPI voxels. Each of the 10k parcels is nested within the Schaefer18_1000Parcels7Networks parcel with which is shares the most voxels, for a nested hierarchical parcellation. Note that, in T1w space, the Schaefer parcellation was warped to subject space to support this hierarchical assignment. Also, some unassigned parcels fall within the cerebellum or subcortical grey matter structures, regions not covered by the Schaefer parcellation. E.g., ``./tpl-MNI152NLin2009cAsym/tpl-MNI152NLin2009cAsym_sub-*_res-func_atlas-Ward_desc-10k_dseg.nii.gz``, ``./tpl-sub*T1w/tpl-sub*T1w_res-func_atlas-Ward_desc-10k_dseg.nii.gz``. The nested assignment to larger Shaefer18-1000Parcels7Networks is specified in ``./tpl-MNI152NLin2009cAsym/tpl-MNI152NLin2009cAsym_sub-*_atlas-Ward_desc-10k_dseg.tsv`` and ``./tpl-sub*T1w/tpl-sub*T1w_atlas-Ward_desc-10k_dseg.tsv``.<br><br>


**2.2 Language ROI masks (n=8)**

For each subject, language ROIS (from Mariya Toneva and Leila Wehbe) were warped from standard MNI space to
individual space. These ROIs are based on the work of Fedorenko et al. 2010
and Binder et al., 2009, as explained [here](https://www.biorxiv.org/content/10.1101/2020.09.28.316935v4)

ROIs include:

* Angular gyri (AngularG)
* Anterior and posterior temporal cortex (AntTemp, PostTemp)
* Dorsomedial prefrontal cortex (dmpfc)
* Inferior frontal gyri (IFG and IFGorb)
* Middle frontal gyri (MFG)
* Posterior cingulate cortex (pCingulate)

E.g., ``./tpl-sub0*T1w/tpl-sub*T1w_res-func_atlas-langToneva_label-AntTemp_mask.nii.gz``

ROI masks are also available in MNI space in a format compatible with all 6 subjects.
E.g., ``./tpl-MNI152NLin2009cAsym/tpl-MNI152NLin2009cAsym_res-func_atlas-langToneva_label-AntTemp_mask.nii.gz``<br><br>


**2.3 Yeo networks (n=6) derived from seed functional connectivity**

Networks are based on [Yeo et al., 2011](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3174820/)
For each subject, each network was derived by averaging the signal within a
seed parcel (MIST-ROI atlas), and by correlating its activation with the
rest of the brain using resting state runs from the CNeuroMod hcptrt dataset. Network masks are available in
MNI and native (T1w) space for all subjects.

Networks include:

* Default Mode network
* Dorsal Attention network
* Front-parietal network
* Sensorimotor network
* Ventral attention network
* Visual network

E.g., ``./tpl-sub0*T1w/tpl-sub*T1w_res-func_atlas-yeo7networks_label-defaultMode_mask.nii.gz``,
``./tpl-MNI152NLin2009cAsym/tpl-MNI152NLin2009cAsym_sub-0*_res-func_atlas-yeo7networks_label-defaultMode_mask.nii.gz``<br><br>


**2.4 Early visual ROIs derived from retinotopy**

For four subjects (sub-01, sub-02, sub-03 and sub-05) who completed a retinotopy task,
ROI masks from the early visual cortex were derived from their population
receptive fields and from group priors using the [Neuropythy toolbox](https://github.com/noahbenson/neuropythy).
ROI masks are available in MNI and native (T1w) space for the four subjects who completed the retinotopy task.

ROIs include:

* V1, V2, V3, V3a, V3b, VO1, VO2, hV4, LO1, LO2, TO1 and TO2

E.g., ``./tpl-sub0*T1w/tpl-sub*T1w_res-{anat, func}_atlas-retinoVisionNpythy_label-V1_mask.nii.gz``,
``./tpl-MNI152NLin2009cAsym/tpl-MNI152NLin2009cAsym_sub-0*_res-{func, anat}_atlas-retinoVisionNpythy_label-V1_mask.nii.gz``<br><br>


**2.5 Higher visual ROIs derived from fLoc**

For three subjects (sub-01, sub-02 and sub-03) who completed the fLoc task,
ROI masks from higher level visual areas with face, scene and
body preferences were identified with a combination of group priors and their
own data. Binary ROI masks are available in MNI and native (T1w) space.

ROIs include:

* Extrastriate body area (body-EBA)
* Fusiform face area (face-FFA)
* Occipital face area (face-OFA)
* Posterior superior temporal sulcus (face-pSTS)
* Medial place area (scene-MPA)
* Occipital place area (scene-OPA)
* Parahippocampal place area (scene-PPA)

E.g., ``./tpl-sub0*T1w/tpl-sub*T1w_res-func_atlas-fLocVisionTask_label-faceFFA_mask.nii.gz``,
``./tpl-MNI152NLin2009cAsym/tpl-MNI152NLin2009cAsym_sub-0*_res-func_atlas-fLocVisionTask_label-faceFFA_mask.nii.gz``

For all subjects, group parcels of regions with face, scene and
body preferences identified by the [Kanwisher lab](https://web.mit.edu/bcs/nklab/GSS.shtml#download) were also warped into
single-subject space.

E.g., ``./tpl-sub0*T1w/tpl-sub*T1w_res-func_atlas-fLocVisionKanwisher_label-faceFFA_mask.nii.gz``

The Kanwisher lab parcels are also available in MNI space in a standardized format that fits all subjects.

E.g., ``./tpl-MNI152NLin2009cAsym/tpl-MNI152NLin2009cAsym_res-func_atlas-fLocVisionKanwisher_label-faceFFA_mask.nii.gz``<br><br>

-------------------------
The [Courtois project on Neural Modelling (Courtois NeuroMod)](https://www.cneuromod.ca/) aims to train artificial neural networks using extensive experimental data on individual human brain activity and behaviour. Participants (n=6) performed a series of structured and naturalistic tasks while functional data being acquired in the MRI scanner . A extensive description can be found [here](https://docs.cneuromod.ca/en/latest/DATASETS.html).

Courtois NeuroMod data are [freely shared with the scientific community](https://docs.cneuromod.ca/en/latest/ACCESS.html) to advance research at the interface of neuroscience and artificial intelligence. Access to to the data is based on a registered access model. See the Courtois NeuroMod website for more information. Redistribution of data outside of the Courtois NeuroMod data bank is prohibited.
