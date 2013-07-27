SBG-Scripts-for-GDocs
=====================

Two scripts to help with the set up of Standards Based Grading in Google Docs

The basic set up to use this to create a SBG Gradebook is to do the following: 

1) Create a Master Spreadsheet for the class, column A will be the list of student names, column B will be the list of e-mail addresses (corresponding to the row so line 1 will give a student name and his or her e-mail).

2) copy the master spreadsheet Id (this is a pretty long string ...
such as: 0Agwc91nl2SoVdGJVTFlCQkhHdkxIWkVnZUkyT08xTkE).  It can be found in the URL in between 
the "spreadsheet/ccc?key=" and the "#gid=0" right at the end.

3)  open up a blank file (call it Student Gradebook template) and paste in the master spreadsheet ID into A1.  

*Optional*
(Since this stays consistent, you could actually paste it into the Student Template script in line 12.  Instead of:
var masterid = displayPage.getRange(1,1).getValue();
you would have:
var masterid = "0Agwc91nl2SoVdDVHcFFMSndpVVRRMXpBWFNuV1NsRnc";
with your master spreadsheet Id between the quotes.


in A1 (

3) the "Student-Template-Script" code by going to Tools > Script editor
