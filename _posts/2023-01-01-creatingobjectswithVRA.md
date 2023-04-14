<H1> How to create objects with vRealize Automation? </H1>

<h2> One objective, multiple paths </h2>
In this series we will develop an use case and the multiple ways we have to get it fulfilled using vRealize Automation and their different integrations. 


<h3>The scenario</h3>
We need to create an AKS Cluster, in a new resource group and a new subnet created on the fly.


<br/><br/>

<b>Option #1:</b> Cloud assembly native resources.

Altough we have native resources to create multiple Azure objects, AKS is not one of them (as of now). So this option is discarded. 

Next...
                
<br/><br/>

<b>Option #2:</b> Code Stream.



|  Pros.    |  Cons     |
|-----------|------------------|
| Easy to implement| Requires an execution enviroment |
|Allows for complex integrations | There are no day 2 actions| 

In <a href= https://github.com/lamaedelanube/lamaedelanube.github.io/blob/main/_posts/2022-03-16-AKS%20con%20CodeStream-1.md>this</a>  post we will discuss further some of the ways to get it accomplished.

<br/><br/>

<b>Option #3 </b> Leverage Cloud Assembly - Terraform integration.

|  Pros |  Cons     |
|-----------|------------------|
| Easy to implement| * Might require an execution enviroment |
|Allows for complex integrations|  You must learn Terraform| 
|Allows some day 2 actions  | Requires a GIT Repo |
|| Terraform provider must exist |

 <a href= https://lamaedelanube.github.io/2022/04/10/Terraform-VRA-Parte1.html>Here</a> we will be talking about this use case

<br/><br/>

4. Create custom resources


|  Pros |  Cons     |
|-----------|------------------|
|The resource will be managed by VRA| This is the hardest to implement|
|| Requires VRO  |
|| Workflows must be created to all CRUD operations |

          
<br/><br/>


