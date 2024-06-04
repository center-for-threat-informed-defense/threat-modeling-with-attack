Cheat Sheet
==========
.. note::
    This cheat sheet can be used to save time throughout the threat modeling process outlined, but is it important to understand the full process prior to choosing this version. Please review Questions 1 through 4 before choosing this route.

What are we working on?
-----------------------

* Develop a top level DFD for your system
* Identify critical components

What could go wrong?
--------------------

* Analyze your DFD using a simple attack tree or STRIDE
* Brainstorm ATT&CK TTPs that could be used to attack the critical components within your DFD

    * Gather ideas from TTPs used against your tech platform previously- see ATT&CK matrix and down select by platform 
* Quick search through existing security stack for ability to defend against these brainstormed TTPs

What are we going to do about it?
---------------------------------

* Implement the mitigations listed within the ATT&CK page for each TTP

    **OR**

* Implement the NIST 800-53 controls for each TTP using the MITRE Engenuity Mappings Explorer

Did we do a good job?
---------------------

* Periodically repeat this process to evaluate your existing mitigations and make sure they are in sync with the development of your system.