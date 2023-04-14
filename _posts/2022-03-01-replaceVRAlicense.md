Replace the VRA license


Imagine that you  log into VRA and you find the following message.
 
Well, since changing a license is something we do not ussually do, we might completely forget about license expiration. in the case of VRA, unlike most other Vmware's products, does not have an option on your console to perform this task.
Remember: EVERY vRealize Automation management task should be done through Lifecycle Manager. This is the designed(and easy) way. 

<b>How To?</b>

Phase A. Add the license in locker
1.	Log in to lifecycle manager
2.	Go to locker – licenses
 
3.	Add license manually and assign the new license we have. Click Validate and then Add.

Phase B. Assign the license to the product:
1.	Select the environments tab and there see details.
2.	Find the vRealize Automation product.
3.	There go to (....) and click on add license.
4.	When it shows us the previous license we click on next and then select the new license.
5.	Again it will ask us to mark the license we want to replace.

But, what if there is no LCM?

This should not be a productive case and I would really recommend installing the LCM and importing the environment exists manually. But hey! let's just imagine that's the case. Then, we can add the license directly from the VRA command line:
1.	SSH access to a VRA appliance.
2.	Review the license that currently exists:
vracli license current
! [image] (https://user-images.githubusercontent.com/51407995/163229110-d63d54b6-85e9-4357-af03-01d0c0a7a96d.png)
3.	Add the new license:
vracli license add {license}
4.	And Delete the previous one:
VRA License Remove {license}
 
5.	Restart the appliance. This way.
And after waiting for half an hour for the cluster to come back online, we will be done!
