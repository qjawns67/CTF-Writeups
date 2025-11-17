## Username
natas3

## Password
3gqisGdR0pjm6tpkDKdIWO2hSvchLeYH

## Write-Up
There is nothing on this page.  
I found out "No more information leaks!! Not even Google will find it this time..." comment in HTML source code.  
We should know that how "Web Crawler" for search engine like Google works.  
Web Crawler is bot that search for Internet automatically to index website information.  
Web Service provide a guide, robots.txt that tells which pages it can index and which pages it shouldn't index to Web Crawler.   
When we enter /robots.txt, we can check text  
User-agent: *   
Disallow: /s3cr3t/  
User-agent is target of index ban and Disallow is banned directory or file.(* means EVERY)  
So we found out /s3cr3t directory is disguised, when we check that directory, we can find out password  

## Method of solve
Checking robots.txt
