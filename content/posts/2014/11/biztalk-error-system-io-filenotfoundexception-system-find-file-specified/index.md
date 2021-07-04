---
title: "BizTalk Error: System.IO.FileNotFoundException: The system cannot find the file specified."
date: "2014-11-06"
categories: 
  - "biztalk"
  - "deployment"
  - "rdexperts"
tags: 
  - "biztalk"
  - "custom-functoid"
  - "gac-reference"
---

After deployment of my BizTalk solution to the TEST environment, I was experiencing this error on a given receive port. I was not having this problem earllier on my local DEV BizTalk server/machine.

[![2014-11-06 09_03_29-AP60TST - MultiDesk](/images/2014-11-06-09_03_29-AP60TST-MultiDesk.png)](http://blog.jeroenmaes.eu/wp-content/uploads/2014/11/2014-11-06-09_03_29-AP60TST-MultiDesk.png)

Don't be mistaken when you see this error, this is not an error related to the adapter. I found other blogs stating this had something to do with the DLL's of the solution not being the correct version. So I redeployed everything (using the BTDF), but without any success.

In my case, after browsing the GAC and comparing my DEV with the TEST environment, **I found out that my deployment  was missing a Custom Functiod in the GAC that I was using in my map.** After fixing this in my BTDF deployment script and redeploying, the error was gone.
