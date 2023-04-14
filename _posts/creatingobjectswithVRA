<H1> How to create objects with vRealize Automation? </H1>

<h2> one objective, multiple paths </h2>
In this series we will develop an use case and the multiple ways we have to get it fulfilled using vRealize Automation and their different integrations. 


<h3>The scenario</h3>
We need to create an AKS Cluster, in a new resource group and a new subnet created on the fly.


<br/><br/>

Option #1: Cloud assembly native resources.

Altough we have native resources to create multiple Azure objects, AKS is not one of them (as of now). So this option is discarded. 

Next...
                
<br/><br/>

Option #2: Code Stream.



|  Pros.    |  Cons     |
|-----------|------------------|
| Easy to implement| Requires an execution  |
|Allows for complex integrations | There are no day 2 actions| 

<a href= https://github.com/lamaedelanube/lamaedelanube.github.io/blob/main/_posts/2022-03-16-AKS%20con%20CodeStream-1.md>Aquí</a> In this post we will discuss further some of the ways to get it accomplished.

<br/><br/>

3. Leverage Cloud Assembly - Terraform integration.

|  Pros |  Cons     |
|-----------|------------------|
| Easy to implement| * Podria requerir un motor de ejeucion |
|Allows for complex integrations|  You must learn Terraform| 
|Allows some day 2 actions  | Requires a GIT Repo |
|| Terraform provider must exist |

Here <a href= https://lamaedelanube.github.io/2022/04/10/Terraform-VRA-Parte1.html>esta</a> we will be talking about this use case

<br/><br/>

4. Create custom resources


|  Pros |  Cons     |
|-----------|------------------|
|El recurso creado será como uno nativo de VRA| This is the hardest to implement|
|| Requires VRO  |

          
<br/><br/>
####5. Usar SaltStack  Config
####|  Pros |  Cons     |
####|-----------|------------------|
####|Allows for a lot| Requires the implementation of the salt stack infrastructure|
####|| There is a learning curve to Salt Stack  |

