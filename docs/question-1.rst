.. _Question 1:

Question 1: What are we working on?
===================================

.. figure:: /_static/question1graphic.png
  :alt: Question 1 Overview
  :scale: 30%
  :align: center

  Question 1 Overview Graphic (Click to Enlarge)

Question 1 enables the primary and secondary function(s) of the system to be identified and analyzed. It identifies critical tasks that must be performed for the system to successfully accomplish its function(s) and highlights the resources those critical tasks rely upon.

Part 1: Assemble your team
--------------------------

Step 1: Gather relevant documentation
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Ensure the team familiarizes themselves with relevant documentation of the system under analysis. We want to ensure the team understands the system prior to engaging other stakeholders. Depending on your type of system and the time you have, some documents we recommend reviewing are:

+------------------------------------------------+------------------------------+
| Documents of Interest                                                         |
+================================================+==============================+
| Information security policies                  |  Password policies           |
+------------------------------------------------+------------------------------+
| Employee staffing policies                     |  Data classification policies|
+------------------------------------------------+------------------------------+
| Disaster recovery plans                        | Data backup policies         |
+------------------------------------------------+------------------------------+
| Business continuity plans                      |  External drive policies     |
+------------------------------------------------+------------------------------+
| Incident response plans                        |  Network architecture        |
+------------------------------------------------+------------------------------+
| Remote access policies                         |  Network security policy     |
+------------------------------------------------+------------------------------+
| Risk assessment procedures and policies        |  User permission guidelines  |
+------------------------------------------------+------------------------------+
| Allowed applications list                      |  Account management policies |
+------------------------------------------------+------------------------------+
| Security applications list                     |  Cloud security policies     |
+------------------------------------------------+------------------------------+
| File storage application list and policies     |  Cloud architecture          |
+------------------------------------------------+------------------------------+
| Inventory procedures                           |  Mobile security policies    |
+------------------------------------------------+------------------------------+

Step 2: Identify key stakeholders
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

These individuals are your subject matter experts who will provide insights into the nature of the assessed system. They can either serve as active members of the assessment team or as points of contact throughout the assessment as needed. You may already know who these individuals are, but there are some techniques that might help you narrow your search for relevant personnel:

#. Pre-mortem

   * Imagine a crisis scenario: the assessed system is inoperable; the timeline for project development has broken down; you’re unable to provide a key service to your customers, etc. Who do you call? What information do you need?

#. Responsible, Accountable, Consulted, and Informed (RACI) Matrix

   * A RACI Matrix lets you represent which staff are involved in the operation of the system in question, and their respective impact.
   * A RACI Matrix that ties specific staff to tasks and cyber assets can be developed in tandem with the development of a Mission Impact Assessment (see below)

Step 3: Prepare for the kick-off
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Prior to your initial kick-off meeting with the individuals identified in Step 2, request precise programmatic documentation that only speaks to the materials in scope for the assessment – consider using draft documentation instead of waiting for final products.

* For external stakeholders, pairing this with a site visit would allow them to tour the host’s facilities, observe a demonstration, or participate in a technical briefing.

Step 4: Meet with stakeholders
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Depending on time, we recommend having at least two meetings. This gives your stakeholders a chance to communicate with each other and fosters valuable crosstalk. The first meeting is your “kick-off,” which establishes a common understanding of the scope and intent of your threat modeling, establishes relationships with your identified stakeholders, and gives them an understanding of how/why you will be working with them. The second meeting is at the end of your threat modeling process and gives you a chance to present your assessments and get feedback from your stakeholders prior to completion. Informal technical exchanges between stakeholders should also occur outside of these meetings throughout the duration of the assessment.

Part 2: Mission Decomposition
-----------------------------
After conducting your kick-off meeting, it's time to start conducting an analysis of your mission and the systems needed to facilitate it. Drafting this analysis can also be done during your kick-off meeting or over the course of several meetings/discussions with stakeholders, depending on how much time you have. Below are four steps that can guide you through mission and system decomposition. Each step has a series of questions that drive a better understanding of your critical assets.

Step 1: Map the mission objectives
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
At this stage we want to determine: What is the ultimate purpose of the system? What goal is the system trying to accomplish?
It’s here that we’ll invoke our fictional example device: the Ankle Monitoring Predictor of Stroke (AMPS). This fabricated IoT device is borrowed from MITRE’s `Playbook for Threat Modeling Medical Devices <https://www.mitre.org/sites/default/files/2021-11/Playbook-for-Threat-Modeling-Medical-Devices.pdf>`_. In our scenario, this device is meant to be worn by a patient who is at increased risk of experiencing a stroke. By wearing the device throughout the day, the patient and their doctor can monitor for indicators of an imminent stroke via a companion app on the patient’s phone and readings uploaded to the AMPS cloud service each day.
As a security team evaluating AMPS for its manufacturer, we identified that a core mission objective of AMPS is to collect and share patient health data accurately and securely. Because of the sensitive nature of the health data AMPS collects and shares, which includes location data to guide an emergency response in the event of a stroke, the AMPS device should effectively protect the confidentiality of that data.

.. figure:: /_static/3.png
  :alt: Mission/System Decomposition Graphic
  :scale: 50%
  :align: right

Step 2: Identify Operational Tasks (Cross Functional Flow Chart)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Next, leverage the knowledge pooled from stakeholders to determine the different operational sub-systems that contribute to the system’s primary purpose identified in Step 1. An Analytic Hierarchy Process (AHP) can be used to weigh the importance of different operational systems. Ask yourself, what are the operational tasks that must be executed to perform that function? These are also known as Mission Essential Functions (MEFs). To visualize these MEFs, we recommend using a cross functional flow chart like the one below for the AMPS.

.. figure:: /_static/4.png
  :alt: Cross-Functional Flow Chart of a Data Flow in a Fictional Medical Device: the Ankle Monitor Predictor of Stroke (AMPS)
  :scale: 75%
  :align: center

  Cross-Functional Flow Chart of a Data Flow in a Fictional Medical Device: the Ankle Monitor Predictor of Stroke (AMPS)

Part 3: System Decomposition
----------------------------
Step 3: Develop a Data Flow Diagram (DFD) of your system.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
There are multiple ways to design a DFD, but we recommend the `DFD3 <https://github.com/adamshostack/DFD3>`_ standard. Begin by answering the following questions:

* What are the known components of the system?
* What components within your system connect to each other?
* What known third-party connections exist outside of your system’s control?

From these questions, start to draw your diagram and gradually add additional components and sub-systems to the DFD depending on scope and time. Start at a high level and work your way down as seen in the below AMPS examples. Ultimately, these datapoints should come together to form a comprehensive map of your system.

.. figure:: /_static/5.png
  :alt: High-level DFD for AMPS
  :scale: 70%
  :align: left

  High-level DFD (Click to Enlarge)

.. figure:: /_static/6.png
  :alt: Mid-level DFD with Trust Boundaries for AMPS
  :scale: 50%
  :align: right

  Mid-level DFD with Trust Boundaries (Click to Enlarge)

Step 4: Determine which system functions are associated with distinct operational tasks.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
With the DFD of your system in hand, you can then link the system’s operational tasks to specific system functions. When executing a specific task, what parts of the system are utilized? These include both assets and data flows between systems.

+-----------------------------+-------------------------+-----------------------+
|Mission Objective            | Operational Task        | System Function       |
+=============================+=========================+=======================+
| Track patient's stroke risk | Collect sensor data     | AMPS embedded sensors |
+-----------------------------+-------------------------+-----------------------+
| Track patient's stroke risk | Store data in the cloud | AMPS cloud services   |
+-----------------------------+-------------------------+-----------------------+
| Securely share patient data | Store data in the cloud | AMPS cloud services   |
+-----------------------------+-------------------------+-----------------------+


Part 4: Identification of critical assets
-----------------------------------------
Now that you’ve done mission and system decomposition, you should have a much better idea of which system functions facilitate operational tasks that enable your mission. Using your DFD and the matrix from Part 7, you can now identify critical assets. Ask yourself the following questions:

* Which system assets and dataflows are shared by multiple processes?
* What assets and data flows enable different system functions?
* How does the failure of each operational task impact the system’s mission objectives?
* What are downstream effects of taking each cyber asset offline?

In the example below, we’ve identified critical assets/components of the AMPS using our DFD, highlighting them in gold.

.. figure:: /_static/7.png
  :alt: Critical AMPS System Components
  :scale: 60%
  :align: left

  Critical AMPS System Components

.. figure:: /_static/8.png
  :alt: Mid-Level DFD with Trust Boundaries & ID-ed Critical Assets
  :scale: 60%
  :align: right

  Mid-Level DFD with Trust Boundaries & ID-ed Critical Assets

