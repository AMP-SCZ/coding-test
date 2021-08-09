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
* Human subjects sign a consent form to participate in a research study. Your task is to disguise the `date of consent` to protect their privacy. Modify the csv by replacing given dates to ones earlier than year 1925. You must use a random number of days (offset) for each subject so there is no way to trace back. For us to conveniently check your work, save the offset in a file `enroll_data_offset_{your_initials}.csv`.

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

* Modify the csv by replacing `birth date` column with `age` in years at the original date of consent and save it as `enroll_data_anon_{your_initials}.csv`.

*Upload*
* Push the csv back to dropbox using their API.


### Task 2
Write a web application in JavaScript, HTML, CSS with--
 * a time period filter for original `date of consent`
 * a drop down menu for groups--`cohort` and `age`
 * two visualizations, using the same graphics--
   * X axis is site, Y-axis is enrollment by cohort
   * X axis is site, Y-axis is enrollment by age group (in increment of 10 years)

You may use any JavaScript library you want.

  <details>
  <summary>Sample Output</summary>
  
  * The Y-Axis represents the total enrollment after `Group By` and `Time Period` controls are applied.
  * There are two cohorts--CHR and HC. Hence, in the following example, there are two legends. When displaying groups by age, add as many legends as the number of groups.
  * Numbers overlaid on the bar segments represent the percentage of the entire bar height covered by that segment.
  * *Hint*--for filling segments of a single bar, you can use SVG elements `defs` and `linearGradient`. But you can also plot multiple bars contiguously. If you do the latter and you have a hard time cacluating coordinates, just flip X and Y axes i.e. display the enrollment on X-axis and sites on Y-axis.
  * Time Period filter is over the original `date of consent`. This task is different from anonymization so we ask that you to use the originals.
  * Sample shows fictitious numbers and site names, do not let them confuse you


  ![image](https://user-images.githubusercontent.com/35086881/112389870-cc5f9d00-8ccb-11eb-8c34-df2bd8770d1d.png)
  
  </details>

### Task 3
* Make a GitHub repo and push up all your work
* Write a skeletal README.md as you would write for any GitHub repo so a remote user is able to get a sense of your project. You can also write any limitation you faced or new thing you learnt while doing this project.
* Launch a public webpage from GitHub so *Task 2* could be seen from the internet


### Notes
* Good coding practice (comment, space etc.) is recommended but not required.
* You are expected to navigate through this project on our own. But do reach out to us via the comment box below if anything is unclear or if you are stuck with any part of the project.
