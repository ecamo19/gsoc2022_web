# 

# __[Sobol Variance Partitioning Implementation for PEcAn’s uncertainty module](https://summerofcode.withgoogle.com/programs/2022/projects/FzRn47Nh)__

[Code Availability](https://github.com/ecamo19/gsoc_project_2022_vm){ .md-button .md-button--primary }


 __Mentors:__ 

 Michael Dietze, Boston University

 Alexis Helgeson, Boston University

__Contributor:__

 Erick Calderon-Morales
 
__email:__ erickcamo19@gmail.com 

# Project's Description

Quantifying precisely the degree of uncertainty in models predictions and acknowledging the existing data gaps still remains challenging given the immense variety of data sources that exist and the lack of open source tools that quantify the models' uncertainty. The PEcAn (Predictive Ecosystem global Analyzer) project is an open-source tool that aims to solve this problem by synthesizing multiple data sources for the improvement of model-data feedback. With this tool it is possible to use models for forecasting how an ecosystem might respond to climate change and also is possible to quantify the uncertainty around its predictions. However, currently PEcAn uses a method that do not explore the whole parameter space, giving an incomplete quantification of the uncertainty around important variables in models. Thus, it is necessary to develop new functionalities in PEcAn in order to improve the assessment of ecosystem models' uncertainties. The Sobol Variance Partitioning (SVP) is a method for accessing the degree of uncertainty in models that explore all the parameter space, improving the quantification of model uncertainties. In this project, we will focus on developing a new function within PEcAn that estimates the uncertainty components of a model taking into account higher-order parameter interactions using the SVP method.






