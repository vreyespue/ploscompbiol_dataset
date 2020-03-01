
#  Dataset for Reyes-Puerta et al., Plos Comput Biol, 2015

Paper: [Reyes-Puerta V, Kim S, Sun JJ, Imbrosci B, Kilb W & Luhmann HJ, Plos Comput Biol, 
2015](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1004121)

The present dataset contains responses from neurons in the barrel cortex 
of anesthetized rats to brief whisker deflections with specific stimulus 
features (location and frequency). 

All relevant data are contained in the Matlab 7.0 MAT-file `Spike_Stim_Data.mat`, which contains a structure 
for each of the animals included in the study (named Anm_01 to Anm_13). 
The employed data format follows loosely that established for the [FIND 
toolbox](https://www.ncbi.nlm.nih.gov/pubmed/18692360). 

An 8x16 channels probe was employed for the animals Anm_01 to Anm_09, 
allowing simultaneous recordings from 21 to 74 neurons (median 50) in 3 
to 4 barrel-related columns (median 4). A 1x16 channels probe was used 
in the remaining animals Anm_10 to Anm_13, allowing simultaneous 
recordings from 5 to 9 neurons (median 6.5) in a single barrel-related 
column. 

From the total of 437 neurons included in the present study, putative 
inhibitory (INH, 14.2%, n=62) and excitatory (EXC, 85.8%, n=375) neurons 
were identified according to their spike width and waveform asymmetry, 
from which 7% (4 INH, 27 EXC) were located in layer 2/3 (L2/3), 14.9% 
(15 INH, 50 EXC) in L4, 44.6% (14 INH, 181 EXC) in L5A and 33.4% (29 
INH, 117 EXC) in L5B/6. INH neurons presented distinct spike waveforms, 
and were associated to higher spontaneous activity than their EXC 
counterparts across all layers (see the corresponding 
[paper](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1004121)
for further details). 

In each experiment (i.e. data related to a single animal), the following 
stimulation protocol was repeated for each of the selected (2 to 3) 
target whiskers. First a block of stimuli was applied at low-frequency, 
typically containing 200 trials with an inter-trial-interval of 5 to 30 
s (thus corresponding to stimulation frequencies between 0.03 and 0.2 
Hz). Afterwards blocks of stimuli were applied at higher frequencies (1, 
2, 4, 7 and 10 Hz), each of them typically containing 100 trials. 
Individual blocks of trials were separated by periods of at least 10 s. 
For all stimuli, the voltage pulse controlling the piezoelectric bimorph 
actuator was an up-down square step function of 2 ms duration. 


## Fields stored in the Anm_01 TO Anm_13 structures 

For each one of the structures Anm_01 to Anm_13, the following 
information items are provided into individual fields: 

- **animal_id** (integer): ID number of the animal (1 to 13).
- **animal_age** (integer): Age of the animal at the day of the experiment (in days).
- **animal_weight** (integer): Weight of the animal at the day of the 
experiment (in grams).
- **elect_info** (string): Probe model used for the experiment. ‘a8x16’ 
refers to the 8x16 channels probe, and ‘a1x16’ to the 1x16 channels 
probe. For further details about the probe specifications, please visit 
the [Neuronexus website](http://www.neuronexus.com).
- **NeuralID** (integer array): Vector containing for each one of the 
recorded cells their specific ID number. Typically it goes from 1 to 
N_neurons. 
- **NeuralLayer** (integer array, one-dimensional): Represents for each 
recorded cell the specific layer at which it is located. Note that in 
this simplified nomenclature, 2 corresponds to L2/3, 4 to L4, 5 to L5A, 
and 6 to L5B/6.
- **NeuralDepth** (integer array, one-dimensional): For each recorded cell, 
this number represents the specific depth under the cortical surface at which the 
corresponding probe channel was located. This information was inferred 
using current source density analysis of the local field potentials upon 
whisker deflection (see publication for further details). 
- **NeuralBarrel** (string cell array, one-dimensional): For each cell, the 
specific barrel-related column at which it was located (inferred using 
voltage-sensitive dye imaging, and confirmed through posthoc 
histological verification, see publication for further details). 
- **NeuralCharactInhExc** (string cell array, one-dimensional): For each 
cell, its neural type (‘INH’ for putative inhibitory, ‘EXC’ for 
putative excitatory, see above). 
- **Block_XX_Whk_YY_Frq_ZZ**: Structures containing the information related 
to the different blocks of trials (see following section for further 
details). 


## Fields stored in the Block_XX_Whk_YY_Frq_ZZ sub-structures 

For each block of trials recorded in a specific experiment (i.e. 
individual animal), a structure was created containing the 
corresponding information. These structures follow the nomenclature 
Block_XX_Whk_YY_Frq_ZZ, in which XX denotes the ID number of the block 
(thus representing their sequential order of recording), YY denotes the 
specific stimulated whisker (only one whisker in each block), and ZZ the 
frequency of stimulation. Each block structure contains the following fields: 

- **stim_whisker** (string): Whisker used for stimulation within the block.
- **stim_freq** (double): Frequency used for stimulation (in Hertz).
- **block_time_start** (double): Total time (with respect to the beginning 
of the recording) at which the block of stimuli starts (in secs).
- **block_time_end** (double): Total time (with respect to the beginning 
of the recording) at which the block of stimuli ends (in secs).
- **trials(:)** (struct array, one-dimensional): Structures containing the 
information related to the different trials (see following section for further details). 



## Fields stored in the trials(:) sub-sub-structures 

Each trial in the present dataset contains the spike times of all 
neurons within a time window of 100 ms after whisker stimulation. For 
each one of the structures in Anm_ID.Block_XX_Whk_YY_Frq_ZZ.trials(:), 
the following information items are provided into individual fields: 

- **trial_time_start** (double): Total time (with respect to the beginning 
of the recording) at which the trial starts (in secs).
- **trial_time_end** (double): Total time (with respect to the beginning of 
the recording) at which the trial ends (in secs).
- **NeuralTimeStamp** (double cell array, one-dimensional): For each 
recorded cell, time stamps of the detected and sorted spikes within a 
time window of 100 ms after whisker stimulation. Time values are given 
in seconds and are global, i.e. with respect to the beginning of the 
recording. Further specifications of the recorded cells can be found 
within the fields Anm_ID.Neural* (see above). 

