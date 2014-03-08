<h3> Setting up the Gradebook </h3>

Please follow these instructions to set up a SBG Gradebook in Google Docs:

1. Make sure you are logged into a google account that you want to use for keeping your student data
2. Go the file titled: "B links to templates.md" on Github, there you will find two links.  Please click on both links (they will take you to pre-made spreadsheet files).
3. In each of the spreadsheet files, click on File > Make a Copy.  This should create copies of each of these spreadsheets in your Google Drive account.
4. After you've made copies of the spreadsheets, go ahead and close those windows/tabs.
5. Then switch over to your Google Drive and open your newly created files (feel free to rename the Master Spreadsheet and Student template according to the class you will teach: Aural skills II Master, Written Theory I Master, etc.).
6. In the "Master Spreadsheet," highlight and copy the Url 
7. Open the "Student Template" spreadsheet.
8. Go to Tools > Script Editor
9. In line 29 of the code, paste the Master Spreadsheet Url that you copied in step 6.  Line 29 should then look something like this (be sure to paste between the quotes):
<p>
var workbook = SpreadsheetApp.openByUrl("https://docs.google.com/a/udel.edu/spreadsheet/ccc?key=0Agwc91nl2SoVdGl1VmVGazNUM0NpOVZMbG1KVHdUMnc&usp=drive_web#gid=0");
</p>

10. Save the file (click on the disk icon, or File > save), and then close the script editor window.
11. Great, now your template knows where to pull data from when it updates. Now you need to copy the Student Template Url (just as you did in step 6: copy the whole Url field)
12. Now switch back to the "Master Spreadsheet" window
13. Go to Tools > Script Editor
14. On line 23 of the code, paste the Student Template Url so it looks something like this:
<p>
  var template = SpreadsheetApp.openByUrl("https://docs.google.com/a/udel.edu/spreadsheet/ccc?key=0Agwc91nl2SoVdDZZeHl1T1NvcFVjVVNqMTRaZXpFY3c&usp=drive_web#gid=0");
</p>
15. You will likely also want to change what the title of each student gradebook will be.  the default is "Outcomes Gradebook for [student name]."  To change this, go to line 11 of the code and fill in what you want to appear between the quotes.  E.g. for "Harmony I" you might have:
<p>
  var titleStem = "Harmony I Gradebook for ";
</p>
16. Now save your script, and close that window.
17. Great - you've done all of the hard part involving the script code.  Now you want to set up your gradebook.  To do this paste the names and e-mail addresses of each of your students in the appropriate columns of the Master Spreadsheet (i.e. columns A and B).
18. After you've put in all of the names, you are ready to run the Create Student Sheets Script.  I recommend that you run this script in the evening when Google's servers aren't so busy (I've had this take a while in the middle of the day). Do this by going to Tools > Script Manager, and then clicking on the "Run" button.  Note that the first time you click "Run" you will have to click "OK" on two permissions dialog boxes. After you've given permission to the script to run, you then have to click on "Run" again.

19. You should start seeing student files show up in the main folder of your Google drive.  (and you'll likely want to organize them all into a separate folder for the class.  A quick way to do this is search for the title stem of your student's gradebook (e.g. Harmony I Gradebook was the example above), and then select all, so you can move the files to a separate folder).
20. Depending on the time of day you run your script this process may be fast or slow - I've found it is much faster in the evening when Google's servers aren't getting as much traffic.
21. When the student template script (Pull Data) runs, it needs to know how many categories you are using.  The script is written so that it pulls a number from the last row of your Master Spreadsheet, which needs to be the number of categories you want displayed for the students.  An easy approach to this is to type in the following formula on the last row of the column A in the Master spreadsheet:   <p>
=(Counta(1:1)) - 2 </p>  (Basically this counts how many columns have data and subtracts two for the name and e-mail address columns) 
22. Here comes the tedious part. Unfortunately you can't automatically create triggers for scripts that access other files of yours (this is an understandable security feature that Google has in place).  In the student Template file, there is a trigger setting script that you will need run for each student file.  So you have to do the following for each of your student files:
 <br> </br>
 <br>a) open the file </br>
 <br>b) Tools > Script Manager </br>
 <br>c) It should automatically default to highlight the "opentrigger" script, if not click on that script</br>
 <br>d) Click on the "Run" button
 <br>e) You will need to click OK to give the script authorization to run</br>
 <br>f) You will also have to approve that the script will access some of your other spreadsheets</br>
23. TADA and Congratulations! After this you should be all set in terms of the student files updating automatically. Now all you have to do is make sure that you keep the Master Spreadsheet in order, and things will be fine.



<h3> Entering in new grades </h3>
In the Master gradebook, each column is for a separate category/standard and each row is for a student. You'll want to think a little bit about how to organize your columns, so that similar categories are adjacent, etc.  Once you've got some of your categories organized the way you want them, duplicate your "Average" tab and re-title it "End of Records."  You only need to do this once. Once you have all that sorted out, here's how you enter grades in:

1) first check to see if the standards/categories are already a column header in the "Average" tab, if not create a new column for that standard.

2) Duplicate the "End of Records" tab, and then retitle it to the new assignment name that you are entering grades for (e.g. project 1, HW 3, Exam 2, etc.).

2) Paste the top row of the "Average" tab onto the newly created new assignment tab (to make sure that all of your categories are up to date).

3) Enter in the grades in the new assignment tab (I like to hide the columns that are not relevant to this assignment, so it's easier to see what the actual scores are, but this isn't necessary).  

4) Go to the Master spreadsheet and set up an function that looks at the same cell on each tab and averages them together.  Something like: <p>
=Average(Quiz02!D2,Quiz03!D2,Quiz04!D2,Quiz05!D2,Quiz06!D2,Quiz07!D2,Quiz08!D2) </p>
Note that you actually don't need to pull the cells from each tab; you only need to average the tabs that have a grade in that category.... Once you've done this for the first cell, you can just use the auto fill function in google spreadsheet to quickly average all of the tabs.

5) Do a quick spot check that your function references are good and that the averages are being computed accurately.  

The "Average" tab should list each student's average grade for each category, and the assignment tabs show you each students' scores for that assignment.  You can open up each student's individual grade sheet if you want to look at how they are doing more holistically. When the student or you opens the student gradebook file, the script should run and pull the data from the master gradebook. After a few seconds, the file "magically" updates with the current info from the Master.

To see an example of the Master spreadsheet (with all of the averages and grade computing) please see: <p>
<a href="http://www.udel.edu/001859" target="_blank">SBG Master Spreadsheet Example</a>
</p>



<h3> Creating the SBG set up without copying the templates </h3>

Here is the more complex approach to creating the SBG gradebook set up without copying the templates.

1a) Create a new spreadsheet called "Master Spreadsheet" (or something like that) for the class you are hoping to use SBG: column A will be the list of student names, column B will be the list of e-mail addresses (corresponding to the row so line 1 will give a student name in A and his or her e-mail in B).  At the bottom of the spreadsheet, click on the triangle next to the tab title (it says "Sheet1" by default) and rename it "Average."  **Important** If the name of the first tab is not "Average" the student scripts will not run properly.

2) Copy the Master Spreadsheet Url

3) Create a new spreadsheet (call it "Student Gradebook Template" or something like that) 

4) In the "Student Gradebook Template" spreadsheet, go to Tools > Script editor and then paste in the "Student-Template-Script" code from this Repository.  At this point you'll want to change line 12 of the code by pasting in your Master Spreadsheet Id.  Line 12 should then look something like this:
<p>
  var workbook = SpreadsheetApp.openByUrl("https://docs.google.com/a/udel.edu/spreadsheet/ccc?key=0Agwc91nl2SoVdGl1VmVGazNUM0NpOVZMbG1KVHdUMnc&usp=drive_web#gid=0");
</p>

5) Great - you can save and close the script editor.  At this point you may want to consider adding some highlighting or column/row shading to help your students with legibility, but your Student template file is ready.

6) Go back to the "Master Spreadsheet," go to Tools > Script editor.  Paste in the Generate Student Gradebook script (from this Github repository - it's listed as C).  
 
7) Now go back to to the Student Template spreadsheet and copy the Student Template Url as you did in step 2.

8)Now go to your Master Spreadsheet script editor, and past in the Student Gradebook Template Url in line 23.  It should read something like this (except with your Template url):<p>
 var template = SpreadsheetApp.openByUrl("https://docs.google.com/a/udel.edu/spreadsheet/ccc?key=0Agwc91nl2SoVdDZZeHl1T1NvcFVjVVNqMTRaZXpFY3c&usp=drive_web#gid=0");

  </p>

9) Great - your Master script is set and your template is set with a script in it ready to run.  I recommend that you run this script in the evening when Google's servers aren't so busy (I've had this take a while in the middle of the day). So go ahead and run your Generate-Student-Gradebooks script (Tools > Script manager... then click on the Run tab).  

10) You should start seeing student files show up in the main folder of your Google drive. 

11) Here comes the tedious part. Unfortunately triggers don't copy when a file is duplicated, so you have to do the following for each of your student files:
 <br> </br>
 <br>a) open the file </br>
 <br>b) Tools > Script Editor </br>
 <br>c) Click on the "triggers" icon (looks like a clock)</br>
 <br>d) Click on the blue text that says: "No triggers set up. Click here to add one now"</br>
 <br>e) The default option is on opening the file, which is what you want, so just click Save.</br>
 
As you get going, this doesn't take as much time as you think (depending on your class size), but I'd love it if someone found a way to automate this part.

12) Lastly, after you've created all of the student sheets.  Go to the last row of your Master Spreadsheet and below the row with last student's name, paste the following code into column A: <p>
=(Counta(1:1)) - 2 </p>
This will count how many categories that you have (subtracting 2 for the student name and e-mail address columns). 

After this you should be all set in terms of the student files updating automatically. Now all you have to do is make sure that you keep the Master Spreadsheet in order, and things will be fine (see instructions above for Entering in new grades).





  
