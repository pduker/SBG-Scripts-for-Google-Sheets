<h3> Setting up the Gradebook </h3>

Please follow these instructions to set up a SBG Gradebook in Google Docs:

1a) Create a new spreadsheet called "Master Spreadsheet" (or sth like that) for the class you are hoping to use SBG: column A will be the list of student names, column B will be the list of e-mail addresses (corresponding to the row so line 1 will give a student name in A and his or her e-mail in B).  At the bottom of the spreadsheet, click on the triangle next to the tab title (it says "Sheet1" by default) and rename it "Average."  **Important** If the name of the first tab is not "Average" the student scripts will not run properly.

2) Go to Tools > Script editor, and then paste in the code from the "Generate-Student-Gradebooks" file on this Repository.  Then switch tabs back to the Master spreadsheet.

3) Copy the Master Spreadsheet Id (this is a pretty long string ... 
such as: 0Agwc91nl2SoVdGJVTFlCOkhHdkxIWkVnZUkyT08xTkE). It can be found in the URL in between 
the "spreadsheet/ccc?key=" and the "#gid=0" right at the end.

4) Create a new spreadsheet (call it Student Gradebook Template) and paste in the master spreadsheet ID into A1.  Then hide the whole first row (select row, left click, Hide row).

5) In the Student Gradebook Template spreadsheet, go to Tools > Script editor and then paste in the "Student-Template-Script" code from this Repository.  

_Optional_: 
Since the Master Spreadsheet Id stays consistent, you could actually paste it into the Student Template script in line 12 of the code.  In that case don't fill in A1 and instead alter the Student-Template-Script as follows: 
Instead of line 12 being: 
var masterid = displayPage.getRange(1,1).getValue(); 
you would have: 
var masterid = "0Agwc91nl2SoVdDVHcGFMSndpVVRRMXpBWFNuV1NsRnc"; 
with your master spreadsheet Id between the quotes above.
_WARNING_ - haven't tried this option yet, and not sure why we didn't do it in the first place, but I think it should work.


6) Now that your Student template file is ready, you have to point the Master script to it. Close the script editor and go back to the Student Gradebook Template spreadsheet.  Once there, copy the Student Gradebook Template Id (a similarly long string) as you did in step 3.

7) Go back to the "Master Spreadsheet," go to Tools > Script editor (or just find the tab if you didn't close it).  And on line 22, paste the Student Gradebook Template ID so that it reads something like:
  var templateid = "0Agwc91nl2SoVdDWHcFFMSndpVVRRMXpBWFNuV1NsRnc";

8) Great - your Master script is set and your template is set with a script in it ready to run.  So go ahead and run your Generate-Student-Gradebooks script (Tools > Script manager... then click on the Run tab).

9) You should start seeing student files show up in the main folder of your Google drive.  You'll likely want to organize them all into a separate folder for the class.

10) Here comes the tedious part. Unfortunately triggers don't copy when a file is duplicated, and the command to set a trigger for the file doesn't seem to work (at least I haven't been able to figure out how to do this), so you have to do the following for each of your student files:
 <br> </br>
 <br>a) open the file </br>
 <br>b) Tools > Script Editor </br>
 <br>c) Click on the "triggers" icon (looks like a clock)</br>
 <br>d) Click on the blue text that says: "No triggers set up. Click here to add one now"</br>
 <br>e) The default option is on opening the file, which is what you want, so just click Save.</br>
 
As you get going, this doesn't take as much time as you think (depending on your class size), but I'd love it if someone found a way to automate this part.

11) Lastly, after you've created all of the student sheets.  Go to the last row of your Master Spreadsheet and below the row with last student's name, paste the following code into column A: <p>
=(Counta(1:1)) - 2 </p>
This will count how many categories that you have (subtracting 2 for the student name and e-mail address columns). 

After this you should be all set in terms of the student files updating automatically. Now all you have to do is make sure that you keep the Master Spreadsheet in order, and things will be fine.


<h3> Entering in new grades </h3>
In the Master gradebook set up, each column is for a separate category/standard and each row is for a student. You'll want to think a little bit about how to organize your columns, so that similar categories are adjacent, etc. Also consider color coding the "Master" by highlighting every 2nd or 3rd row and column to make it easier to read.  Once you've got it looking nice, duplicate your "Average" tab and re-title it "End of Records."  You only need to do this once. Once you have all that sorted out, here's how you enter grades in:

1) first check to see if the standards/categories are already a column header in the "Average" tab, if not create a new column for that standard.

2) Duplicate the "End of Records" tab, and then retitle it to the new assignment name that you are entering grades for (e.g. project 1, HW 3, Exam 2, etc.).

2) Paste the top row of the "Average" tab onto the newly created new assignment tab (to make sure that all of your categories are up to date).

3) Enter in the grades in the new assignment tab (I like to hide the columns that are not relevant to this assignment, so it's easier to see what the actual scores are, but this isn't necessary).  

4) Go to the Master spreadsheet and set up an function that looks at the same cell on each tab and averages them together.  Something like: 
=Average(Quiz02!D2,Quiz03!D2,Quiz04!D2,Quiz05!D2,Quiz06!D2,Quiz07!D2,Quiz08!D2)
Note that you actually don't need to pull the cells from each tab; you only need to average the tabs that have a grade in that category.... Once you've done this for the first cell, you can just use the auto fill function in google spreadsheet to quickly average all of the tabs.

5) Do a quick spot check that your function references are good and that the averages are being computed accurately.  

The "Average" tab should list each student's average grade for each category, and the assignment tabs show you each students' scores for that assignment.  You can open up each student's individual grade sheet if you want to look at how they are doing more wholistically. When the student or you opens the student gradebook file, the script should run and pull the data from the master gradebook. After a few seconds, the file "magically" updates with the current info from the Master.



  
