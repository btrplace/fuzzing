# fuzzing
PFE - Personal project for the Master 2 Ubinet program of Université de Nice - Sophia Antipolis.

Who? 
Name: Fabien Hermenier, Ludovic Henrio
Mail: fabien.hermenier@unice.fr, ludovic.henrio@cnrs.fr
Telephone: never heard about that technology. Literally
Web page: https://sites.google.com/site/hermenierfabien/home, http://www-sop.inria.fr/oasis/Ludovic.Henrio/

Where?
Place of the project: Inria (partially) 
Address: 2004, route des Lucioles
Team: Scale
Web page: https://team.inria.fr/scale/

What?
Title: Fuzzing a VM Scheduler
Pre-requisites if needed: - 
Description:

Inside a IaaS cloud, the VM scheduler is responsible for deploying the VMs to appropriate physical servers according to the SLAs. When environmental conditions (failures, load spike, etc) or the clients' expectation evolve, the VM scheduler must reconfigure the deployment accordingly, using actions over the VMs and the servers. Providers typically bill the client on a utility computing basis. The cost reflects the amount of resources allocated and consumed, minored by the providers penalties when the SLA is not met in practice.

The VM scheduler is the cornerstone of the good functioning of an IaaS cloud. The provider bases his offering and the clients base their requirements on the features described in its documentation. The scheduler is then expected to take decisions that are aligned with its theoretical behavior. Implementing a VM scheduler that is correct, i.e. that behaves according to its documentation, is however difficult. To implement a reconfiguration action, a developer must understand the infrastructure management capabilities and the pre-conditions related to each reconfiguration action. For example, one of the preconditions is no server can be turned off with VMs running on it. To implement a SLA enforcement algorithm, the developer must also master several families of combinatorial problems such as assignment and task scheduling and ensure its code fits the many possible situations. For example, he must consider the implication of every possible VM state on its resource consumption.

The difficulties inherent in the implementation a VM scheduler have led to defective implementations with severe consequences for both clients and providers. For example, Nova is the components embedding the VM scheduler of the leading open source IaaS software stack OpenStack. The scheduler code is tested and every modification must be peer-reviewed before integration. Despite this quality management system, 8 bugs are currently open about correctness issues. The same kind of bugs has been seen in the research oriented VM scheduler BtrPlace (http://www.btrplace.org).

Fuzzing is a software testing technique to check complex software. It consists in generating random input data for a component to usually detect crashing situations. We are currently trying to fuzz BtrPlace but in addition to crashs, we also detect inconsistent behavior with regards to a formal specification of some components. In this PFE, we want to go beyond these simple fuzzing techniques. More especially, we want to propose novel exploration techniques. For example by fragmenting it into comparable situations then to browse between fragments first. It might also be interesting to adapt the search with regards to the result of the previous tries.

The objective of this PFE are:
- to establish a bibliography around fuzzing techniques, from generic to domain specific approaches.
- to propose novel exploration techniques
- to implement them inside the current fuzzer of BtrPlace
