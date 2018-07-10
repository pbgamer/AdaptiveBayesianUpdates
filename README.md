# Adaptive Bayesian Updates

<<<<<<< HEAD
There are fourteen files included in this repository: one text file (ending in <samp>.txt</samp>), three <samp>R</samp> scripts (ending in  <samp>.R</samp>), five STAN functions (ending in  <samp>.stan</samp>), and five <samp>R</samp> data objects (ending in <samp>.rds</samp>). The simulation studies reported in Boonstra and Barbaro were run using commit 5; however, all subsequent commits have thus far only made changes to documentation and should therefore yield the same results, subject to simulation error.  
=======
There are fourteen files included in this repository: one text file (ending in <samp>.txt</samp>), three <samp>R</samp> scripts (ending in  <samp>.R</samp>), five STAN functions (ending in  <samp>.stan</samp>), and five <samp>R</samp> data objects (ending in .rds). The simulation studies reported in Boonstra and Barbaro were run using commit 5; however, all subsequent commits have thus far only made changes to documentation and should therefore yield the same results, subject to simulation error.  
>>>>>>> 5ab6064300b1065a3ffcb5c0f5b995203d90997f

## Text file
<samp>runABUSims.txt</samp> is the script for running the simulation study on a cluster using SLURM. The following script does this:

<code> sbatch runABUSims.txt </code>

<<<<<<< HEAD
## <samp>.R</samp> scripts
=======
## R scripts
>>>>>>> 5ab6064300b1065a3ffcb5c0f5b995203d90997f
<samp>runMe.R</samp> provides two means of interfacing with the code. On a local machine, the user may choose a specific scenario (as described in that script) and run the code locally on his/her machine. On a cluster running SLURM, the user can use this script to submit multiple jobs simultaneously. 

<samp>Functions.R</samp> provides all of the necessary functions to fit the methods described in the paper as well as to run the simulation study. The functions <samp>glm_standard</samp>, <samp>glm_nab</samp>, and <samp>glm_sab</samp> are the main statistical contributions from this manuscript.

<samp>GenParams.R</samp> constructs inputs for running the simulation study. As described in the descriptions of this script and <samp>runMe.R</samp>, these inputs can be overwritten by the user.

## STAN files
The STAN files are described below. Note that these currently all implement a logistic link, but changing to a non-logistic link (i.e. log, probit, etc.) will be relatively easy. 

<<<<<<< HEAD
<samp>RegHS_Stable.stan</samp> implements the regularized horseshoe prior, as described in Boonstra and Barbaro, applied to a logistic regression. An <samp>.R</samp> user calls this with <samp>glm_standard</samp> in <samp>Functions.R</samp>. 

<samp>NAB_Stable.stan</samp>, <samp>NAB_Dev.stan</samp> both implement the 'naive adaptive Bayesian' prior, as described in Boonstra and Barbaro, applied to a logistic regression. The '<samp>_Dev</samp>' modifier was initially used for testing development versions of the prior against the current stable version. For the results reported in Boonstra and Barbaro, the only difference between the two is in the hyperprior distribution on &eta; (eta): in the former it is distributed as Inv-Gamma(2.5, 2.5), and in the latter it is Inv-Gamma(25, 25). The 'stable' versions are reported in the main manuscript. An <samp>R</samp> user calls this with the function <samp>glm_nab</samp> in <samp>Functions.R</samp>. 

<samp>SAB_Stable.stan</samp>, <samp>SAB_Dev.stan</samp> are analogous versions of the 'sensible adaptive Bayesian' prior. An <samp>R</samp> user calls this with the function <samp>glm_sab</samp> in <samp>Functions.R</samp>. 
=======
<samp>RegHS_Stable.stan</samp> implements the regularized horseshoe prior, as described in Boonstra and Barbaro, applied to a logistic regression. An R user calls this with <samp>glm_standard</samp> in Functions.R. 

<samp>NAB_Stable.stan</samp>, <samp>NAB_Dev.stan</samp> both implement the 'naive adaptive Bayesian' prior, as described in Boonstra and Barbaro, applied to a logistic regression. The '_Dev' suffix was originally used for testing development versions of the prior against the current stable version. For the results reported in Boonstra and Barbaro, the only difference between the two is in the hyperprior distribution on &eta;: in the former it is Inv-Gamma(2.5, 2.5), and in the latter it is Inv-Gamma(25, 25). The 'stable' versions are reported in the main manuscript. An R user calls this with glm_nab in <samp>Functions.R</samp>. 

<samp>SAB_Stable.stan</samp>, <samp>SAB_Dev.stan</samp> are analogous versions of the 'sensible adaptive Bayesian' prior. 
>>>>>>> 5ab6064300b1065a3ffcb5c0f5b995203d90997f

## <samp>R</samp> data objects
These are the compiled versions of the programs described in the STAN file. If R does not find these, it will go ahead and recompile the STAN files and create new versions. 

### Note, 10-Jul-2018:

<<<<<<< HEAD
=======
### Note, 10-Jul-2018:

>>>>>>> 5ab6064300b1065a3ffcb5c0f5b995203d90997f
After updating to version 3.5.0, <samp>R</samp> occasionally throws the following 'error':

<code>Error in x$.self$finalize() : attempt to apply non-function</code>

Error is used in quotes because it does not interrupt any processes and does not seem to affect any results. Searching online, this has been asked about by others and seems to be related to garbage collection:

http://discourse.mc-stan.org/t/very-mysterious-debug-error-when-running-rstanarm-rstan-chains-error-in-x-self-finalize-attempt-to-apply-non-function/4746