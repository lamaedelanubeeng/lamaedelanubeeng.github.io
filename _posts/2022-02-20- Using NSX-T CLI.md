<h1> NSX-T Central CLI </h1>

I like the NSX-T CLI quite a lot. I think it's very intuitive and covers any (or almost any) use case I've been presented with. The documentation seems really good, we can find it <a href="https://vdc-download.vmware.com/vmwb-repository/dcr-public/cc42e3c1-eb34-4567-a916-147e79798957/8264605c-a5e1-49a8-b603-cc78621eeeab/cli.html.">here</a> 


Let's say that we are facing a scenario in which we have to execute one or more actions at the same time on different NSX-T objects. We are going to leverage the NSX-T CLI. However, Who wants to log manually into all the managers and edges? No one has time for that.

Luckily there is a way to execute different commands from one of the managers servers, and get them run in all our infrastructure. It is the NSX-T Central CLI, Which I rather call the ON command:


<img width="741" alt="image" src="https://user-images.githubusercontent.com/51407995/163097614-590de761-8bad-4a44-ac58-4eea4c94e4bf.png">



<b>How to use it? </b>

Well, we simply enter one of the managers servers as admin, and type on and tab, the list of available UUIDs will appear.
Personally, what I do is to copy that list and pass it to excel, and there "format" the command I want to execute, for each instance.


Let's see an use case:


I have to configure VRLI as the receiver of the logs for all managers and edges in the environment. We know that the command is as follows:

<img width="741" alt="image" src="https://user-images.githubusercontent.com/130717306/231923043-5ee22215-aaa3-4a4f-a3d9-aa19af32039e.png">



So, in my case it would be something like this:

<img width="741" alt="image" src="https://user-images.githubusercontent.com/51407995/163097839-f9890524-72b3-4a9a-9e63-06526147ee71.png">


And so on,  for all nodes in out NSX-T infrastructure.


With this, we can copy and paste the entire block and wait for each of the commands to be executed. 

Aaaaaand... done!
