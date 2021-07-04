---
title: "Migration from BizTalk 2006 to 2013R2: lessons learned"
date: "2015-12-12"
categories: 
  - "biztalk"
  - "visual-studio"
tags: 
  - "biztalk-2006"
  - "biztalk-2013r2"
  - "cumulative-updates"
  - "migration"
---

What we learned when migrating a BizTalk Server 2006 farm (with multiple solutions/projects) to BizTalk Server 2013R2:

### 1\. You need an intermediate step

Migrating BizTalk 2006 solutions directly to BizTalk 2013R2 (Visualt Studio 2013) is not supported. You will need to migrate the solution to BizTalk 2010 (Visual Studio 2010) first as an intermediate step. More information [here](https://social.msdn.microsoft.com/Forums/en-US/f9ac6b6c-3dbe-487b-85c5-448d257d62f4/migration-from-biztalk-server-2006-to-2013?forum=biztalkgeneral) in a MSDN forum thread. (nothing fancy in this one I must admit, but you need to take this step into account when estimating an upgrade...)

### 2\. Install the latest BizTalk CU on your development machine

The fact that we needed an extra intermediate step in the migration process was no big deal in our situatuion. We had an emtpy VM with BizTalk 2010 and Visual Studio 2010 in place. This machine was installed a few years ago by a developer, but was never used. It had no BizTalk Cumulative Updates installed.

We didn't have any issues when migrating simple BizTalk 2006 solutions. We migrated to BizTalk 2010 and then migrated to BizTalk 2013R2 on an other machine.

When migrating the more complex solutions (big orchestrations and lots of ASMX web ports), we started to experience some weird behaviour in Visual Studio 2010:

- Web ports and schema's went missing
- Unrecognized projects in Visual Studio 2013 (after successful build in Visual Studio 2010)
- [Mismatched 'braces' '{}' error](https://support.microsoft.com/en-us/kb/2548064) on build

That last error lead us in the right direction: [BizTalk Server 2010 CU2](https://support.microsoft.com/en-us/kb/2573000):

> This issue might also occur when you try to build a BizTalk Server 2010 solution that was converted from a Microsoft BizTalk Server 2006 R2 or Microsoft BizTalk Server 2009 solution in Visual Studio 2010.

After installing [BizTalk Server 2010 CU8](https://support.microsoft.com/en-us/kb/3081737) on our development machine (the latest update at that moment), we restarted the migration (from the original BizTalk 2006 solution) of those complex projects, without the need to replace anything. The whole migration process completed without any error!

So, spare yourself the misery and start with a fully up to date BizTalk 2010 development environment. Other blogs on the internet might suggest to fix the "mismatched 'braces' '{}' error" error [by manually editting the .odx file](http://biztalksolutionstoproblems.blogspot.be/2012/12/working-on-project-that-involved-lot-of.html). This was not the correct fix in our case as the error kept returning after every other change in the orchestration.
