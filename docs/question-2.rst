Question 2: What could go wrong?
================================

.. figure:: /Graphics/Question2Graphic.png
    :scale: 75%
    :align: center

The process outlined in Question 1 derives critical assets within a particular system.
In Question 2, we identify and prioritize threats to those assets. ATT&CK will serve as
the framework through which we map and discuss threats to our system. While our
analysis will go beyond the tactics, techniques, and procedures (TTPs) found within
ATT&CK, its value as a language for detailing adversary behaviors makes it a central
part of our approach. ATT&CK’s widespread use within the CTI community and its
comprehensive classification system allows us to draw upon existing threat data while
still integrating additional threats not yet captured in public reporting.
For more information on MITRE ATT&CK, see these resources.

Theory vs. Evidence
-------------------

Generally, there are two complementary approaches that can be utilized to perform
threat analysis: **Theoretical Modeling**, and **Evidence-based Analysis**. Regardless of
which threat modeling methodology you use to answer Question 2, you will need to
strike a balance between these two approaches for your model to be effective. Both
approaches address different aspects of the threat landscape, directly addressing the
potential (“Could” and “Could not”), and the possible (“Has” and “Has not”) threats
that concern your system.

The two axis on the above table represent the theoretical and evidence-based outcomes.

* Theory includes threats that have potential to impact your system.
   * Theory-base threats are hypothetical threats. These include brainstorming
   conducted by your team, known exploits performed in a controlled environment, and
   hypothetical attacks that have not been leveraged by threat actors.
* Evidence includes documented threats that have been leveraged against other system(s)
   * Evidence-based threats are observed threats. These include TTPs used to exploit
   technology platforms leveraged by your system, known exploits used by adversaries
   that target your industry, and malicious actions you’ve recorded within your system.

When considered together, these two approaches give a well-rounded view of a system’s
security posture, both for known and unknown threats.

.. figure:: /Graphics/10.png
    :scale: 75%
    :align: center

|

The above scale illustrates how theory and evidence support each other throughout the
threat modeling process by focusing on the vulnerability disclosure lifecycle.
Inherently, theory-based modeling approaches tend to be more preparatory in
anticipation of an unknown vulnerability, while evidence-based approaches tend to be
more reactionary and respond to actualized threats in the wild.
In the following section, we will be modeling threats against the AMPS device to
demonstrate a well-rounded theory and evidence approach. We will employ Attack Trees
as an example of one of the threat modeling methodologies that could be used to derive
potential threats. Using our tree, we’ll map theoretical and evidence-based threats an
adversary might exploit to extract user information.

Theory
------

As we’ve discussed, a theory-based approach, regardless of which threat modeling
methodology is used, identifies threats that have a potential to impact your system.
We broke this approach into three parts.

Part 1: Structured threat brainstorming
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Goal:** Generate an unweighted list of threats against your system, based on system
analysis produced when answering Question 1.

Mapping theoretical attacks on your system establishes the scope for our threat
calculus. Much like we did in answering Question 1, we must think back to the key
assets we’re trying to protect. We then start from a high level, identifying as many
access vectors targeting our critical assets as we can, or at least a large
representative sample. This wide aperture allows us to then hone our focus as we
progress to cataloguing attacks based on real-world Evidence in the next section. In
this manner, we’re able to capture attacks that are entirely possible but have yet to
be observed in the wild, while also focusing much of our efforts on known
vulnerabilities. While there are varying methods for building our catalogue of
intrusions, we’ve chosen to leverage attack trees.

**What is an attack tree?**

Attack trees are a threat modeling technique that allows analysts to map the various
ways in which an adversary could exploit a specific system to accomplish a specific
set of goals. In the context of the AMPS, we’ve identified that a key mission
objective of ours is maintaining the confidentiality of the user’s data.  Our example
attack tree will therefore aim at mapping the different pathways an adversary could
take to access sensitive user information, namely their location.

**Bottom-up attack trees**

Attack trees typically represent the flow of attacker actions in two ways: top-down or
bottom-up. The attack tree below relies on a bottom-up approach and will serve as our
template moving forward. This tree captures the sequential pathways an attack could
and, in some cases, must take to reach their objective. Regardless of the attacker's
intention, any adversary seeking to exploit a given system must achieve these
intermediate goals. In this manner, the tree is agnostic towards the subsequent goals
of the attacker.

.. figure:: /Graphics/11.png
    :scale: 50%
    :align: center

|

Here we see a theoretical attack tree for a thief attempting to burgle a house.
The thief has several potential avenues for achieving their goal. Some are more
complex than others, requiring multiple steps. Some constitute entire sub-trees of
their own, such as the “Garage Attack”. Each attack has its associated characteristics:
the cost of the attack, the complexity, the likelihood of success, the time needed to
execute it. Each of these will influence the actions of the attacker and therefore
influence where mitigation strategies should be deployed.

The origin point of the tree is the kernel, or root node, the ultimate objective of
the attacker that sits at the top of the tree (in the example above, the root node of
the tree is “Burgle House”). The attacker works their way towards that objective by
satisfying the intermediate goals that branch out from the root node. Each branch
represents a different exploitation strategy that can or must be employed to achieve
the ultimate objective. In some cases, a particular strategy (branch) must be executed
to allow another strategy to move forward.

.. figure:: /Graphics/12.png
    :scale: 50%
    :align: center

|

The arrow-shaped OR nodes within the tree represent goals that can be achieved by any
of the goals below them (here, Intermediate Goal 1 OR 2 OR 3). The flat bottom AND
nodes, similarly, are fulfilled by the goals listed beneath them. All these goals
(here, Subgoal 3a AND Subgoal 3b) must be fulfilled to progress. The square subgoals
represent the actions that must be taken to achieve their final goal.
Using our knowledge of the system we codified responding to Question 1, we now need to
brainstorm potential attacks that can be launched against the critical assets we
identified. We will do this using an attack tree. Initially, the nodes within the
tree can be conceptual in nature. In the later steps, these will become more granular.

Part 2: Critical path analysis
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Goal:** Find commonalities between threats produced during brainstorming and identify
critical paths or components in your system.

In this step, just as we mapped system processes to critical assets in Question 1,
we’re taking the theoretical attacks we’ve brainstormed and associating them with
critical paths and components.

.. figure:: /Graphics/13.png
    :scale: 50%
    :align: left

.. figure:: /Graphics/14.png
    :scale: 65%
    :align: right

As we establish these associations between threats and assets, we’ll begin distilling our theoretical threats. This exercise will clarify how steps in an attack are associated with one another, determining which attacks must be executed and in what order. It will also verify whether certain steps in an attack are still possible once mapped onto specific assets within the system.
In the example below, we’ve created an attack tree and populated it with theoretical threats against our AMPS device. In Question 1, we said collecting and securely storing patient data was essential to our product. We’ve therefore made the goal of our attack tree stealing patient sensor data, specifically user location data. We’ve spoken with our team, trawled academic literature, reviewed blog posts by industry professionals, and watched presentations by security experts to create an initial set of theoretical threats to our device. Taken together, these give us an initial list of threats that we can then associate with our critical assets.

.. figure:: /Graphics/15.png
    :scale: 65%
    :align: center

Part 3: Translating Attack Tree Concepts into ATT&CK TTPs
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
**Goal:** Use ATT&CK as a common language to describe adversarial behaviors against system components

.. figure:: /Graphics/16.png
    :scale: 75%
    :align: center

|

Now that we’ve built out our attack tree, clarifying our language and invoking specific system data exchanges and assets, we can begin cataloguing the ATT&CK Tactics, Techniques, and Procedures (TTPs) needed to facilitate those attacks on each critical path and component. These datapoints will constitute the core of our attack tree and link our results from this theoretical exercise to the results of our evidence-based analysis later.

This step is essentially the manual translation of Part 2’s conceptual attack steps into tangible ATT&CK TTPs. We recommend using Decider to assist in these translations. This tool allows you to either filter for specific tactics, platforms, and data sources that will direct you towards the appropriate TTP or search key terms, related to your attack concept, in the search bar to derive the appropriate TTP. When comparing your Part 2 attack tree concepts to existing ATT&CK TTPs, consider adding nodes to your attack tree for any TTPs you may not have thought of.

Below is an example of how a theoretical attack can be aligned with a TTP (T1185: Browser Session Hijacking).

.. figure:: /Graphics/17.png
    :scale: 50%
    :align: right

|

Over the course of our search for threats relevant to the AMPS device, we determined that one of the vectors (branch of the tree) an attacker could use to access user location data was by accessing their web portal. We determined that one potential vector for gaining access to their portal was by stealing their log in credentials. This can be done using an activity characterized as Session hijacking in ATT&CK.

Ultimately, we will be integrating these threats into a singular tree using the Center’s Attack Flow tool, directly linking them to our critical assets. Attack Flow integrates seamlessly with ATT&CK. Threat actor actions represented as nodes on the tree can be linked to specific TTPs. Furthermore, additional contextual elements such as attack characteristics, assets, data types, conditions, and references can be added to each node of your tree. Having identified Browser Session Hijacking (T1185) as one of our theoretical exploits, we can now associate that specific node on the tree with T1185, thereby pulling in all the data that’s been associated with that exploit. Not all the threats you identify will be directly tied to TTPs. These threats should still be included in your tree and will still inform the response you develop in Question 3.



An example of the AMPS attack tree and all associated TTPs can be found below.

.. figure:: /Graphics/18.png
    :scale: 75%
    :align: center

Evidence
---------

.. note::
  Throughout the evidence section for the purpose of saving time layers can be omitted. For the sake of evidence being incorporated it is recommended to include at least one of the layers for data, but which is up to the needs of the organization.

The previous section focused on a theory-based approach using attack trees. In this section, we will cover the evidence-based approach to complement our theoretical tree and aid in identifying additional TTPs for consideration in the tree. Evidence is derived by attacks observed in the wild and reported on by legitimate sources. The MITRE ATT&CK team reads opensource reports published by these sources and associates adversarial behavior with a TTP. Sources for these TTPs are different than those previously used to build the theory-based attack tree.  This is why the complementary approach of theory and evidence is crucial. We will use the TTPs derived in this section to add to the attack tree in the previous section. We recommend considering TTPs derived by four types of observed behavior.

#. TTPs used against your Technology Platform(s)
#. TTPs used by Threat Actor(s) targeting your Industry
#. TTPs used by Software used maliciously against your Industry
#. TTPs used by Campaign(s) targeting your Industry

Throughout this section, we break down each type of observed behavior and demonstrate how to use the TTPs describing this behavior in your attack tree. We will continue to use AMPS in all examples.
Multiple technology platforms were identified in our attack tree. For the purposes of this paper, we will only be using observed TTPs related to the cloud platform, Azure, branch of the attack tree.
As we walk through this section and explain how to generate TTPs from each of the four types of observed behaviors above, we will start to compile a consolidated list of TTPs pertinent to branches of our tree (in this case the azure branch). These TTPs will be compiled in the form of ATT&CK Navigator layers. The figure below shows the process of stacking the multiple ATT&CK Navigator layers derived from each category of data. The information gathered during this section will also support scoring in the following section.

.. figure:: /Graphics/19.png
    :scale: 50%
    :align: right

|

The observed TTPs in these layers may not have been previously used to achieve the goal we are analyzing in our attack tree (user location data). This is expected. Often, intrusions go through your company to access your business partners or customers. Though your company, or others in your industry, may not have been the desired end target in these reported incidents, you were an intermediate target and the TTPs used in these “leap frog” intrusions against your industry or tech platform can be used to target you in the future. Thus, we include them in our observed TTP layers.

.. note::

    All ATT&CK Navigator Layer examples can be found within drop downs throughout the Evidence section. Each example will allow for download and opening within ATT&CK Navigator for editing.


Layer 1: Technology Platform TTPs
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Goal:** Compile a list of TTPs that have been used to target your tech platform.

To characterize the observed threats targeting your system, we recommend starting with techniques targeting your specific technology platform. This information will be used to prioritize threats in your attack tree later.
Types of observed CTI data varies by company depending on which commercial data you subscribe to or which public datasets you leverage. As a best practice, if the data is available, internally generated observed threat data targeting your network and technology platforms should be incorporated. For the purposes of our example, the fictitious team evaluating AMPS doesn’t pay for any CTI data and only had publicly available data at its disposal. A good starting place for any team regardless of budget is ATT&CK navigator. In this tool, there is an option to filter mobile, enterprise, or industrial control system matrix by technology platform. Our theory-based attack tree is already broken down into technology platform branches. Focus on generating observed TTPs one branch at a time. Navigator will generate an ATT&CK matrix with TTPs that have been observed targeting your technology platform in the wild. ATT&CK version 14.1 has the following platform filters: macOS, Windows, Linux, Azure AD, PRE, Containers, Office365, SaaS, Google Workspace, and IaaS. The Azure branch can be seen in the figure below. We recommend adding TTPs (or navigator layers) derived from your commercial data or data generated internally to this technology platform navigator layer. This additional data will help capture more observed TTPs used against your technology platform.

.. collapse:: Example Platform Layer

    **This ATT&CK Navigator view shows the TTPs linked to Azure AD. Throughout this evidence section, we will down-select off of these TTPs.**

    .. figure:: /Graphics/Platform_Layer.svg
        :scale: 75%
        :align: center

    .. raw:: html

        <p>
            <a class="btn btn-primary" target="_blank" href="https://mitre-attack.github.io/attack-navigator/#layerURL=https://center-for-threat-informed-defense.github.io/insider-threat-ttp-kb/heatmap_InT_2.09.json">
            <i class="fa fa-map-signs"></i> Open Layer in Navigator</a>

            <a class="btn btn-primary" target="_blank" href="..\heatmap_InT_2.09.json" download="heatmap_InT_2.09.json">
            <i class="fa fa-download"></i> Download Layer JSON</a>
        </p>

|

Layer 2: Threat Actor (TA) TTPs
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Goal:** Compile a list of TTPs that have been used by a threat group/s targeting your industry.

If time permits, we also recommend generating threat profiles to characterize the adversaries, or groups, that are likely to target your industry and therefore your system. This information will also help in prioritizing threats in your attack tree later.
To get started with threat actors that are relevant to your organization, consider any threat actors that are known to be a concern in the past, or have been mentioned recently as a concern to your organization. It is always a good idea to consider threat actors that have previously been a threat to your organization since they are known to you. Ask your stakeholders if they know of any TAs they are concerned with too.
The ATT&CK Groups knowledge base can be a good starting point for any team. The groups page (https://attack.mitre.org/groups/) gives an overview of all the TAs reported publicly. Many CTI venders have their own naming structure, MITRE Groups is an attempt at combining these TAs under a single naming convention. On this page, you can “CTL + F” to look for groups relevant to you. Some focus areas to search for might be location (ie. United States, Iran, China) or industry (ie. financial, government, retail), both searches help to narrow down threat actors important to your organization. Also be sure to keep an eye out for when these groups were active. Groups that have not been active in a recent timeframe might not be useful to your organization, but this is an internal decision that needs to be made based on your organization’s needs. Be sure to keep these dates in mind as they will affect the scoring in the next section.
A navigator layer exists on each Group’s page. Use this layer to generate a list of TTPs for each TA you identified. Below is an ATT&CK navigator example for FIN7 that highlights the TA’s TTPs in blue. This threat actor was chosen by searching “medical” on the ATT&CK Groups page which identified this group as previously targeting our industry’s “medical equipment.”

If you have more time, once you’ve finished using the ATT&CK Groups page, you should look at threat actors in the news that are potentially relevant to your industry. If your organization subscribes to commercial data, search that database or use Threat Intelligence Platforms available to you. An example of this can be found in Appendix A.  Another good starting point for teams on a budget is the APT Groups and Operations Google Sheet. This spreadsheet consists of list of threat actors by country and lists out the actor, other possible names associated with the group, operations associated, origin, toolset/malware utilized, a description of their motives/goals, and targeted industries.
Once you have a list of TAs compiled, we recommend checking each name against the APT Groups and Operations Google Sheet, since this spreadsheet contains community based information about threat actors and the various names attached to each group this allows so your organization the opportunity for further research into the group. Due to this being a living spreadsheet with various people making edits it allows for a more real-time approach in terms of updates that can be helpful to organizations focusing on a specific threat actor. Ultimately this resource is another opportunity to find more evidence based TTPs associated with the actor.
One final opensource resource is the Thai CERT database. This database allows you to search for threat actors by country, sector, motivation, or key word. Once you’ve identified TA’s of concern, compare these to the aliases on the ATT&CK Groups page (CTL + F search for name) and consider using any resulting group’s Navigator layer.

.. collapse:: Example Threat Actor Layer

    **This ATT&CK Navigator view shows the TTPs linked to Azure AD. Throughout this evidence section, we will down-select off of these TTPs.**

    .. figure:: /Graphics/20.svg
        :scale: 75%
        :align: center

    .. raw:: html


        <p>
            <a class="btn btn-primary" target="_blank" href="https://mitre-attack.github.io/attack-navigator/#layerURL=https://center-for-threat-informed-defense.github.io/insider-threat-ttp-kb/heatmap_InT_2.09.json">
            <i class="fa fa-map-signs"></i> Open Layer in Navigator</a>

            <a class="btn btn-primary" target="_blank" href="..\heatmap_InT_2.09.json" download="heatmap_InT_2.09.json">
            <i class="fa fa-download"></i> Download Layer JSON</a>
        </p>

|

Layer 3: Malicious Software TTPs
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
**Goal:** Compile a list of TTPs that have been used for the execution of publicly available (malicious) tools.

The next step will follow a similar process as the steps above. To start, an organization should always compile internal data first. This can be done by utilizing datasets from paid tools or ones that were publicly compiled, as well as any previous threats the company has seen. By starting with the known and building on the new data, it allows for a more exhaustive list of TTPs while ensuring company specific data is considered.
After reviewing internal and commercial data, use the ATT&CK software page, similarly to how we used it for the TA layer. In this scenario we will be using it to build a list of TTPs used by malicious software targeting your specific technology platform. This will be done by accessing https://attack.mitre.org/software/ and using ‘CTL + F’ to searching for your technology platform.
Our example relies on Azure which results in two findings of software, AADInternals and ROADTools. For the sake of this example, the team will focus on ROADTools. We recommend include all software pertaining to your platform, or just specific ones you find most applicable, this will be a decision you will have to make based on your needs and time. During this step, remember that ATT&CK software is not just compromised of malicious software, but also commercial, open-source, built-in, or publicly available software that could be used by a defender, pen tester, red teamer, or an adversary maliciously.  Each Software page comes with a Navigator layer. The ROADTools ATT&CK navigator layer can be seen below in red.

.. collapse:: Example Software Layer

    **This ATT&CK Navigator view shows the TTPs linked to Azure AD. Throughout this evidence section, we will down-select off of these TTPs.**

    .. figure:: /Graphics/21.svg
        :scale: 75%
        :align: center

    .. raw:: html


        <p>
            <a class="btn btn-primary" target="_blank" href="https://mitre-attack.github.io/attack-navigator/#layerURL=https://center-for-threat-informed-defense.github.io/insider-threat-ttp-kb/heatmap_InT_2.09.json">
            <i class="fa fa-map-signs"></i> Open Layer in Navigator</a>

            <a class="btn btn-primary" target="_blank" href="..\heatmap_InT_2.09.json" download="heatmap_InT_2.09.json">
            <i class="fa fa-download"></i> Download Layer JSON</a>
        </p>

|

Layer 4: Campaign TTPs
~~~~~~~~~~~~~~~~~~~~~~

**Goal:** Compile a list of TTPs that have been used in a campaign targeting your industry.

To provide a more detailed picture, if an organization has the time, it is recommended they research campaigns that might be applicable to them. This can be done in various ways similar to the previous layers. First, if there are any campaigns recently reported on that are of concern to your organization, these should be included. It might also make sense to include any data from previous campaigns that targeted your organization as well as data from tools used internally. Once this data has been considered and added, the team should use the ATT&CK campaigns page for further research. Focus on campaigns targeting your specific industry. This can be searched by using ‘CTL + F’ on https://attack.mitre.org/campaigns/. During this step, be cognizant of the timing of these campaigns. We do not want to be looking at campaigns that are too old to be useful. Only your organization can know which campaigns they find useful but keep these dates in mind as they will affect the scoring in the next section.
Continuing with an example applicable to the AMPS device, we focused on one of these campaigns related to healthcare, specifically C0010. In many cases, this campaign might be considered not recent enough to be relevant, but for the sake of this example we will be using it regardless of the reported date being in 2022. The ATT&CK Navigator layer below highlights the TTPs relevant to this campaign in yellow.

.. collapse:: Example Campaign Layer

    **This ATT&CK Navigator view shows the TTPs linked to Azure AD. Throughout this evidence section, we will down-select off of these TTPs.**

    .. figure:: /Graphics/22.svg
        :scale: 75%
        :align: center
    .. raw:: html


        <p>
            <a class="btn btn-primary" target="_blank" href="https://mitre-attack.github.io/attack-navigator/#layerURL=https://center-for-threat-informed-defense.github.io/insider-threat-ttp-kb/heatmap_InT_2.09.json">
            <i class="fa fa-map-signs"></i> Open Layer in Navigator</a>

            <a class="btn btn-primary" target="_blank" href="..\heatmap_InT_2.09.json" download="heatmap_InT_2.09.json">
            <i class="fa fa-download"></i> Download Layer JSON</a>
        </p>

|

.. collapse:: Evidence Layer Video Walkthrough

    .. raw:: html

        <iframe width="560" height="315" src="https://www.youtube.com/embed/h_BC6QMWDbA?si=Abpy35U4SYKMYUeE" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>


Compile All CTI Layers and Compare to Theory-Base Attack Tree
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Goal:** Compile list of TTPs that your system will most likely face

Right now, you have a list of TTPs, in the form of ATT&CK Navigator Layers, that have been known to be used against technology platforms in your tree. Take those lists and overlap them using Navigator. This yields a longer list of all TTPs that could be relevant to your attack tree. The overlap between layers can provide some insight for prioritization. The example below shows a combination of all layers. The blue TTPs will show those used by threat actors targeting your industry, the red TTPs signify the TTPs used by malicious software targeting your industry, the yellow highlights the TTPs used by campaigns targeting your industry, and grey shows any overlap between multiple factors.

.. collapse:: Example Evidence Combined Layer

    **This ATT&CK Navigator view shows the TTPs linked to Azure AD. Throughout this evidence section, we will down-select off of these TTPs.**

    .. figure:: /Graphics/23.svg
        :scale: 75%
        :align: center

    .. raw:: html


        <p>
            <a class="btn btn-primary" target="_blank" href="https://mitre-attack.github.io/attack-navigator/#layerURL=https://center-for-threat-informed-defense.github.io/insider-threat-ttp-kb/heatmap_InT_2.09.json">
            <i class="fa fa-map-signs"></i> Open Layer in Navigator</a>

            <a class="btn btn-primary" target="_blank" href="..\heatmap_InT_2.09.json" download="heatmap_InT_2.09.json">
            <i class="fa fa-download"></i> Download Layer JSON</a>
        </p>

|

Compare these TTPs to those in your theory-based attack tree. Since these TTPs are all related to the Azure branch of the attack tree, we will focus there. In practice, you would make one overlay for each technology platform branch of your tree. To apply this to our current example we are going to take our attack tree branch centered around Azure and map the steps back to ATT&CK techniques, as seen in the navigator layer below.

.. collapse:: Example Theory Layer

    **This ATT&CK Navigator view shows the TTPs linked to Azure AD. Throughout this evidence section, we will down-select off of these TTPs.**

    .. figure:: /Graphics/24.svg
        :scale: 75%
        :align: center

    .. raw:: html


        <p>
            <a class="btn btn-primary" target="_blank" href="https://mitre-attack.github.io/attack-navigator/#layerURL=https://center-for-threat-informed-defense.github.io/insider-threat-ttp-kb/heatmap_InT_2.09.json">
            <i class="fa fa-map-signs"></i> Open Layer in Navigator</a>

            <a class="btn btn-primary" target="_blank" href="..\heatmap_InT_2.09.json" download="heatmap_InT_2.09.json">
            <i class="fa fa-download"></i> Download Layer JSON</a>
        </p>

|

.. collapse:: Evidence and Theory Combined Video Walkthrough

    .. raw:: html

        <iframe width="560" height="315" src="https://www.youtube.com/embed/h_BC6QMWDbA?si=Abpy35U4SYKMYUeE" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>


This navigator layer is now placed on top of our overall evidence layer above and we look at the TTPs that the two have in common, which are highlighted in orange. Then what we want to do is look at the techniques that are not overlapping to see if they have a place in our branch are represented in grey.

.. collapse:: Example Theory Evidence Overlay Layer

    **This ATT&CK Navigator view shows the TTPs linked to Azure AD. Throughout this evidence section, we will down-select off of these TTPs.**

    .. figure:: /Graphics/25.svg
        :scale: 75%
        :align: center

    .. raw:: html

        <p>
            <a class="btn btn-primary" target="_blank" href="https://mitre-attack.github.io/attack-navigator/#layerURL=https://center-for-threat-informed-defense.github.io/insider-threat-ttp-kb/heatmap_InT_2.09.json">
            <i class="fa fa-map-signs"></i> Open Layer in Navigator</a>

            <a class="btn btn-primary" target="_blank" href="..\heatmap_InT_2.09.json" download="heatmap_InT_2.09.json">
            <i class="fa fa-download"></i> Download Layer JSON</a>
        </p>

|

The list we obtain from the last evidence and theory layer is where we will focus our efforts. While the other combined list can, without a doubt, be extremely helpful we want to focus on the TTPs we believe are applicable to our system. This is the list of TTPs we will use moving into the next section.



Scoring the Catalogue of Threats to Your System
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. note::

    Scoring is not a mandatory step, however it can provide great context for priorization.

This step lets us calculate the threat associated with specific attack vectors and TTPs. The end goal of this step is to prioritize which threats we mitigate in Question 3.

.. figure:: /Graphics/26.png
    :scale: 75%
    :align: left

Revisiting the ideas presented at the introduction to Question 2, we can organize identified TTPs into different priority categories depending on the strength of their individual theory and evidence. These categories are not meant to be a strict numerical ranking – rather, they should be used as an aid to help prioritize your time and effort while evaluating mitigations and countermeasures.

Given a particular TTP identified by your overlay of theory and evidence, consider some of the following factors that will help guide your prioritization of TTP data. Note that this list is non-exhaustive, and there may be other factors specific to your use case that you wish to incorporate.

.. list-table::
   :widths: 50 50
   :header-rows: 1

   * - Factors indicating stronger Theory
     - Factors indicating stronger Evidence

   * - TTP has been hypothesized in a research paper
     - TTP has been used by a threat group targeting your industry

   * - TTP has been demonstrated in a technical lab
     - TTP has public reports of execution using publicly available (malicious) tools

   * - TTP has known, publicly available tools for execution
     - TTP has been used in a campaign targeting your industry within the last 90 days

   * - TTP has associated vulnerabilities (CVEs) applicable to your tech platform(s)
     - TTP has been used in a campaign targeting a tech platform you use within the last 90 days

   * - TTP is associated with accessing a critical cyber asset
     - TTP is associated with a vulnerability/CVE disclosed within the past 30 days

   * - TTP is associated with a critical system choke point identified in system diagrams
     - TTP has been used against your tech platform in the past

   * - TTP is associated with a critical system choke point identified in threat analysis
     -

The more factors that apply for either theory or evidence, the further you move in the table right or down respectively. The simplest form of this analysis assigns an equal value to all factors (i.e., a weight of 1). However, you may find that some factors should be treated with more importance to suit your prioritization needs. For example, you may give TTPs associated with external system boundaries (i.e., external network connections) extra weight to prioritize developing mitigations for system entry points.

.. figure:: /Graphics/27.png
    :scale: 80%
    :align: right

The result will manifest like the diagram shown. TTPs are assigned a theory-evidence score, which places them at a point in the table. Thresholds can be individually adjusted for both theory and evidence to determine how large or small to make the sectors in the table. For example, in industries that utilize newer or more specialized technology, there may be less available evidence to consider in your threat overlay. Consequently, you may choose to weigh individual pieces of evidence higher than other industries.

Example scoring
^^^^^^^^^^^^^^^

Consider TTP: **T1011.001** – Exfiltration Over Other Network Medium: Exfiltration Over Bluetooth
Assume the adversarial goal in this case is to steal sensitive patient data. One avenue to do so would be to go directly to the source – the AMPS device itself.
T1011.001 describes activity where “Adversaries may attempt to exfiltrate data over Bluetooth rather than the command-and-control channel. If the command-and-control network is a wired Internet connection, an adversary may opt to exfiltrate data using a Bluetooth communication channel.” The AMPS device has been designed with Bluetooth in mind, as it needs to pair with a phone.
Several Bluetooth vulnerabilities have been documented in literature, but we will choose to focus on one named SweynTooth . SweynTooth is a collection of vulnerabilities in certain Bluetooth Low Energy (BLE) chipsets, with a range of impacts ranging from crashes to security bypass. Perusing the website dedicated to this vulnerability, we can come to the following conclusions on the strength of **theory factors:**

* The TTP has been hypothesized in the writeup (beyond hypothesized, in fact)
*	The TTP has been demonstrated (there is proof of concept code against multiple devices)
*	The TTP has known tools for execution (there is proof of concept code)
*	SweynTooth is a Bluetooth vulnerability and therefore applies to this TTP
*	Patient data is a critical cyber asset for this device (which the TTP directly affects)
*	The Bluetooth connection between the AMPS device and the patient phone is a link that crosses a trust boundary on the DFD (and is therefore a critical link)
*	This TTP is present in attack tree branches that directly access the device, but there are other ways to get patient data (e.g. compromising their online account). Ergo, this may or may not be considered a choke point from a threat analysis standpoint.

On the theory side, the above culminates in **6/7 factors** applying here, indicating **strong supporting theory** for this TTP.
With respect to evidence, we see a much different story manifesting:

*	Threat groups operating against the healthcare industry have generally not been targeting Bluetooth (caveat - at the time of writing)
*	There **are** several reports of Bluetooth exploits being leveraged in the wild
*	Similar to the first point, there are very few **campaigns** leveraging Bluetooth in the wild, and by extension, very few campaigns targeting this industry and tech platform
*	While Bluetooth is generally regarded as insecure, there have not been any major vulnerability disclosures over the past 30 days (at the time of this writing)

On the evidence side, the above culminates in **1/5 factors** applying here, indicating **little or weak supporting evidence**. Together, the theory and evidence place this TTP toward the upper-right on the figure, which gives this TTP a medium priority under normal weighting.

.. figure:: /Graphics/28.png
    :scale: 75%
    :align: right

To reiterate, this step is not meant to produce a definitive first-to-last ranking of TTPs – rather, it serves to quickly prioritize where to focus your efforts when considering countermeasures and mitigations in Question 3. Therefore, once you are done sorting TTPs, sort the boxes, rather than the individual TTPs themselves, for priority. Returning to the example figure, this would result in the following prioritization scheme.
Depending on your priorities, you may choose to sort the categories of TTPs differently if your concerns align more with theory or with evidence. i.e., you may choose to prioritize the center box higher than the top right box if you are more worried about strength of evidence than strength of theory.

Example Scoring TTPs within AMPS’s Azure Attack Tree Branch
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The following table summarizes the TTPs identified during the Theory and Evidence activities presented earlier in this section. We’ve sorted the table into three columns – Theory, Evidence, and both, to track which activity each TTP was derived from.
To keep rest of this example concise, we have elected to only score the TTPs listed under the “Theory and Evidence” column. However, scoring can (and should) be applied to all identified TTPs.

*Theory factor scoring*

#. TTP has been hypothesized in research paper(s)
#. TTP has been technically demonstrated in a published setting (lab, presentation, etc.)
#. TTP has known, publicly available tools for execution
#. TTP has associated vulnerabilities (CVEs) applicable to your tech platform(s)
#. TTP is associated with accessing a critical cyber asset in your system
#. TTP is associated with a critical system choke point identified in system diagrams
#. TTP is associated with a critical system choke point identified in threat analysis

Some notes on the above:

*	Datapoints for Factor 1 encompass TTPs that are theoretically possible but have yet to be demonstrated. Threats were primarily identified from academic publications and industry publications.
*	Sources for Factor 2 often pull from academic and industry publications, but these exploits have been corroborated by testing. Presentations by security professionals at conferences and online are another valid source for this information.
*	Satisfying Factor 3 entails tracking down sources that link the identified TTP with existing tools. For this example, azure red teaming reports were a key source in identifying known tools associated with specific TTPs.
*	Entries for Factor 4 were determined by searching through existing CVE repositories for CVEs specifically tied to Azure and Microsoft products.
*	Entries for Factor 5 were identified by reviewing our attack tree and determining whether a TTP directly targeted critical assets.
*	Entries for Factor 6 were identified by examining our original DFD. Chokepoints or interests that represent key information bottlenecks within the system were identified.
*	Entries for Factor 7 were identified in much the same way as Factor 6, but in this case chokepoints were identified within the system attack tree as lynch-pins within a larger adversary campaign. 

*Evidence factor scoring*

#. TTP has been used by a threat group targeting your industry
#. TTP has public reports of execution using publicly available (malicious) tools
#. TTP has been used in a campaign targeting your industry within the last 90 days
#. TTP has been used in a campaign targeting a tech platform you use within the last 90 days
#. TTP is associated with a vulnerability/CVE disclosed within the past 30 days
#. TTP has documentation of previous use against your tech platform.

Some notes on the above:

*	Entries for Factor 1 were determined by searching the groups page on the ATT&CK website. Relevant groups were identified by searching for the keyword “healthcare”, where their TTP lists were cross-referenced with entries in the table.
*	Entries for Factor 2 were determined by searching the relevant TTP entries in ATT&CK for related software artifacts applicable to Azure.
*	Entries for Factors 3 and 4 were determined by searching were determined by searching campaigns on the ATT&CK website targeting Azure. At the time of writing, there are no known campaigns occurring within the last 90 days against Azure. While there have been campaigns targeting Healthcare in the past, they have largely focus on Denial of Service and Ransomware outcomes , which fall outside of the scope of the TTPs we are evaluating.
*	Entries for Factor 5 were determined by a keyword search for “Azure” on the CVE website. While there are multiple Azure CVEs at the time of writing, none are related to the TTPs.
*	Entries for Factor 6 were taken directly from the ATT&CK Navigator Overlay presented in section [xxx] detailing TTPs relevant to the Azure platform.

It is important to note that factors 3, 4, and 5 are all considered with restricted time windows, as allowing all instances of a TTP may lead to over-scoring based on ‘stale’ information. I.e., a campaign that occurred two years prior, while informational, does not carry the same urgency as a campaign actively happening within the last month.
After scoring, the TTPs can be placed on a heatmap overlay, then sorted by grouping from highest to lowest priority. The following figure illustrates the outcome of this process. Points on the heatmap with multiple listings represent TTPs that achieved the same score. Note, that in this example, T1556 and T1059.001 could have their positions exchanged, depending on if your priorities align closer to Theory or Evidence factors.

.. figure:: /Graphics/29.png
    :scale: 100%
    :align: center

As a reminder, this example only scored TTPs that appeared during both Theory and Evidence investigation. When creating a full threat model, it is important to consider all TTPs for completeness.
