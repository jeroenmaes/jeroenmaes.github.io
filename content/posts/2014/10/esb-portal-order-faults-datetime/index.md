---
title: "ESB Portal - Order Faults by DateTime"
date: "2014-10-22"
categories: 
  - "biztalk"
  - "esb-toolkit"
  - "rdexperts"
tags: 
  - "biztalk"
  - "default-order"
  - "esb-management-portal"
---

The ESB Portal can be a usefull tool, but can become an anoying one as well quite fast... The default order of the Faults in the grid is by Severity. You can order by DateTime, but this sorting order will be lost on page reload... Verry irritating indeed.

[![2013-03-21 15_31_59](/images/2013-03-21-15_31_59.png)](http://blog.jeroenmaes.eu/wp-content/uploads/2013/03/2013-03-21-15_31_59.png)

We can change the standard sorting order by opening the ESB.Portal solution and adding some code to the FaultList.ascx.cs Class:

[![2013-03-21 15_28_20](/images/2013-03-21-15_28_20.png)](http://blog.jeroenmaes.eu/wp-content/uploads/2013/03/2013-03-21-15_28_20.png)

 

// Order Faults by DateTime Desc instead of Severity
if (Faults.Rows.Count > 0)
{
  Faults.Sort("DateTime", System.Web.UI.WebControls.SortDirection.Descending);
}

The result on page load:

[![2013-03-21 15_38_23](/images/2013-03-21-15_38_23.png)](http://blog.jeroenmaes.eu/wp-content/uploads/2013/03/2013-03-21-15_38_23.png)
