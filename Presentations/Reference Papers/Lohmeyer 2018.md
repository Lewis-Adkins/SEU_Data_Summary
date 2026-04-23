**Title:** Telemetry Fault-Detection Algorithms: Applications for Spacecraft Monitoring and Space Environment Sensing
**Authors:** Ashley Carlton, Rachel Morgan, Whitney Lohmeyer, Kerri Cahoy
**Publisher:** Journal of Aerospace Information Systems
**DOI:** [10.2514/1.I010587](https://arc.aiaa.org/doi/10.2514/1.I010587)

# Abstract

Telemetry from solid state power amplifiers and amplifier thermistors from 32 GEO Earth orbit communications satellites from 1991 to 2015 are examined. Transient event detection and change-point event detection techniques that use a sliding window-based median are used, statistically evaluating the telemetry stream compared to the local norm. This approach allows application of the algorithms to any spacecraft platform because there is no reliance in the algorithms on satellite- or component-specific parameters, and it does not require a priori knowledge about the data distribution (Not satellite specific algorithm). used to identify 6 events that affect 51-53 telemetry streams at once

# I. Introduction

## A. Motivation

GEO Satellites are important from communication between all industries (comms/defense). Satellite failures that degrade performance can be highly disruptive. All satellites at some point will experience "anomalies" during their lifetime from space environment, human error, age of component, or software modifications.  impacts from space weather
1. surface charging
	1. differences between ambient electron and ion fluxes resulting in electrostatic discharge
2. internal charging
3. SEUs
4. Ionizing does (TID effects)
LEO satellites are most at risk but GEO sats can be at risk due to their entrance and exits out of the plasmasphere leading to onboard system failures. "soft" anomalies from SEU can be fixed with EDAC but "hard" anomaly  is not recoverable.

Telemetry (Greek for measurement at a distance) provides primary source of health information available from space craft with downlinking electrical signals proportional to the quantity being measured. "Housekeeping telemetry" monitors health of components. One large comm sat can have thousands of telemetry streams. ComSat current and temperature telemetry from solid stat power amplifiers (SSPAs) and thermistors are studied 

## B. Fault Detection Techniques

Long operational missions require updated fault detection and diagnosis techniques. simple limit-checking methods called "thresholding" including hard and soft limits are used for components but could change due to degradation. 

Polling (voting) schemes are used on a system level. techniques include "consecutive occurrence counters" and "persistence filters" to quickly assess systemwide faults.

New fault detections are being developed but not deployed just yet due to computational resource and limitations in current models.

## C. Spacecraft as a Sensor

"Spacecraft as a sensor" most notably used by Aerospace Corp. in El Segundo CA (Bowman and DeSieno 1997) (No link available?)

# II. Approach 

## A. Overview

Only using "Housekeeping" telemetry, algorithms (algos) developed to extract unusual events. Transient and change -point detections  algos that evaluate telemetry stream to a local norm (non satellite specific)

Events are identifies on spacecraft systems and number of telemetry streams is increased at each level. First detection algos are applied to each individual telemetry stream to identify events in single telemetry streams on component level. Then, events detected from all telemetry streams of a certain type (temperature, current, etc) or subsystem are examined. similar performance might be expected from components of same type or subsystem, so comparing and comping events may reveal affects.

At system level, detections of events from telemetry streams for many subssytem are considered. when compiling and comparing events in datasets from multiple satellites, intersections of system level events could be an enviromental event (natural or manmade). These detected events are then compared to space weather evetns and publiclty available anomaly lists, SpaceTrak and Serdata

## B. Data Used in This Analysis 

GEO Comsat telemetry used for two reasons;
1. ComSat is importnat
2. Decades of telemetry
ComSat only had design lifetime of 10-15 years but many sats operate beyond for ROI reasons. these long missions interact with temporal variations in the space enviroment (11 year solar cycle).

## C. Telemetry Characteristics and Algorithm Goals

Assessing the characteristics of our telemetry dataset to design algo: Time - Series data. Diffult to apply techniques in one domain (not specified) to another. Anomalies could be defined differently in different domains (satellites, studies?). 

### C1. Point and Contextual Anomalies

In telemetry, time series dataset, point anomalies and contextual anomalies can occur. Point anomalies are when individual data instances can be considered anomalous with respect to the rest of the data. Thresholding techniques can often detect point anomalies if obvious. Point anomalies for sequence data,  can often appear as a set or collective anomalies more difficult to detect.

Contextual anomalies occur if a data instance is only anomalous in a certain context. Example:  Satellite temperature measure 50$\degree$C may make sense during certain times but may be contextually anomalous  during eclipse periods. normal behavior can evolve over time.

### C2. Labeled Telemetry Data

Labeled training data where datasets instances are labeled normal or anomalous are impossible to obtain. Identical satellites may yield different telemetry. environment and operational demands are different.

Therefore detection algo has been developed to be "unsupervised" (not requiring training data). Technique may suffer from a high false alarm rate

### C3. Noise

Difficult to identify and extract. Onboard processor interruptions, corruptions of data, error in comm access can affect telemetry signal. Dropouts in the data where there are zeros or discontinuous jumps that last from 12-24 hours with frequency 1-2 a year

### C4. Output

"Event score" indictiave of the degree to which a data instance is anomalous. The scoring enables a rnaked list of anomalies from which a user can select the scoring threshold for detection.

## D. Spacecraft Telemetry

GEO ComSat telemetry used in this analysis from MIT with two commercial operators: Intelsat and Inmarsat. 
### D1. Inmarsat Data
From 2011 22 years of archived telemetry from 10 satellites in three fleets (different manufactures). 
Data acquired (1 GB Total):
* Solid State Power Amplifier (SSPA) current and temperature telemetry
* Solar Array Power
* Total Bus Loads
* Anomaly and SEU lists <- Already has the Timestamped SEU???

### D2. IntelSat Data
From 2014, 20 years of archived telemetry from 22 satellites in four fleets (different manufactures)
Data acquired (.5 TB Total)
* SSPA current and temperature telemetry
* Traveling Wave Tube Amplifiers (TWTAs)
* Solar Panel Current
* Total Bus Power
* Shunt Loads
* Magnetometer Measurements
Focus on SSPA current and temperature measurements with the SEU lists from 4 satellites

# E. Space Environment Data

Detection algo in relation to space enviroment measurements int GEO. Using:
* GOES >2 MeV electron flux
* GOES >10 MeV proton flux
* [Kp index]([https://www.swpc.noaa.gov/products/planetary-k-index](https://wdc.kugi.kyoto-u.ac.jp/dstdir/index.html)) (mesaure of the geomagentic activity)
* [Sunspot daily averages ](https://www.sidc.be/SILSO/datafiles)from World Data Center in Brussels
* [Solar Wind Data](https://www.swpc.noaa.gov/products/ace-real-time-solar-wind) from Advanced Composition Explorer (ACE)

# F. Known Satellite Anomaly Lists

Reported satellite anomalies in or near GEO at same time as events detects in the spacecraft telemetry.
* [NOAA National Geophysical Data Center](https://www.ngdc.noaa.gov/stp/satellite/anomaly/doc/5jsumm.txt) <- (only one that works)
* [SpaceTrak](https://www.slingshot.space/product-seradata) <-(book a demo for data?)
* [Satellite News Digest](https://sat-nd.com) <- (links to website data nowhere)

# III. Algorithm Descriptions

Analysis includes methods for detecting transient events (spikes, jumps, drops) and for detecting change points in the telemetry. Use sliding median windows to find transients and change points ([Turkey 1977](https://www.jstor.org/stable/2529486?origin=crossref)). Good for no domain knowledge required, and the algos are not satellite specific. No assumption in distribution of telemetry and no training data are required.

Tested data with a one-sample [Komolgorov Smirnov](https://www.tandfonline.com/doi/abs/10.1080/01621459.1951.10500769) test. Telemetery systems from other components tested and yielded a stadnard normal cumulative distribution function (CDF). Therefore the median is chosen as the statistical metric instead of the mean becaouse of its more robustness to outliers.

## A. Transient Event Detection

based on Turkey method. data segmented into same size bins (or windows) over seven days that allow for definition of normal to change over the dataset. One orbit of GEO satellite is 1 day so seven days mitigate effects of orbit. telemetry sampling rate is hourly - 168 points per bin. variable bin size and number of data points.

The event score $S$ is the absolute difference between the datapoint $x_i$ and local median $\text{median(X)}$ divided by the standard deviation $\sigma$
$$
S = \frac{| x_i - \text{median}(X)|}{\sigma}
$$
choosing threshold for event score lets a user choose how many events to keep.

## B. Change Point Event Detection

Techniques for change point detection can be found here:
* [Wang 2011](https://ieeexplore.ieee.org/document/5990537)
* [Reeves 2007](https://journals.ametsoc.org/view/journals/apme/46/6/jam2493.1.xml)
* [Wang 2011](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0020060)
* [Yamanishi 2004](https://link.springer.com/article/10.1023/B:DAMI.0000023676.72185.7c)

To detect change points in time series and determine trends you can use piecewise linear approximations (PLAs). PLAs use to approximate the data in bins. The median for each bin is compared. no dynamic bin sizing.

Data initially segmented into 2-day bins and weekly bin statistics (median, std dev, etc) are computed. Bins that show large changes in median between adjacent bins an optimization routing is employted using  comhination of moving windows one data point at a time (hourly resolution) to maximize the difference in the median between two adjacent windows in the local time frame of the originally large change in median.

The event score is determined by the magnitude of the change in median at the event date
$$
S = \frac{| \text{median}(X_1) - \text{median}(X_2)|}{|\text{median}(X_1)|} \times 100
$$
Change point detection algorithm reports the largest changes in median using the event score $S$ and numbers the events by their event score.

# IV. Results and Event Analysis

We are looking for events that are detected on the same dates from components on the same satellite and event dates common to multiple satellites, which may be indicative of a system-level event and an environmental level event, respectively.

## A. Compiling Events from Individual Types of Components

When comparing the events detected for a type of component on a satellite we find clusters of events at dates that seem unlikely to be random. This suggest that there is some relationship between the transients in the telemetry and system- level events

THERM -INTELSAT-1/2 doesn't show clustering with other thermistor events. could be due to physical locations of thermistors (near thrusters?)

Periodicity of events explained possible by eclipse seasons of satellite.

## B. Comping Events from Components on One Satellite

there are common event dates regardless of component type indicating possible system level events. For each satellite that had maneuvered during its lifetime the maneuver is detected as on of the top 5 events for each of the satellites. This is a a significant finding because this information could be useful for groups interested in a satellites activity, such as for a space situational awareness application.

## C. Compiling Events from Multiple Satellites

Same event detections were deployed on the other satellites in the dataset. top events from one satellite coincide with a top event form another satellite.  Telemetry from each satellite spans over a decade and so it is unlikely that these events are unrelated. It could be indicative of an environmental level event

# V. Conclusion

Change point detection and transient detection algorithms have been developed that identify deviations from normal, avoiding component- or satellite-specific conditioning. Although the metrics are well established, these first-step methods are not currently used to evaluate spacecraft health using telemetry. Analyzing housekeeping telemetry from 32 geostationary Earth orbit (GEO) ComSats from 1991 to 2015, we find transient and change point events that occur in many or all of the telemetry files, indicating potential system-level effects on certain dates. Spacecraft maneuvers are detected in five out of five cases. Events from thermistor telemetry show periodicity with eclipse season. At the environment level, a top event date is found that occurs in two satellites: 4 December 2007. The space environment has been considered as well as available operational information and anomaly reports from other spacecraft in GEO. The present findings have been shared with the satellite operators, who were interested in the results and are using the approach to improve anomaly management in their systems. Government agencies were also interested in these findings, and requests for additional information have been supported. Further analysis with the events detected is required to determine if a relationship exists.