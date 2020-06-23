<!-- #region -->
# Ground Motion Displacement RMS vs Time

![run notebooks](https://github.com/ANU-RSES-Education/SeismicNoise_AuSIS_MAR/workflows/run%20notebooks/badge.svg)

This repository is a self-updating version of the [seismic social-distancing "monitoring" toolkit](https://github.com/ThomasLecocq/SeismoRMS) of Thomas Lecocq, Fred Massin, and Claudio Satriano that was designed to show the effect on seismic noise of stay-at-home orders for the COVID19 emergency. The notebook software is bundled with some code to trigger github actions to download any new data and update the images in this README file.

This example is from the Suburban Adelaide in South Australia

<!-- #endregion -->

## Classic plot

![classic](results/latest.png)

## Hourly plot

![hourly](results/latest-hourly.png)


## Health checker 

Verify that the daily data is complete and monitor the updates from [this plot](results/latest-gridmap.png). If days are incomplete, try deleting the .npz file that is cached and it will be rebuilt when you run the notebook locally or when the scheduled job re-runs (assuming the data are available on the server).

## Tabulated results

The [tabulated output](results/latest.csv) of the run is also available.

## Help

To run the notebook to check everything is ok just run the `notebook_runner.sh` script. This will download all the data, process it and build the plots. You can check in the .npz files in the data directory to save time when the scripts run online, but you should avoid checking in the large `data/*mseed` files or anything that is located in `workdir`. By default, these files will be ignored by git. Take care that the github actions will update the repository. 

### AuSIS stations

A list of the AuSIS stations can be obtained with this code snippet. 

```python
from obspy.clients.fdsn import Client
from obspy import UTCDateTime

c = Client("IRIS")
print(c.get_stations(UTCDateTime(), network="S1", channel="BHZ"))
```

### Community indicators

The data and scripts to make this plot are provided in the notebooks directory. 

![community](notebooks/CoronaVirusCommunityIndicators.png)

but this does not automatically update because the searches for the data are not yet fully automated. 

