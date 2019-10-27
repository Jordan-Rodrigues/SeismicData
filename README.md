# SeismicData
## Inspiration
The US government gathers seismic data globally and must be capable of efficiently parsing the data and quickly deriving insights. Currently, individuals are hired to continuously watch the data throughout the day. With modern technology, this is not necessary and likely does not result in ideal, consistent performance. Our solution automates an anomaly detection solution that extracts up and down-shifts within the frequency domain of seismic data. 

## Introduction
Our scripts analyze seismic data from sensors placed throughout the world. When there is a signal of importance, shown by changes in the frequency of high amplitude signals, we detect the anomaly using a hybrid Machine Learning and Digital Signal Processing approach. We can then notify the correct personnel and provide insight about the signal. Our solution is designed to preform as much analysis of that data as possible to minimize the amount of human capable necessary to understand the signals. Accordingly, our solution provides the bandwidth of the signal and time at which it occurred. 

## Key Components
This project identifies anomalies in seismographic information via two main approaches.  The first approach is entirely based in computer vision.  Given a generated seismograph, a variety of convolutions and filters are applied to find distinct lines, which correspond to the anomalies we are looking for.  From here, we extract the frequency and duration and have exported those for further analysis.  In addition, each of these graphs are then clustered, allowing us to categorize these anomalies by their duration, frequency, etc.

#### CV Approach Workflow: 
 - Generated spectrogram from sensor-derived .wav or .sac files
 - Converted spectrogram to image
 - Extracted up/downshifts (anomalous events) by applying convolutional filters for edge detection
 - Derived durations and frequency ranges of shifts using object detection/image segmentation
 - Clustered processed images to assign images to 5 distinct event classes
 - Appended derived data into a dataframe & performed data exploration

The second approach is more heavily based on signal filtering.  Essentially, we recognized that the anomalies we are looking for can be characterized by relatively constant amplitude, with changing frequency with respect to time.  We located these anomalies by taking “slices” of the data at constant amplitude.  From there we applied filters to find the parts of these slices that were continuous and changing over time. 

## Challenges we ran into
In terms of our vision processing approach we had trouble with filtering properly.  It took a while to realize that we couldn’t rely on color, rather we had to consider edge detection.  After this main roadblock vision processing went well.  In terms of the signal processing approach, we struggled for a while to visualize our data.  We were plotting large amounts of data in 3D to get an intuition of what an anomaly would like.  It took many hours, but eventually we became comfortable enough with the data to realize that our slicing approach would work very well.

## What we learned
We were all very happy to gain practical experience in signal processing, especially since half of the team had never dealt with it before.  The team was immensely effective at spreading expertise.  For instance, some of us were experienced in DSP, but others were experienced in vision processing, and together we effectively taught each other whatever we needed to know. We are super proud that we got the algorithms working and correctly detecting signals!


