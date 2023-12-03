<h1>SEIM: Splunk Basics</h1>

<h2>Description</h2>
This project will showcase how to use Splunk Cloud to perform a search and an investigation of the data.

To operate effectively, SIEM tools must ingest and index data. SIEM tools collect and process data to become searchable events that can be queried, viewed, and analyzed.
<br/>
<h2>Environments Used </h2>

- <b>Splunk Cloud</b>
- <b>Mac OS</b>

<h2>Program walk-through:</h2>
<p>
So far, you've created a Splunk account and activated and accessed the Splunk Cloud free trial, but your Splunk Cloud instance does not contain any data. Next, you'll need to upload data into Splunk to start querying. Complete the following steps to upload data into Splunk:
</p>
<p>
You will need some data to upload to begin evaluating it on Splunk. Here are the steps to upload the data:
</p>
<ol>
  <li>On the Splunk bar, click Settings. Then click the Add Data icon.</li>
  <li>Click Upload.</li>
  <li>Click the Select File button.</li>
  <li>Upload the tutorialdata.zip file, and click Open.</li>
  <li>Click the Next button to continue to Input Settings.</li>
  <li>By the Host section, select Segment in path and enter 1 as the segment number.</li>
  <li>Click the Review button and review the details of the upload before you submit.</li>
</ol>
The details should be as follows:</p> 
<ul>
  <li>Input Type: Uploaded File</li>
  <li>File Name: tutorialdata.zip</li>
  <li>Source Type: Automatic</li>
  <li>Host: Source path segment number: 1</li>
  <li>Index: Default</li>
</ul>
Click Submit. Once Splunk has ingested the data, you will receive confirmation that the file was successfully uploaded.
<br/>
<br>
<p align="center">Splunk Menu</p>
<img src="https://imgur.com/gvYfeg4.png" align="center" height="80%" width="80%" alt="Splunk Menu"/>
<br/>
<p>
Now that you've uploaded the data into Splunk, perform your first query to confirm that the data has been ingested, indexed, and is searchable. Follow these steps to perform a query:
<ol>
<li>Navigate to Splunk Home. (To return to Splunk Home, click the Splunk Cloud logo on the Splunk Cloud page.)</li>
<li>lick Search & Reporting. You may close any pop-ups that appear.</li>
<li>In the search bar,  enter your search query: index=main This search term specifies the index. An index is a repository for data. Here, the index is a single dataset containing events from an index named main.</li>
<li>Select All Time from the time range dropdown to search for all the events across all time.</li>
<li>Click the search button. Note that the search button is represented by the magnifying glass icon. Your search should retrieve thousands of events.</li>
</ol>
</p>
<br>
<p align="center">Splunk Basic Search</p>
<img src="https://imgur.com/Bqb4T09.png" align="center" height="80%" width="80%" alt="Splunk Basic Search"/>
<p>Pro tip: It's a best practice to use short time ranges in your searches because a shorter time range returns results faster and uses fewer resources. Adjust the time using the time range dropdown or by using time modifiers in your search.</p>
<br/>
<h2 align="center">Evaluate the fields</h2>
<p>When Splunk indexes data, it attaches fields to each event. These fields become part of the searchable index event data. This helps security analysts easily search for and find the specific data they need. Now that you've run your first query, examine the search results and the fields.
For each event, the fields are host, source, and sourcetype. Under SELECTED FIELDS, examine the same fields.</p>
<br>
<p align="center">Splunk Evaluation</p>
<img src="https://imgur.com/PCSQ3CQ.png" align="center" height="80%" width="80%" alt="Splunk Evaluation"/>
<br/>

<p>Examine the field values by clicking on the field under SELECTED FIELDS. You should observe the following:
<ul>
<li>host: The host field specifies the name of the network host from which the event originated. In this search, there are five hosts:
<li>mailsv - Buttercup Games' mail server. Examine events generated from this host.
<li>www1 - This is one of Buttercup Games' web applications.</li>
<li>www2 - This is one of Buttercup Games' web applications.</li>
<li>www3 - This is one of Buttercup Games' web applications.</li>
<li>vendor_sales - Information about Buttercup Games' retail sales.</li>
<li>source: The source field indicates the file name from which the event originates. You should identify eight sources. Notice /mailsv/secure.log, which is a log file that contains information related to authentication and authorization attempts on the mail server.</li>
<li>sourcetype: The sourcetype determines how data is formatted. You should observe three sourcetypes. Examine secure-2.</li>
</ul>
</p>
<br>
<h2 align="center">Narrow your search</h2>
<br>
<p>Because you've been tasked with exploring any failed SSH logins for the root account on the mail server, you'll need to narrow the search results for events from the mail server.
</p>
<p>
Under SELECTED FIELDS, click host and click mailsv.
Notice that a new term has been added to the search bar: index=main host=mailsv. The search results have narrowed to over 9000 events that are generated by the mail server.</p>

<br>
<h2 align="center">Search for a failed login for root</h2>
<br>
<p>Now that you've narrowed your search results to events generated by the mail server, continue to narrow the search to locate any failed SSH logins for the root account.</p>
<ol>
  <li>Clear the search bar.</li>
  <li>Enter index=main host=mailsv fail* root into the search bar. This search expands on the search from the previous task and searches for the keyword fail*. The wildcard tells Splunk to expand the search term to find other terms that contain the word fail such as failure, failed, etc. Lastly, the keyword root searches for any event that contains the term root.</li>
  <li>Click search.</li>
</ol>
<br>
<h2 align="center">Evaluate the search results</h2>
<br>
<p>Your search from the previous task should have retrieved search results for over 300 events. Navigate to other pages of the search results to observe the events not listed on the first page of the results.
</p>

<p>
Pro tip: Splunk highlights search terms in search results to make it easier to identify where the search terms appear in the data.
</p>
<br>
<ol>
<li>How many events are contained in the main index across all time? <b>109,864</b></li>
<li>Which identifies the name of a network device or system from which an event originates? <b>Host</b></li>
<li>Which of the following hosts used by Buttercup Games contains log information relevant to financial transactions? <b>vendor_sales</b></li>
<li>How many failed SSH logins are there for the root account on the mail server? <b>346</b></li>
</ol>
<br>
<h2 align="center">Key takeaways</h2>
<br>
<p>In this activity, you used Splunk Cloud to perform a search and investigation. Using Splunk Cloud, you were able to:
</p>
<ul>
<li>Upload sample log data</li>
<li>Search through indexed data</li>
<li>Evaluate search results</li>
<li>Identify different data sources </li>
<li>Locate failed SSH login(s) for the root account</li>
</ul>
</p>
<p>Thank you for going through this tutorial with me. Now it is your turn to upload data to Splunk and make your investigations.</p>

