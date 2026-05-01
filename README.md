# SWLG_Code Summary

## Code

**Location**: SWLG_Code/code

seu_geo_temporal.ipynb - marks the geolocation and temporal occurences of SEUs <br>
seu_predict_ml.ipynb - characterizes proton flux data to be fred into machine learning model.




## Data Files 
**Location:** SWLG_Code/code/data

### SEU - Timestamps and Geolocation

**Location**: SWLG_Code/code/data/seu_timestamp 

#### TDRS-5 Satellite

**Description:** NCEI created the satellite anomalies database from external data in an effort to more clearly understand and document how space weather events affected satellites. <br>
Connecting individual anomalies to space weather events is a complex task that typically requires collaboration between satellite operators, engineers, and space weather subject matter experts. The information <br>produced in that discourse can be difficult to obtain.<br>

**Data:** [tdrs5j](https://www.ngdc.noaa.gov/stp/satellite/anomaly/doc/)  <- is actully only a tdrs 1 timstamp of SEU<br>

**Paper:** [[Lohmeyer 2018]]<br>

TDRS-5 Satellite

#### TDRS-1 Satellite 

**Description:** NCEI created the satellite anomalies database from external data in an effort to more clearly understand and document how space weather events affected satellites. 
Connecting individual anomalies to space weather events is a complex task that typically requires collaboration between satellite operators, engineers, and space weather subject matter experts. The information produced in that discourse can be difficult to obtain.

**Data:** [TDRS-1 SEU table](https://www.ncei.noaa.gov/products/satellite-anomalies) <- anom5j database for a bnunch of satellites with minimal SEU data<br>

**Paper:** [[Lohmeyer 2013]]<br>

#### GOES-16 Satellite

**Description:** NCEI created the satellite anomalies database from external data in an effort to more clearly understand and document how space weather events affected satellites. 
Connecting individual anomalies to space weather events is a complex task that typically requires collaboration between satellite operators, engineers, and space weather subject matter experts. The information produced in that discourse can be difficult to obtain.

**Data:** [GOES-16 and GOES-17 EXIS Space Wire anomalies](https://www.ncei.noaa.gov/products/satellite-anomalies) 

**Paper:** [[Lohmeyer 2018]]

#### GOES-17 Satellite

**Description:** NCEI created the satellite anomalies database from external data in an effort to more clearly understand and document how space weather events affected satellites. 
Connecting individual anomalies to space weather events is a complex task that typically requires collaboration between satellite operators, engineers, and space weather subject matter experts. The information produced in that discourse can be difficult to obtain.

**Data:** [GOES-16 and GOES-17 EXIS Space Wire anomalies](https://www.ncei.noaa.gov/products/satellite-anomalies) 

**Paper:** [[Lohmeyer 2018]]
#### Flying Laptop Satellite

**Description**: Single Event Upset Data with Position Data used in "Single Event Upsets in flight observation and analysis for the “Flying Laptop” small satellite". Data measured by the FLP UT-699 Onboard Computer. (2019-06-27)

**Data:** [Flying Laptop SEU Data](https://darus.uni-stuttgart.de/dataset.xhtml?persistentId=doi:10.18419/darus-443) 

**Paper:** [[Noeldeke 2021]]

### Space Enviromental Data

**Location: ** SWLG_Code/code/data/enviromental

#### SOHO/EPHIN - Proton
Description: Interface to produce plots, listings or output files from SOHO Proton and Helium Instrument (EPHIN, level3), hour averages

Data:  https://omniweb.gsfc.nasa.gov/ftpbrowser/soho_ephin_flux_hr.html
Paper: [[Torres 2025]]

# Telemetry Data

## Jason-3
**Description:** These data consist of raw Level-0 telemetry data from the Jason-3 spacecraft. There are three datatypes available: Housekeeping Telemetry - Recorded (HKTM-R) is stored on the spacecraft for later downlink; Payload Telemetry 1 (PLTM-1) is the payload science data from the core-mission payloads: Poseidon, DORIS, AMR, and GPSP; and Payload Telemetry 2 (PLTM-2) is the payload science data from the passenger mission of opportunity payloads. They are available as CCSDS packet files.
**Data**: [NCEI](https://www.ncei.noaa.gov/access/metadata/landing-page/bin/iso?id=gov.noaa.nodc:Jason3-Telemetry)
**Paper**: N/A - Just found google searching

## Deep Space Climate Observatory (DSCOVR)
**Description:** The Deep Space Climate Observatory (DSCOVR) is a [solar wind](https://en.wikipedia.org/wiki/Solar_wind "(opens in a new window)") monitoring system that provides early warnings before a Coronal Mass Ejection (CME) or shockwave strikes our planet. DSCOVR data supports forecasts and research that allow power grid and satellite operators time to protect critical infrastructure from [damage or disruption](http://www.swpc.noaa.gov/impacts).
**Data**: [NCEI]([https://www.ncei.noaa.gov/access/metadata/landing-page/bin/iso?id=gov.noaa.nodc:Jason3-Telemetry](https://www.ncei.noaa.gov/products/deep-space-climate-observatory-dscovr))
**Paper**: N/A - Just found google searching




