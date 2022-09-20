PODD DEPLOYMENTS AT UW CSE2
===========================

The Post-Occupancy Data Devices (PODDs) were deployed to the CSE2 building
twice in 2019/2020, each time with 12-13 units distributed over three rooms.
Descriptions of the deployments, data (CSV) files, and measurements can be
found below.

See map images for the deployment locations of the PODDs within the CSE2
building, but note PODDs are sometimes found to have been moved from these
locations by the occupants (see deployment notes below). PODDs are generally
placed 30-36" above the floor (desk/table height) and attempts are made to
avoid objects/obstructions that would significantly impact light measurements.

Data is uploaded in real-time using a mesh network, with one coordinator
(unit 003 in this case) routing the PODD fleet data to the external network.
All readings are also saved locally on SD cards, which still contains any
data that was not uploaded due to network issues; however, this data set
does _not_ include such missing data (only the measurements that were
successfully uploaded).

Primary PODD contact:
  Chris Savage <csavage@lmnarchitects.com>
  LMN Architects


Deployment #1
-------------

The PODDs were placed in three nearby offices on the north face of level 3:
two 1-2 occupant offices (318, 334) and a larger multi-student office (331).
The PODDs were on site from 2019-10-10 to 2019-11-18, but did not operate
during that entire period as batteries deplete after 7-9 days.  There are two
roughly one-week periods of data starting from 10/10, when first deployed, and
from 11/1, when batteries were replaced.

Pre- and post-deployment calibration runs were performed at LMN, where all
units were co-located on a single table, experiencing almost identical
environmental conditions.  The CO2 sensors were recalibrated during the
pre-deployment run to correct drifting baseline levels, but were left as-is
during the post-deployment run (individual unit sensor drift should be
identifiable from this data).

Caveats:

  * When returning to replace batteries on 11/1, unit 005 was found in a
    different location than originally deployed.  It is unclear when this
    move happened.


Deployment #2
-------------

The PODDs were placed in three community areas on the north and east side:
the undergrad commons (120), undergrad computer lab (124), and the staff
lounge / research commons (250).  On-site deployment was from 2020-02-27 to
2020-03-12, though the batteries depleted on most units within 7-9 days of
first deployment.

A pre-deployment calibration run was performed at LMN, where all units were
co-located on a single table, experiencing almost identical environmental
conditions.  The CO2 sensors were recalibrated during the pre-deployment run
to correct drifting baseline levels, but no post-calibration run was
performed to identify drifting that occurred during the deployment.

Caveats:

  * Many of the globe temperature sensors were damaged / detached during
    this deployment.  Damage was easily repairable, but this makes globe
    data unreliable.
  * Deployment occurred during the start of COVID, though data collection
    should have finished before any significant building de-occupation
    occurred.
  * The three units in the research commons (room 250) were moved twice:
    once on 2020-02-28 that placed them together by the window, and again
    on 2020-03-04 that moved them back to the original locations, but not
    with the original units.


CSV Files
---------

The files contain the following five columns:

  * Database timestamp [UTC].  Since the data was uploaded as it was
    collected, this should be within a few seconds of sensor measurements.
  * The PODD unit label.
  * The measurement label.  See below for a description.
  * The measurement.  See below for a description.
  * The internal PODD timestamp.  Should be the local time when the
    measurement occurred, accounting for daylight savings.


Sensors/Measurements
--------------------

Datasheets for many of the sensors can be found here:
  https://github.com/lmnts/PODD/tree/master/Hardware/DataSheets/Sensors

  * 'AirTemp, 'Humidity': The ambient drybulb temperature [°F] and relative
    humidity [%] from an HIH-8120 sensor.  Accuracy is 0.5°C and 2%,
    respectively.  The readings from the coordinator unit (003) should be
    ignored as the ethernet module on this unit and this unit alone shed
    enough heat to bias the readings by 1-3°F.
  * 'GlobeTemp': Temperature readings [°F] from a PR222J2 thermistor placed
    in a black sphere (ping-pong ball) outside of the PODD enclosure.
    Intended to give an indication of the radiant temp, but this is _not_
    the radiant temp and there is currently insufficient calibration of
    this setup to convert to a radiant temp.  Might still be useful for a
    qualitative understanding of radiant vs drybulb conditions, but
    quantitative usage of this data should be avoided.
  * 'Light': The ambient light level [lux] from an upward-facing OPT3001
    light sensor.  This is a fairly accurate sensor (good spectral
    response and IR rejection), but the angular response means the lux
    values can be inaccurate if the area is very strongly side-lit (in
    which case the upward-facing luminance is not a good indication of
    the lighting conditions anyways).
  * 'Sound': Time-averaged sound levels [arbitrary units] using a ADMP401
    microphone.  Due to electronic noise and changing, per-unit baselines,
    the quality of this data is terrible and only the noisiest events can
    be observed.  Data should be avoided.
  * 'CO2': Carbon dioxide levels [ppm] as measured by a COZIR GC-0011
    sensor.  Accuracy is 30ppm plus +/-3% of the reading, but that does
    not include a drifting offset that requires regular calibration.
    The sensors were calibrated just prior to both deployments and the
    drift should be relatively small (< 100ppm) during the course of the
    ~ 1 month deployments.  Post-processing can be performed to counteract
    the offset by noting that the sensors should regularly reach ambient
    CO2 levels (410ppm) when spaces are unoccupied and there is sufficient
    ventilation.
  * 'CO': The carbon monoxide sensors were not connected, so there is no
    CO data (readings are all 0).
  * 'PM_2.5','PM_10': Particulate matter PM2.5 and PM10 values [ug/m3] as
    measured by the Sensirion SPS30 sensor.  Claimed accuracy is only
    +/- 10 ug/m3 below 100 ug/m3, but the fleet of sensors are consistent
    down to < 1 ug/m3 level.






