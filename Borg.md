# Large-scale cluster management at Google with Borg 
  - https://storage.googleapis.com/pub-tools-public-publication-data/pdf/43438.pdf
  
### 1. Intro
1. what is Borg?
    - Google’s Borg system is a cluster manager that runs hundreds of thousands of jobs, from many thousands of different applications, across a number of clusters each with up to
tens of thousands of machines
    - The cluster management system we internally call Borg admits, schedules, starts, restarts, and monitors the full range
of applications that Google runs. This paper explains how.
 
 2. Benefits
    - hide the details of resource management and failure handling so its users can focus on appication development instead. 
    - Operattes with high reliability and avaliability, and supoorts application that do the same. 
    - lets us run workloads across tens of thousands of machines effectively. Borg is not the first system to address these issues, but it’s one of the few operating at this scale, with this degree of resiliency and completeness. 

3. The user's perspective 
    - Borg's users are Google developers and system administration (site reliablity engineers) that run Google's applications and srevices. 
    - workload: the first is the long-running latency-sensitive requests, such as Gmails, Google Docs, Web Search. The seccond is the batch of jobs that short-term performance jobs. 
    
4. Clusters and Cells 
    - The machines in a cell belong to a single cluster, defined by the high-performance datacenter-scale network fabric that connects them. A cluster lives inside a single datacenter building, and a collection of buildings makes up a site.1
    
