## Input
A csv file `enroll_data.csv` in a dropbox folder named `recruitment_project` with columns:
> site ID, date of consent, cohort, birth date


### Task 1
*Download*
* We have shared the above folder with you. You will be required to upload your results there. To be able to do that, you need a dropbox account. Create one if you do not have it already.
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
* Push the two csvs back to dropbox using their API.


### Task 2

Oftentimes, we have to compute volumes of different brain regions--cerebellum, thalamus, ventricle etc.
For this purpose, we superimpose a given T1w image upon a standard T1w image whose region boundaries are known.
The latter image is called an atlas. It consists of integer labels defined by the numbers under `#No.`
column in [this](https://surfer.nmr.mgh.harvard.edu/fswiki/FsTutorial/AnatomicalROI/FreeSurferColorLUT) look up table.
After superimposition, counts of the labels give volumes of respective brain regions. The superimposition is achieved
via popular brain image registration tools e.g. [ANTs](https://surfer.nmr.mgh.harvard.edu/fswiki/FsTutorial/AnatomicalROI/FreeSurferColorLUT).
In this task, we ask you to do just the above.


Prerequisite 



Input to your program:
    given T1 image,
    atlas,
    standard T1 image
  

Install Python >= 3.6
    nibabel, pandas, ANTs (hint for downloading)
Load IIT structural atlas (hint for downloading)
FreeSurfer look up table (hint for downloading)
    some string processing
    
Register given T1 image to the space of IIT atlas
    must do it through subprocess call from Python

Count the volume of each region
    Hint:
        The registered image contains only integer lables
        Binarize the registered image by each integer
        Volume is the sum of ones in the above
        
Save the volumes in a CSV file:
    
        region name,volume

Upload the result to dropbox
Download the images from dropbox
Write a GitHub repository with all your codes, and a skeletal README
