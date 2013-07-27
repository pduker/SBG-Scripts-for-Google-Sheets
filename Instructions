The basic set up to use these scripts to create a SBG Gradebook is to do the following:

1) Create a new spreadsheet called "Master Spreadsheet" (or sth like that) for the class, column A will be the list of student names, column B will be the list of e-mail addresses (corresponding to the row so line 1 will give a student name in A and his or her e-mail in B).

2) Go to Tools > Script editor, and then paste in the code in the "Generate-Student-Gradebooks" file.  Then switch tabs back to the Master spreadsheet.

3) Copy the Master Spreadsheet Id (this is a pretty long string ... 
such as: 0Agwc91nl2SoVdGJVTFlCQkhHdkxIWkVnZUkyT08xTkE). It can be found in the URL in between 
the "spreadsheet/ccc?key=" and the "#gid=0" right at the end.

4) Create a new spreadsheet (call it Student Gradebook Template) and paste in the master spreadsheet ID into A1.  Then hide the whole first row (select row, left click, Hide row).

5) In the Student Gradebook Template spreadsheet, go to Tools > Script editor and then paste in the "Student-Template-Script" code.  

Optional 
Since the Master Spreadsheet Id stays consistent, you could actually paste it into the Student Template script in line 12 of the code.  In that case don't fill in A1 and instead alter the Student-Template-Script as follows: 
Instead of line 12 being: 
var masterid = displayPage.getRange(1,1).getValue(); 
you would have: 
var masterid = "0Agwc91nl2SoVdDVHcFFMSndpVVRRMXpBWFNuV1NsRnc"; 
with your master spreadsheet Id between the quotes above.
WARNING - haven't tried this option yet, and not sure why we didn't do it in the first place, but I think it should work.


6) (Now that your Student template file is ready, you have to point the Master script to it) Close the script editor and go back to the Student Gradebook Template spreadsheet.  Once there, copy the Student Gradebook Template Id (a similarly long string) as you did in step 3.

7) Go back to the "Master Spreadsheet," go to Tools > Script editor (or just find the tab if you didn't close it).  And on line 22, paste the Student Gradebook Template ID so that it reads something like:
  var templateid = "0Agwc91nl2SoVdDVHcFFMSndpVVRRMXpBWFNuV1NsRnc";

8) Great - your Master script is set, your template is set with a script in it ready to run.  So go ahead and run your Generate-Student-Gradebooks script (Tools > Script manager... then click on the Run tab).

9) You should start seeing student files show up in the main folder of your Google drive.  You'll likely want to organize them all into a separate folder for the class.

10) Here comes the tedious part. Unfortunately you can't automate a trigger for the generated file (at least I haven't been able to figure out how to do this), so you have to do the following for each of your student files:

 a) open the file
 b) Tools > Script Editor
 c) Click on the "triggers" icon (looks like a clock)
 d) Click on the blue text that says: "No triggers set up. Click here to add one now"
 e) The default option is on opening the file, which is what you want, so just click Save.
 
As you get going, this doesn't take as much time as you think, but I'd love it if someone found a way to automate this part.

After this you should be all set.  When the student or you opens the file, the script should run and pull the data from the master gradebook. After a few seconds, the file "magically" updates with the current info from the Master.



  
