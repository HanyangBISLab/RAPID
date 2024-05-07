# RAPID
## Ratio based Algorithm for Polypeptide Isotopic cluster Determination
RAPID is a command-line program to determine isotopic clusters and their monoisotopic <br>
masses based on a new probabilistic model. It determines monoisotopic masses of peptides,<br>
especially peptides of mass < 5000 Da. RAPID takes the Thermo Finnigan RAW and mzXML <br>
file formats as input. It automatically processes all the MS scans of multiple RAW flies.<br>
The results are published in a table format similar to that of ICR-2LS or Decon2LS.<br>
<hr>


## 1. Usage
<pre>
- Command: java -jar rapid.jar configFile
- Example: java -jar rapid.jar foo.txt
</pre>
## 2. Parameters (See foo.txt file)
<pre>
- File::DataList (required)
 List of input RAW files. All input files are processed sequentially. Each result of a 
 input file is published in a table format similar to that of ICR-2LS or Decon2LS. See 
 the 'DeconvPep::OutputFormat' parameter. The result files are generated in the same folder 
 as the input files. 
 
- File::DataType (default: FINNIGAN)
 Sets the data type of input files.
	FINNIGAN: Thermo Finnigan .RAW files (requires the same or compatible version of 
		Xcalibur where .RAW files are generated)
	MZXML: mzXML files

- PeakPicking::SNRThreshold (default: 3.0)
 Sets the Signal-To-Noise Ratio.

- PeakPicking::BackgroundRatio (default: 5.0)
 Sets the maximum intensity level to be considered as background.

- PeakPicking::Partition (default: 5)
 Sets the number of partitions of a scan for peak picking. 

- PeakPicking::FitType (default: QUADRATIC)
 Sets the type of peak-fitting to be performed.
	APEX: Chooses the most intense point in the peak profile.
	LORENTZIAN: Does a lorentzian fit to the entire peak profile.
	QUADRATIC: Chooses three points - the apex, and one on either side of the profile, 
		and performs a quadratic fit.

- DeconvPep::MaxCharge (default: 10)
 Sets the maximum charge state of an isotopic cluster.

- DeconvPep::ThScore (default: 0.0)
 Sets the threshold score of an isotopic cluster to display.

- DeconvPep::OutputFormat (default: PEK)
 Sets the format of result files. 
	PEK: The format of ICR-2LS (<input file name>+.pek)
	CSV: The format of Decon2LS (<input file name>+_scans.csv and <input file name>+_isos.csv)

- DeconvPep::ResultOrder (default: ABUNDANCE)
 Sets the order of displayed results.
	ABUNDANCE: by decreasing order of the sum of abundances of the N most abundant peaks
		(where N is AdvDeconv::MaxAbundancePeak).
	SCORE: by decreasing order of the score of a cluster. 
	MASS: by decreasing order of the monoisotopic mass of a cluster.
	M/Z: by increasing order of the m/z of the most abundant peak of a cluster.

- DeconvPep::Target (default: MS)
 Sets the target scans
	ALL: all scans (MS + MS/MS)
	MS: only MS scans
	MS/MS: only MS/MS scans

- AdvDeconv::MaxAbundancePeak (default: 3)
 Sets the maximum number of peaks, a sum of abundances of which is displayed in result files.

- AdvDeconv::ScanNoModifier (default: 0)
 Sets the modifier to scan numbers in result files. Set -1 to get the same scan numbers as ICR-2LS.

- AdvDeconv::MaxMissPeak (default: 3)
 Sets the maximum number of peaks allowed to be missed in a pseudo cluster.

- AdvDeconv::MassErr (default: 1.0E-05)
 Sets the error bound on a mass difference between two adjacent peaks.
</pre>
## 3. Citation
<pre>
- Isotopic Peak Intensity Ratio based Algorithm for Fast and Accurate Determination of Isotopic Clusters 
  and Monoisotopic Masses of Polypeptides from High Resolution Mass Spectrometric Data
  Park, K.; Yoon, J. Y.; Lee, S.; Paek, E.; Park, H.; Jung, H.-J.; Lee, S.-W. 
  Anal. Chem. 2008, 80, 7294-7303.
</pre>
## 4. Rights and Permissions
<pre>
- RAPID by 2024 by is licensed under Creative Commons Attribution-ShareAlike 4.0 International, 
  which permits use, sharing, adaptation, distribution and reproduction in any medium or format, 
  as long as you give appropriate credit to the original author(s) and the source, 
  provide a link to the Creative Commons license, and indicate if changes were made.
  To view a copy of this license, visit https://creativecommons.org/licenses/by-sa/4.0/
</pre>

