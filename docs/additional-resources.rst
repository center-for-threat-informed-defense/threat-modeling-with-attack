Additional Resources
====================

Cyber Threat Intelligence Resources
-----------------------------------

Leveraging existing CTI allows you to develop known attack vectors that could be used against your system. There are many resources for CTI data and this appendix is made to refence a few that we have found useful.

*	The Center’s `Sightings Ecosystem <https://mitre-engenuity.org/cybersecurity/center-for-threat-informed-defense/our-work/sightings-ecosystem/>`_ project is an example of data that can be leveraged throughout this process to help identify, or highlight, commonly seen TTPs. At the time of publish, the work consists of over 1.6 million sightings of 353 unique techniques from almost 200 countries.
*	Many venders publish opensource reports on blogs or their websites. Monitor these sources for new/relevant reports.  Attack Flow created best practices for selecting open-source reports and this can be beneficial during this step:

.. important::
    * “Reports should be transparent about where the data originates and provide a technically competent overview of an incident.
    * Reports should originate from a vendor with a track record of accurate reporting and first-hand analysis of the incident in question.
    * Reports should provide the most current information on the malware or breach.
    * Reports should make it easy to identify any information gaps. Use multiple sources to address gaps and corroborate the data, if possible.
    * Reports should distinguish between facts, assumptions, and analytical assessments.
    * When available, use attribution and targeting information from reports to enrich your attack flows.”

*	When it comes to researching CTI for embedded systems, MITRE developed a publicly available knowledge base called `EMB3D <https://emb3d.mitre.org/properties-list/>`_. This is a great resource for both theory and evidence. Start by down selecting by embedded system property and read through the various threats to each.

It is a good idea to have a central location/repository for all your CTI data. This can be a spreadsheet or a threat intelligence platform (TIP) like OpenCTI (see example data below for FIN7). There are many TIP out there that will do to research work for you – automatically pulling in the latest vender reports. Some TIPs will even auto-parse the data in reports for you. Be sure to spot check any automated report parsing for accuracy.

