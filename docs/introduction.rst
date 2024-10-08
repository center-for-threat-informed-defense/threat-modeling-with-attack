Introduction
============
.. figure:: /_static/intrographic.png
    :alt: Threat Modeling with ATT&CK Overview Graphic
    :scale: 25%
    :align: center

    Threat Modeling with ATT&CK Overview (Click to Enlarge)

This project defines how to integrate `MITRE ATT&CK® <https://attack.mitre.org/>`_ into
your organization’s existing threat modeling methodology. At the core of this approach
are four key questions, outlined in the `Threat Modeling Manifesto
<https://www.threatmodelingmanifesto.org/>`_, that we need to answer:

* Question 1: What are we working on?
* Question 2: What could go wrong?
* Question 3: What are we going to do about it?
* Question 4: Did we do a good job?

This process is intended for universal application to any system or technology stack
(large or small) using any existing threat modeling methodology like STRIDE, PASTA, or
Attack Trees. To demonstrate its use and applicability to a wide audience of
cybersecurity practitioners, we apply this process to a fictional internet-of-things
(IOT) system called the Ankle Monitoring Predictor of Stroke (AMPS). The fictional AMPS
device gives the wearer and their healthcare providers indications and warnings of a
stroke. This work builds upon The MITRE Corporation’s `Playbook for Threat Modeling
Medical Devices
<https://www.mitre.org/sites/default/files/2021-11/Playbook-for-Threat-Modeling-Medical-Devices.pdf>`_
by applying this integrated threat modeling approach to the fictional medical device
created under that project.

The systems and subsystems that make up this device are modeled after a popular
commercially available IOT device and intentionally chosen for their mobile/cloud-based
dependencies. This broad application to a system spanning mobile and enterprise
environments allows readers to visualize how this process could be applied to their
problem sets. Examples throughout this project are presented from the perspective of a
security team working for the AMPS manufacturer. They have been tasked with modeling
threats to the AMPS device and supporting system infrastructure.

Using the process described throughout Questions 1-4, we identify critical components of
the AMPS, prioritize threats to those components, and recommend mitigations. Threat
modeling with ATT&CK allows us to leverage Cyber Threat Intelligence (CTI) data to
significantly improve our results in Questions 2 and 3. We will break down our means of
answering each question in further detail throughout the sections.

.. note::

    Detailed examples of each step throughout this process will be available in
    collapsed sections throughout. Be sure to check them out!
