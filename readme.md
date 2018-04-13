# Analyzing Arizona's traffic stops

The [Stanford Open Policing Project](https://openpolicing.stanford.edu/) has collected data on more than 130 million traffic stops conducted by state law enforcement agencies in 31 states. Included in the data are more than 2.25 million traffic stops conducted by the Arizona Highway Patrol between 2009 and 2015. This tutorial will walk you through an analysis meant to check for racial bias by looking at search rates in the data.

## Before we start

This tutorial uses Python 3.6.4 and the Pandas library to analyze the traffic stops. In addition to those two items you will need to have Altair (a charting library) and Jupyter installed. These libraries are already installed if you are working on one of our virtual machines. Otherwise you will need to run `pip install -r requirements.txt` before beginning.

## Getting the data

We have included the entire 2.25 million traffic stops on the USB drive provided to you at the beginning of the class. If you do not have a USB drive, the data can be downloaded [here](https://stacks.stanford.edu/file/druid:py883nd2578/AZ-clean.csv.gz). Unfortunately the dataset is probably too large to fit on your virtual machine. The good news is we already have taught you the tools to separate out a subset of the data based on the latest year available. Make sure to check your line count afterwords to make sure you got everything.

```bash
$ cat /media/<USB DRIVE NAME>/data/AZ-clean.csv | grep 'AZ-2015' | wc -l
> 450519
$ head -n 1 /media/<USB DRIVE NAME>/data/AZ-clean.csv > ~/code/az_stops/data/az_2015.csv
$ cat /media/<USB DRIVE NAME>/data/AZ-clean.csv | grep 'AZ-2015' >> ~/code/az_stops/data/az_2015.csv
$ wc -l ~/code/az_stops/data/az_2015.csv
> 450520
```

Remember the final count will be off by one because we added the header row into our new csv. Now that we have the latest year we are ready to begin our analysis.
