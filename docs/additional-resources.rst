.. _Additional Resources:

Additional Resources
====================

Cyber Threat Intelligence Resources
-----------------------------------

Leveraging existing CTI allows you to develop known attack vectors that could be used
against your system. There are many resources for CTI data and this appendix is made to
refence a few that we have found useful.

*	The Center’s `Sightings Ecosystem
 	<https://mitre-engenuity.org/cybersecurity/center-for-threat-informed-defense/our-work/sightings-ecosystem/>`_
 	project is an example of data that can be leveraged throughout this process to help
 	identify, or highlight, commonly seen TTPs. At the time of publish, the work
 	consists of over 1.6 million sightings of 353 unique techniques from almost 200
 	countries.
*	Many venders publish opensource reports on blogs or their websites. Monitor these
 	sources for new/relevant reports.  Attack Flow created best practices for selecting
 	open-source reports and this can be beneficial during this step:

.. important::
    * Reports should be transparent about where the data originates and provide a technically competent overview of an incident.
    * Reports should originate from a vendor with a track record of accurate reporting and first-hand analysis of the incident in question.
    * Reports should provide the most current information on the malware or breach.
    * Reports should make it easy to identify any information gaps. Use multiple sources to address gaps and corroborate the data, if possible.
    * Reports should distinguish between facts, assumptions, and analytical assessments.
    * When available, use attribution and targeting information from reports to enrich your attack flows.

*	When it comes to researching CTI for embedded systems, MITRE developed a publicly
 	available knowledge base called `EMB3D <https://emb3d.mitre.org/properties-list/>`_.
 	This is a great resource for both theory and evidence. Start by down selecting by
 	embedded system property and read through the various threats to each.

It is a good idea to have a central location/repository for all your CTI data. This can
be a spreadsheet or a threat intelligence platform (TIP) like OpenCTI (see example data
below for FIN7). There are many TIP out there that will do to research work for you –
automatically pulling in the latest vender reports. Some TIPs will even auto-parse the
data in reports for you. Be sure to spot check any automated report parsing for
accuracy.

Attack Flow
-----------

.. raw:: html

     <iframe width="560" height="315" src="https://www.youtube.com/embed/h_BC6QMWDbA?si=Abpy35U4SYKMYUeE" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

.. TODO were they planning to put a video here? we don't have an attack flow youtube

|

Emulation Tools Mapped to ATT&CK
--------------------------------

There are existing processes or data sources you can leverage to answer these questions.
Perhaps your organization has a process for system risk acceptance, or you actively
track system patches and compliance metrics.

Alternatively, you can stress test your system by subjecting it to some type of security
assessment. This can be accomplished through an internal or external team emulating
adversary behavior. Short of a full red teaming exercise, existing resources such the
`Adversary Emulation Library
<https://github.com/center-for-threat-informed-defense/adversary_emulation_library/>`_
and `Caldera <https://caldera.mitre.org>`_ integrate directly with MITRE ATT&CK and can
be used as part of attack simulation exercises. Other tools, like the `Atomic Red Team
<https://atomicredteam.io>`_, detail tests tied to specific ATT&CK techniques that can
be performed on your system to evaluate the strength of your mitigations.

These can all inform your secondary review and give you the answers you need. From this
secondary review, you’ll be able to ensure that your mitigations are sufficiently
tailored to your system as it evolves with time.
