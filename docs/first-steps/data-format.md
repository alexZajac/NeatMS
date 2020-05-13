# Data format

The module requires two types of input:

* Raw data files in mzML format.
* One feature table file in .csv format.

## Raw data in mzML

Most of vendor format can be converted to mzML format using msconvert from proteowizard... (TODO: give links) 

## Feature table file format

The feature table file format can be easily created from any peak detection pipeline. Below, we give instruction on how to create this csv file from mzMine 2.0 and XCMS.

Every row represent a different peak found in one or more samples.
The first two columns are sample independant and should contain the consensus m/z  and retention time of the peak accross the samples. Every other column is sample specific, each sample requiring 7 columns with different information (m/z, RT, RT start, RT end, height, m/z min, m/z max). The name of each column should be respected for the file to be correctly read. Every sample present in the feature table should match the list of raw files present in the raw data folder. The value 0 is used when a peak is missing from a sample. 

Here is the list of headers for the first 9 columns of an experiment containing one sample file named sample1.mzML.

* row m/z 
* row retention time 
* sample1.mzML Peak m/z 
* sample1.mzML Peak RT 
* sample1.mzML Peak RT start
* sample1.mzML Peak RT end 
* sample1.mzML Peak height 
* sample1.mzML Peak m/z min 
* sample1.mzML Peak m/z max 

An example file is available in the data folder of the github repository (TODO: link)

### Feature table export from mzMine 2.0

The feature table can be exported after the aligning peaks accross samples, this is important as we need all the samples together in a single file. NeatMS does not currently support the import of sample specific feature table.

After selecting the aligned peak list on the right side panel in mzMine2, you can access the export panel through *Peak list methods* > *Export/Import* > *Export to CSV file*.

First, make sure the *Field separator* is `,`. 

Select the following elements in the *Export common elements* panel:

* Export row m/z
* Export row retention time

Select the following in the *Export data file elements* panel:

* Peak m/z 
* Peak RT 
* Peak RT start
* Peak RT end 
* Peak height 
* Peak m/z min 
* Peak m/z max

Make sure to unselect any other element and click OK. Your feature table file is now ready.

MZmine 2 also provides filtering options, we recommend to not filter the peaks at this stage as it can be done in NeatMS, but doing it now will not impact on NeatMS usage.

### Feature table export from XCMS

This feature is in development and is coming soon.