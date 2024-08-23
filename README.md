<p align="center">
  <img src="https://summerofcode.withgoogle.com/assets/media/logo.svg"/>
</p>

# Google Summer of Code 2024 with LibreCube - Open Source Space and Earth Exploration

![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54) ![NumPy](https://img.shields.io/badge/numpy-%23013243.svg?style=for-the-badge&logo=numpy&logoColor=white) ![GitLab](https://img.shields.io/badge/gitlab-%23181717.svg?style=for-the-badge&logo=gitlab&logoColor=white)

## Hi, I'm Faith 🖖 

<img align="left" alt="Faith Tng" width="25px" style="object-fit:cover" src="https://www.svgrepo.com/show/350417/user-circle.svg"/>
<p style="padding-left:40px;">Faith Tng</p>

<a href="mailto:faithasastring@gmail.com" width="1px">
    <img align="left" alt="Faith Tng" width="25px" src="https://img.icons8.com/?size=256&id=P7UIlhbpWzZm&format=png"/>
    <p style="padding-left:40px;">faithasastring@gmail.com</p>
</a>

<a href="https://gitlab.com/faithinspace" width="1px">
    <img align="left" alt="Faith Tng" width="25px" src="https://raw.githubusercontent.com/gauravghongde/social-icons/9d939e1c5b7ea4a24ac39c3e4631970c0aa1b920/SVG/Color/Github.svg"/>
    <p style="padding-left:40px;">https://gitlab.com/faithinspace</p>
</a>

<a href="https://www.linkedin.com/in/faithtng" width="1px">
    <img align="left" alt="Faith Tng" width="25px" src="https://raw.githubusercontent.com/gauravghongde/social-icons/9d939e1c5b7ea4a24ac39c3e4631970c0aa1b920/SVG/Color/LinkedIN.svg"/>
    <p style="padding-left:40px;">https://linkedin.com/in/FaithTng</p>
</a>

## Mentors

* [Artur Scholz](mailto:artur.scholz@librecube.org ) - Founder of LibreCube and primary mentor
* [Shayan Majumder](mailto:shayan.majumder2@gmail.com) - GSoc alumni and mentor

## This is the summary of the work I did for the USLP project with the [LibreCube](https://librecube.org/) organization, as a [Google Summer of Code](https://opensource.googleblog.com/2024/05/google-summer-of-code-2024-accepted-contributors-announced.html) contributor.

## Project Description

![CCSDS](https://public.ccsds.org/outreach/images/logos/CCSDS%20Logo%20Letters%20Only/4-Color/ccsdslogo-letters-4color-gradthumb.png)
- Title: Unified Space Data Link Protocol
- Organization: LibreCube - Open Source Space and Earth Technologies
- App repository can be found here: [Python USLP](https://gitlab.com/librecube/prototypes/python-uslp)

<div>
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;The Unified Space Data Link Protocol (USLP) is a relatively new space protocol standard from the Consultative Committee for Space Data Systems (CCSDS) that aims to unify the protocols used for telecommand uplink and telemetry downlink between ground and space assets. In this project, an open-access Python prototype implementation of USLP was developed to demonstrate its benefits within the context of the LibreCube 1U rover platform. Using this unified format, the prototype facilitated the transmission of frames between different endpoints.
</div>

## Preface

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Coming into the project, my Python skills were intermediate and I challenged myself by taking on a project that was rated "Hard". I was motivated by the opportunity to jump into the deep end in order to accelerate my technical skills, while working on something relatively new within the space domain, which is my passion that I have relentlessly pursued for the last 7 years. This was also my first proper development experience outside of university / adhoc projects.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;A lot of heavy upfront research was necessary in the early days, as the USLP is a new standard with documentation that [spans almost 200 pages](https://public.ccsds.org/Pubs/732x1b3.pdf). Another main reference point was the USLP informational report, also affectionately known as "[The Green Book](https://public.ccsds.org/Pubs/700x1g1.pdf)", alongside sixteen other references and appendices. The intricacies within each individual aspect of the project definitely mattered in the implementation; While implementing a new standard can be exciting, the rabbit hole of details can be slightly overwhelming for new developers.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;As the program is remote and largely self-structured, a lot of self-study was required to figure out how to approach the implementation of complicated tasks and readjusting from the feedback of mentors after implementation. Overall, the learning curve was steep but manageable in hindsight. I could have done more if I had not been juggling multiple other responsibilities.

## Summary

In this project, I worked on the development of the USLP Transfer Frame as per the CCSDS 732.1-B-3 [(June 2024 update)](https://https://public.ccsds.org/Pubs/732x1b3.pdf) standard.

- I created and updated UDP packet transfers to accomodate for USLP Transfer Frames in packet form through python sockets. The architecture was created for UDP packets that are transfered between a client sender and a remote sender with a sink as a receiver. This was intended to demonstrate knowledge and understanding of how these packets must be sent, and how should I implement testing of these Transfer Frames even through higher level services that apply modifications to said Transfer Frames.

- The beginning of development warranted heavy refactoring and testing of the Transfer Frame Header that was already present in the repository. This was a major step forward for me in understanding bitwise operations and honing in on fixing the Transfer Frame Header implementation to account for every bit up till the Transfer Frame Data Field.

- The intricate understanding of transfer frame addressing came next. Here, I focused on creating constants that can be used as a means of validation and implementation of services later down the line as the Transfer Frame goes through all of the multiplexing/demultiplexing and through the period of time they go through commutators/decommutators.

- One of the last steps of the project required me to use Transfer Frames to display an idle type of Transfer Frame Data being sent. This inquired the implementation of Transfer Frame Zone Construction rules decoding. Following that, a 32 cell Linear Feedback Shift Register was required to create an infinite amount of different data to be displayed in these idle packets.
- These changes needed a lot of adaptation of the UDP transport protocol to accomodate for testing via the example files. A theoretical client was implemented but required adapting, and a new sink was implemented to show these Transfer Frames being sent and received (decoded).

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;At the end of the project, the demo of the usage of these Transfer Frames by the new client and sink was verified and passed to meet the timeline (though there might be a bug in the implementation of the Transfer Frame Data Field). This finalized the implementation of Non-Truncated Transfer Frames to allow for further implementation of services on top of the implementation. Future development is also impacted by the structure I added though GitLab issues to the project.

## Contributions

- The stepping stone for the CCSDS implementation of USLP packets development branch was created by using bit interpretations of USLP transfer frames:
  - [Development branch](https://gitlab.com/librecube/prototypes/python-uslp/-/tree/develop) 

### Commits and code changes

- [x] [Added examples for UDP packet transfer (source to sink):](https://gitlab.com/librecube/prototypes/python-uslp/-/commit/aa6f22916702d9cd76e888911f79c0c31b1e2942)
    - Using python implemented sockets, I created mock transfers of packets between a client and remote with an example sink to see all packets sent by both.
    - Using the UdpTransport layer existent on the project, I shown the understanding of packets and the OSI model of where the CCSDS documentation wants to implement the services.
    - Worked on the placeholder USLP packet transfer examples and created comments to help with development of the reusable Transfer Frame Header usable by all types of future Transfer Frames, truncated or not.
- [x] [Fixed encoding and decoding, added comments](https://gitlab.com/librecube/prototypes/python-uslp/-/commit/a250bac7662a483c3c55547ebb9f5305172a87bc)
    - Adapted encoding and decoding of the Transfer Frame Header to be on par with CCSDS 732.1-B-3 documentation as per their June update. Added comments about future things to do for bookkeeping.
    - Added validators to make sure there are checks for the sizes of each field of the Transfer Frame Header.
- [x] [Added getters for addressing of transfer frames](https://gitlab.com/librecube/prototypes/python-uslp/-/commit/855412f6907a5416da3d5293da7abb7f6cf0c097)
    - Added getters for remembering what different types of transfer frame addressing (CCSDS 732.1-B-3 2.1.3) would be possible and to be used for future iterations.
 - [x] [WIP: Refactored the USLP frame and accommodated for future changes](https://gitlab.com/librecube/prototypes/python-uslp/-/commit/926b1fd0459127de265a380b3ef506ed2902d51d)
    - Refactored the USLP frame encoding and decoding.
    - Added functionality for the Transfer Frame Data Field, Operational Control Field, and Frame Error Control Field.
    - Added a plethora of constants to be later implemented in the CCSDS services for Transfer Frames.
    - Added a mockup of Transfer Frame Data Zone decoding.
 - [x] [Update for demo issues](https://gitlab.com/librecube/prototypes/python-uslp/-/commit/948e687322b0795cc93400cbe5e037da40ef87db)
    - Updated the encode/decode with further bugfixing.
    - Added the 32 cell Linear Feedback Shift Register(LFSR) as per Annex H of CCSDS 732.1-B-3, using the first option, fibonacci, as a basis for the implementation.
    - Added a new sink (mcf_ground.py) and the related logic to visualize the newly implemented frames.
    - Modified the existing UDP transport file to work with the new changes in Transfer Frame addressing (MCID).

## Future work

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Currently, this system architecture enables a faster feature implementation, in spite of the steep learning curve this project creates through complex documents and detailed standards. I would recommend that the next steps would be to move towards adapting all of the features of the different services, on top of the already implemented non-truncated USLP transfer frames. Subsequent changes can easily be implemented, tested, and iterated in a circular fashion by using the adapted UDP transport frames found in the example files.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;To help future developers, I created issues on the scrum board that proposed a hierarchical order of events, in order to finish implementing the CCSDS standard for USLP.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Although I trust that the project will be in great hands, I intend on working on it past the summer project to see it flourish and be properly implemented, perhaps on a real use case.

## Acknowledgements
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;I would like to express my gratitude to Google, the LibreCube organisation and my mentors Artur and Shayan for the opportunity in being trusted with a project that is relatively novel and challenging. Shoutout especially to Artur for his consistently timely feedback, even through the late hours of the night. I especially appreciated that LibreCube also organised community events to meet other developers through icebreakers and online games, and I now have a deeper interest and respect for open source technologies. Looking forward to staying in touch with the LibreCube and Google Developer community!
