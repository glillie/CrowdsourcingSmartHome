# Amazon Mechanical Turk HIT Information

There are three types of files stored in this folder:
* HIT html files - the source html for the MTurk requester project
* Scenario and Qualification HTML files - the pages requested by iframes in source html
* Input csv file - contains URL links to Scenario and Qualification HTML.

In order to get the qualification and scenario HITs up and running you will need to do several things. First you need to host the 
following files on a domain that has a valid SSL certification:

qualification.html
scenario1.html
scenario2.html
scenario3.html
scenario4.html
scenario5.html

It is important that these files are hosted on a domain that has a valid SSL, otherwise mechanical turk will prevent the pages from 
being shown to the workers (they will only see a blank page). Next you need to update the supplied input.csv file so that it contains
the correct URLs of the scenario pages. This allows us to use one MTurk project to release all five of our different scenarios at one
time (and makes handling the results a lot easier).

## Creating the Qualification
TODO

## Creating the Qualification HIT
TODO

## Creating the Scenario HITs
Once this is done you will need to create a new Project on the Mechanical Turk requester site. This will be used to put out the 
scenario HITs. I used the following properties to create mine:

Project Name: Smart Home Automation - All Scenarios
Title:Help Write the Logic for a Smart Home Scenario
Description: We want you to play the role of a homeowner who wants to program interactions between devices in his or her home. Complete the logic for the given scenario using the supplied keywords. Bonuses given to workers that complete 5 HITs.
Keywords: smart home, automation, logic
Reward per Assignment: 0.25$
Number of Assignments per HIT: 100
Time allotted per assignment: 10 Minutes
HIT Expires in: 7 days
Auto approve and pay workers in: 2 days
Require that workers be Masters to do your HIT:? No
Specify additional qualifications Workers must meet: Smart Home Automation Scenario Qualification has been granted
Only workers who qualify to do my HITs can preview my HITs: No

Once the project is created navigate to the Design Layout tab and set the Frame Height to 1750. Click the source button and then copy
over the html from the hit.html file above into the source textarea box. Save this.

Next you will need to update the source code you just pasted in so that the eventer function is looking for messages coming from 
your domain. To do this hit the source button and find the eventer javascript function near the top of the file. Since my HTML 
pages were hosted on my domain, the scenario HIT was expecting messages to be posted from https://www.gisellelillie.com. 
   
   Code Example:
   <code>// Make sure message is coming from the iframe
    if ( event.origin !== "https://www.gisellelillie.com" ) {
      return;
    }
    </code>
    
You will need to replace https://www.gisellelillie.com with your domain. Save the project updates.

## Getting the automatic text coloring to work
TODO

At this point you should be able to successfully release the HITs, although I suggest trying everything out in the sandbox first.
