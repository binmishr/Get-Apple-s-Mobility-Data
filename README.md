# Get-Apple-s-Mobility-Data

The details of the codeset and plots are included in the attached Adobe Acrobat reader (.pdf) file in this repository. 
You need to download the same to view the contents. There are referrals to other contents in BLUE colour also to follow.

covdata, an R package with a variety of COVID-related datasets in it. That means I’ve been pulling down updated files from various sources every couple of days. Most of these files are at static locations. While their internal structure may change occasionally, and maybe they’ve moved once or twice at most since I started looking at them, they’re generally at a stable location. Apple’s Mobility Data is an exception. The URL for the CSV file changes daily, and not just by incrementing the date or something like that. Instead the file path is a function of whatever version the web CMS is on, and its versioning moves around. Worse, the webpage is dynamically generated in Javascript when it’s requested, which means we can’t easily scrape it and just look for the URL embedded in the “Download the Data” button.

I update manually for a bit, and then I got stuck in the weeds of using a headless browser from within R that could execute the Javascript and thus find the URL. But this was a huge pain. There’s an index.json file that’s stably-located and contains the information I needed to generate the URL of the day. Here’s how to do just that, and then pull in the data to a tibble.

Apple's Mobility Data Documentation : https://covid19.apple.com/mobility
