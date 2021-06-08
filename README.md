# PPG-Signal-Processing

### Stanford Dataset:
 
30 sec PPG signal (20Hz) => FIR low-pass filter (5Hz) => Scaling (mean 0, unit variance)

### DeepBeat Dataset:

25 sec PPG signal (128Hz) => Downsample by 4 (32Hz) => Band-pass filter => Standardized [0,1]


*we’re using the dataset of DeepBeat

## Processing:

*our initial signal is 10Hz <br/>
*has some reading errors 

## Layer 1: 
Divide signal in segments using window_size & overlap. Eliminate segments that has - <br/>
i) a range that is at least 50% of range of the raw signal <br/>
ii) a maximum that is 90% the raw signal’s maximum <br/>
iii) a minimum that is the (minimum + 10%) of the raw signal <br/>

## Layer 2: 
Band-pass filter (0.5Hz - 4.00Hz) / (30bpm -240 bpm)

## Layer 3: 
Resample the signal (increase frequency). <br/>
Right now increasing from 10Hz to 100Hz (the more, the better for hertpy to analyze but 100Hz is good enough!)

## Layer 4:
Segments are eliminated those hertpy can’t process due to ‘bad signal warning’. <br/>
Returns the working_data to use in peak analysis later


## Layer 5:
Check peak detection ratio. <br/>
Eliminate signals using a cutoff ratio for rejected peaks.

## Layer 6:
Downsample to 32Hz + divide in segments of 25sec + standardize [0,1]

 
** (32x25) = 800 <br/>
So, layer6 needs input to be at least 800.
