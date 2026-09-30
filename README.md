# SBIG Detector Characterization

Analyses of an SBIG astronomical detector to characterize its sources of intrinsic noise 
and pixel uniformity using dark, bias, and flat field exposures

## Experimental Setup

- Detector: SBIG astronomical camera
- Reported Detector gain: 0.38 e-/ADU
- Operating temperature: Set to -5 °C
- Filter: None
- Bias exposures: 0.09s, 5 frames
- Dark exposures: 0.09, 1, 2, 5, and 10 seconds; 3 frames per exposure
- Flat exposures: 0.09, 1, and 2 seconds; 3 frames per exposure

The room was kept dark during dark exposures. Bias and dark frames
were acquired with the shutter closed. Flat-field exposures used a
uniformly illuminated laptop screen.

## Methods
### Bias Signal and Read Noise

Five bias frames were median-combined to create a master bias frame. 
The master bias provides the detector's baseline readout signal.
The standard deviation of each pixel across the individual bias frames was
used to calculate the read noise. Taking the means of each of these arrays gave an average bias signal and read noise per pixel.

### Dark Current

The master bias was subtracted from each dark exposure. Frames with the
same exposure time were then median combined. For each pixel, a linear fit was performed between dark signal and exposure
time. The slopes of these fits gave the dark currents. The dark-current map was then converted from ADU/s to electrons/s using
the detector gain, and the mean of all the slopes was used to get an average dark current.

### Total Noise

The detector noise was modeled as the combination of read noise and
dark-current shot noise:

    σ_total(t) = sqrt(σ_read² + D t)

where:

- σ_read is the read noise in electrons
- D is the dark current in electrons/s
- t is the exposure time in seconds

### Flat-Field and Pixel Response

Flat frames were corrected by subtracting the master bias and the
dark current multiplied by the exposure time.
Master flats were created for each exposure time by median combining the
three exposures. Each master flat was then normalized by dividing by its median pixel value. A normalized
value of 1 represents the median detector response, while values above or
below 1 represent pixels with relatively higher or lower sensitivity.


## Results and Observations

### Read Noise

The detector had an average baseline signal of approximately 1048 ADU and
an average read noise of 26.4 ADU. Most pixels had
baseline signals concentrated around 1000–1100 ADU, while the read noise
distribution was concentrated near 26 ADU with a tail extending to higher noises.

### Dark Current

The average dark current was measured to be 0.932 ADU/s, corresponding to
approximately 0.35 e-/s. The dark-current map showed substantial pixel-to-pixel variation, including
some pixels with negative fitted slopes. The short exposure times used for
the calibration may have contributed to the large variation in these measurements.


### Pixel Response

The normalized flat fields revealed spatial variations in detector
sensitivity. The detector showed reduced sensitivity along part of one
edge and increased sensitivity toward the middle of the detector. The mean standard deviation of the normalized flat fields 
was approximately 13.51%, representing the measured pixel-response variation in these
calibration frames.

## Conclusions

The main findings for the detectors properties include:

- A baseline signal of approximately 1048 ADU or 398 e-
- Read noise of approximately 26.4 ADU or 10.0 e-
- Dark current of approximately 0.932 ADU/s or 0.35 e-/s
- A pixel response variation of 13.5%, with one side of the detector being less sensitive.

These calibration measurements can be used to correct for signals produces by the detector
and isolate signals from the observation target in future exposures. 


## Future Work

Further work to better characterize the SBIG detector could be done by:

- Taking calibration exposures at other detector gain settings
- Using longer exposure times for dark and flat exposures
- Measuring detector behavior at different operating temperatures


## Tools

- Python
- NumPy
- Matplotlib
- Astropy
- FITS
