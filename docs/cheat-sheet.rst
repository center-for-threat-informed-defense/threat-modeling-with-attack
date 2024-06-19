Condensed Process
=================

.. note::
    This Condensed Process should only be used if your team has limited time to conduct threat modeling (days instead of weeks). Before using, please review Questions 1 through 4 of the uncondensed process.

:ref:`Question 1`
-------------------

.. figure:: /_static/condensedprocess1.png
  :alt: Data Flow Diagram Outline
  :scale: 100%
  :align: right

  Data Flow Diagram Outline

Develop a top-level Dataflow Diagram for your system

Identify critical components and dataflows that, when impacted, would result in mission failure

:ref:`Question 2`
-------------------

.. figure:: /_static/condensedprocess2.png
  :alt: Attack Tree Outline
  :scale: 100%
  :align: left

  Attack Tree Outline

Analyze your DFD using a structured brainstorming technique (Attack Tree, STRIDE, etc.)

Brainstorm ATT&CK TTPs that could be used to attack the critical components within your DFD

You can gather ideas from TTPs previously used against your tech platform – see the ATT&CK matrix and select by platform
or use the Center’s Top ATT&CK Techniques Calculator.

Once you’ve got your list of brainstormed TTPs, search through your existing security stack for ability to defend against them.

:ref:`Question 3`
-------------------
Implement the mitigations listed within the ATT&CK page for each brainstormed TTP

.. figure:: /_static/condensedprocess3.png
  :alt: ATT&CK Mitigations Outline
  :scale: 100%
  :align: center

  ATT&CK Mitigations Outline

	**OR**

Implement the NIST 800-53 controls for each brainstormed TTP using the MITRE Engenuity Mappings Explorer

.. figure:: /_static/condensedprocess4.png
  :alt: Mappings Explorer Outline
  :scale: 100%
  :align: center

  Mappings Explorer Outline


:ref:`Question 4`
-------------------

.. figure:: /_static/condensedprocess5.png
  :alt: Reevaluate Graphic
  :scale: 100%
  :align: right

  Reevaluate

Periodically repeat this process to evaluate your existing mitigations and make sure they are in sync with the development of your system.

