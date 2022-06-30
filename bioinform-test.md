The coding test consists of one arithmatic task and one neuroimaging task. 
Both will appear at work at our laboratory. As you work on the problems, please create a GitHub repository with all your codes 
and write a skeletal `README.md` describing your workflow. No need to go overboard with writing README.md. 
We want to see if you know about this standard software archiving process.

---

### Task 1

*Download*
* We have shared a Dropbox folder with you. You will be required to upload your results there. To be able to do that, you need a dropbox account. Create one if you do not have it already.
* Write Python code to pull the csv from dropbox using their [API](https://github.com/dropbox/dropbox-sdk-python).

  <details>
  <summary>Hint</summary>
  
    * `upload()` and `download()` examples at https://github.com/dropbox/dropbox-sdk-python/blob/main/example/updown.py
    
    * Remember to include `/` to access a folder via the API i.e. `/recruitment_project`
  </details>
  
*Anonymize*
* Human subjects sign a consent form to participate in a research study. Your task is to disguise the `date of consent` to protect their privacy. First, modify the csv by replacing given dates with ones earlier than year 1925. You must use a random number of days (offset) for each subject so there is no way to trace back. Second, replace the `birth date` column with `age` in years at the original date of consent. Save the modified csv as `enroll_data_anon_{your_initials}.csv`. 

  <details>
  <summary>Hint</summary>
  
    `enroll_data_anon_{your_initials}.csv` should look like:
    
    |	| site ID | date of consent | cohort | age |
    |-|-|-|-|-|
    | 1	| BWH | 8/13/1924 | CHR | 45 |
    | .	| ... | ... | ... | ... |
    
      
  </details>

* For us to conveniently check your work, save the offset in a file `enroll_data_offset_{your_initials}.csv`.

  <details>
  <summary>Hint</summary>
  
    `enroll_data_offset_{your_initials}.csv` should look like:
    
    |	| days_offset |
    |-|-|
    | 1	| 35041 |
    | 2	| 35049 |
    | 3	| 35055 |
    | .	| ... |
      
  </details>

*Upload*
* Push the two csvs back to Dropbox using their API.


---

### Task 2

Oftentimes, we have to compute volumes of different brain regions--cerebellum, thalamus, ventricle etc.
For this purpose, we superimpose a given T1w image upon an standard image whose region boundaries are known.
The latter image is called an atlas. It consists of integer labels defined by the numbers under `#No.`
column in [this](https://surfer.nmr.mgh.harvard.edu/fswiki/FsTutorial/AnatomicalROI/FreeSurferColorLUT) look up table.
After superimposition, counts of the labels give volumes of respective brain regions. The superimposition is achieved
via popular brain image registration tools e.g. [ANTs](https://surfer.nmr.mgh.harvard.edu/fswiki/FsTutorial/AnatomicalROI/FreeSurferColorLUT).
In this task, we ask you to do just the above.


*Prerequisite*

* Python 3
* Libraries: pandas, nibabel
* ANTs: you may install our conda package from `pnlbwh` channel
  We are testing that you know how to install a package from a conda channel


*Input*

  The shared Dropbox folder contains three images:

* given T1w image
* an atlas with integer labels (`atlas-integer-labels.nii.gz`)
* a T1w image in the space of atlas (`atlas-T1w.nii.gz`)
* you should download the [FreeSurfer](https://surfer.nmr.mgh.harvard.edu/fswiki/FsTutorial/AnatomicalROI/FreeSurferColorLUT) look up table by your known method
  


*Workflow*
    
1. Register the given T1 image to the space of `atlas-T1w.nii.gz`. You can do it directly in your terminal.
   
   <details><summary>Hint</summary>
  
   After installing the ANTs package, you may do `antsRegistration --help` to learn about the sequence of
   arguments to pass to `antsRegistration`.
  
   </details>

2. Now your registered image is in the space of the atlas and is ready to superimpose on the atlas.
   Binarize your atlas for each integer label present in it. Multiply the registered image with the binary image.
   Count the number of 1's in the resultant image. This count gives you the volume of that brain region.

3. Do string processing of the look up table to extract the first and second columns. Thus, you obtain the names of brain regions
   corresponding to integer labels.

4. Save your results in a CSV file with three columns:
    
    | label | name | volume |
    | - | - | - |
    | 16 | Brain-Stem | 123
    | 24 | CSF | 4567 |
    | .. | .. | .. |

5. Upload the CSV file to the Dropbox folder used in task 1. Feel free to drag and drop this time.




---

Please open GitHub issues under this repository should you have any questions. We shall respond to you through that. Our GitHub handles are `tashrifibllah` and `yrathi`.
