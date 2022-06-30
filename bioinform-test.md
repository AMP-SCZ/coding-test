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
