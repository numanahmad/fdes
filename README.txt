FDES

	This tool offers a behavioral comparison of process models 
	and computes feedback about encountered differences. 
	It is based on a model of concurrency, Asymmetric Event 
	Structures (AES). 
	The general idea of the technique is to compute the AES of 
	a process model (it can be derived from its PES) and apply 
	the reduction technique	presented in http://arxiv.org/abs/1403.7181. 
	In order to compute a canonical representation for the behavior 
	of an AES, the Nauty (see reference at the bottom of the 
	file) library is used to compute the canonical order of the 
	events in a PES. 
	Additionally, in order to obtain a finite representation of 
	a process with cycles, an unfolding technique is presented 
	to compute a complete prefix unfolding (it was built on top 
	of the library UMA, see reference at the bottom of the file). 
	Such prefix is the used to compute the corresponding AES. 
	In order to find matching of events between a pair of AES, an
	error-tolerant graph matching technique is used.
	It is under testing and further optimizations will be added in order
	to cope with larger process models. 

Install
   - Given that we rely on Nauty, it is necessary to place the folder of Nauty in the 
     same directory of the FDES.jar file. See below the structure of the folder:	
	.
	├── README.txt
	├── models
	├── nauty
	│   ├── dreadnaut
	│   ├── …
	├── FDES.jar

   - The first time the .jar is executed, it might be necessary to enable the permission for the file in nautyIO/runNauty.sh
   
   - The folder ‘models’ contains a set of variants of process models that can be used for testing the tool. 


How to run

	java -jar FDES.jar -m1 model1 -m2 model2 -ES AES -C -EPC

	
    Parameters:
	-C   : Specifies if the computation (and reduction) of the AES will be 
	       canonical
 	-EPC : Specifies if the input models are EPCs in XML format, if it is not 
	       specified, program is expecting a BPMN in XML format
 	-ES <arg> : Select the event structure to use: AES (under testing FES or AES-FES)
 	-m1 <arg> and -m2 <arg> : Specifies the pairs of models to compare. 


References:
	- http://www.win.tue.nl/~dfahland/tools.html
	- http://cs.anu.edu.au/~bdm/nauty/

