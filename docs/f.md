# Exercise 5
We need to check the configuration and location of our page file. Microsoft has done a great job of hiding it. Worse, they move around menus with every release. 

1. Go to Control Panel -> System and Security -> System
2. Click on Advanced System Settings
3. Now click on Advanced System Settings
4. Go to Performance and click on Settings
5. Now click on Advanced
6. Look at the Virtual memory tab, click on Change.
7. How much virtual memory do you have?
8. Why is it set to that value? 

By default, Windows will automatically create the paging file on the operating system drive, normally C: 

Don't do it, but if you un-tick Automatically manage Paging File Size for all Drives then you can manually set paging files up on drives other than the C: 

Note that if you do not keep any paging files on the C: drive, the system will give you some messages implying that it is hurt and feeling rather insecure with itself! There are reasons why we do move the page file to other drives; mostly this would be on servers for performance reasons. To get out of this without making any changes, press cancel and close all the dialog boxes.

