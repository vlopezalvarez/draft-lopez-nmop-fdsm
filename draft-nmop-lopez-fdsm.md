---
title: "Formal definition of state machines"
abbrev: "Formal definition of state machines"
category: info

docname: draft-nmop-lopez-fdsm-latest
submissiontype: IETF  # also: "independent", "editorial", "IAB", or "IRTF"
number:
date:
consensus: true
v: 3
# area: "Operations and Management"
# workgroup: "Network Management Operations"
keyword:
 - state machines
venue:
#  group: "Network Management Operations"
#  type: "Working Group"
#  mail: "nmop@ietf.org"
#  arch: "https://mailarchive.ietf.org/arch/browse/nmop/"
  github: "vlopezalvarez/draft-lopez-nmop-fdsm"
  latest: "https://vlopezalvarez.github.io/draft-lopez-nmop-fdsm/draft-nmop-lopez-fdsm.html"

author:
 -
    fullname: Diego R. Lopez
    organization: Telefonica
    email: "diego.r.lopez@telefonica.com"
 -
    fullname: Victor Lopez
    organization: Nokia
    email: "victor.lopez@nokia.com"

normative:

informative:


--- abstract

This document defines a formal approach for representing state machines in a standardized manner. It specifies the structure and methodology for modeling not just states, but also transitions, and events, aiming to create a consistent framework for use across diverse domains. The goal is to improve clarity, interoperability, and reusability of state machine definitions.

--- middle

# Introduction

State machines play a fundamental role in the formal description of network protocols, and many IETF RFCs have employed them to define protocol operations. These state machines serve to illustrate how a system transitions between various states, helping to clarify complex behaviors and enabling systems collaboration. By using state machines, RFCs can effectively describe how protocols handle different operational scenarios, such as error handling, session management, or negotiation processes.


However, there is no standardized method for describing state machines across RFCs. The current practice varies, with state machines often presented through informal diagrams or simple enumerations of states and transitions. This lack of consistency introduces ambiguity, making it harder to interpret or compare the behavior of state machines across different protocols. Furthermore, the absence of a formal structure makes it difficult interoperability, forcing developers to read diagrams leading into misinterpretation.

There has been some previous work in IETF, {{?RFC2360}} proposes three methods to represent state machines:

* State Transition Diagrams: Represent protocol states as boxes connected by arcs, with transitions labeled by the events that trigger them and actions noted in parentheses. This method is ideal for simple visualizations, limited by ASCII format constraints.

+ State Transition Tables: Display events vertically and states horizontally, with transitions represented as "action/new state" pairs. Multiple actions are separated by commas, and this format efficiently summarizes complex transitions. The preferred approach lists the new state after the action (as seen in {{!RFC1661}}).

- Time Line Diagrams: Depict interactions between two machines, with states shown along the outside and actions triggering transitions within the time line. Time flows downward, showing state changes as events occur in sequence.

Another attemp was the discussion in IETF 86 in the Finite State Machine group. A summary of the conclusions from the Finite State Machine meeting at IETF 68 based on the minutes:

* Need for Formal State Machine Language: There was a general consensus that a formal state machine language would be beneficial, especially for professional protocol developers and for use in RFCs. However, it should not be a mandatory requirement for all IETF specifications, as this could place unnecessary burdens on open-source or hobbyist developers.

+ Existing Tools vs. New Solutions: Some attendees, such as Aaron Silverton, suggested adopting existing formal languages like ITU-T's SDL or UML, while others, including Stephane Bortzmeyer, advocated for developing a simpler, IETF-specific tool like Cosmogol. It was recognized that existing tools can be complex, and a balance between simplicity and expressiveness would be important.

+ Experimentation and Future Steps: There was agreement that an experiment with a formal state machine language, like Cosmogol, should be conducted to validate the approach rather than immediately focusing on choosing or developing a specific language. The importance of simplicity and community adoption was highlighted, and there was no immediate decision to form a formal working group, with the suggestion to continue discussions on the mailing list.

- The overall takeaway was that while formalizing state machine descriptions is seen as valuable, the IETF should proceed cautiously to avoid unnecessary complexity and ensure broad community support.

Finally, {{!I-D.draft-sambo-netmod-yang-fsm}} introduces a formal method for defining finite state machines (FSMs) within YANG models. The work extended the YANG data modeling language by allowing protocol state machines to be formally represented and integrated into network management and configuration systems.

Authors believe that there is a need for a formal definition of state machines that goes beyond mere enumeration. A formal approach would not only provide a clear representation of states but would also define transitions, events triggering transitions, and how condittions transitioning between different states. Such a standardized framework would improve interoperability and understanding, allowing for more precise and reusable state machine descriptions in IETF specifications.


## Requirements Language

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as described in  {{!RFC2119}}, {{!RFC8174}} when, and only when, they appear in all capitals, as shown here.


# Use Cases

## Code generation

YANG models are widely used to describe data structures and operations in a machine-readable format, enabling the automatic generation of client code for application integration. This significantly reduces the development effort by providing ready-made, standardized client libraries for interacting with various systems. However, when state machines are not formally described within these models, this advantage is diminished. In current practice, state machines are often represented informally through text, diagrams, or enumerations.

This situation forces to have human interpretation to understand the transitions and behaviors, and manual coding to reflect them in software. The absence of a formal definition for state machines breaks the automation pipeline, making it impossible to automatically generate code that handles state transitions. A formalized state machine definition would preserve the value of autogeneration, ensuring that the system behaviors, as well as data structures, can be automatically translated into executable code.

## API benchmarking

System and network operators often request support for YANG models in API development, as these models enable better management and interaction with network elements through standardized APIs. One key aspect of API design is ensuring that the system’s stateful behaviors, such as session management or configuration operations, are accurately modeled and tested.

A formal description of state machines would allow for automated testing of API transitions between states. Instead of manually verifying how an API responds to various state changes, a formal model could be used to automatically generate tests that verify the correct implementation of transitions. This would not only improve the efficiency of API development and benchmarking but also ensure more robust implementations by reducing the chances of human error during manual test creation.


# Security Considerations

TODO Security


# IANA Considerations

This document has no IANA actions.


--- back

# Acknowledgments
{:numbered="false"}

TODO acknowledge.
