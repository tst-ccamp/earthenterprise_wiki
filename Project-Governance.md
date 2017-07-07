# Project Governance Model

# Roles & Responsibilities

In order to have a smoothly running project, formal roles with corresponding responsibilities are established.  A member of the community may assume multiple roles, as summarized in the table below:

<table>
  <tr>
    <td>Public Access</td>
    <td>Collaborator - Read access</td>
    <td>Collaborator - Write access</td>
    <td>Owner</td>
  </tr>
  <tr>
    <td>

- Read access
- download
- view history
-  create contributions
- Request modifications on a change
- upload changes for approval
- view
- add comments to existing issues
- file new issues
- view issues</td>
    <td>
- be assigned as reviewer
- submit a review
- be assigned an issue</td>
    <td>
- Write access
- create releases
- approve and merge changes
- change reviewer(s)
- change issue status
- edit issue labels
- edit roadmap (milestones)

</td>
    <td>

- Grants Read/Write access
- Configure GitHub repo
- Configure OpenGEE website

</td>
    
</table>


## Public Access

Any person who wishes to use Google Earth Enterprise can view the repository online. A person with Public Access has basic access to view the source code and history. In addition, they may create issues for questions and request new features  as well as upload code patches for approval. Common activities for a person with Public Access include:

* Uploading changes for approval

* Filing new issues

* Updating existing bugs with comments

* Writing/enhancing documentation and tutorials

* Participating in the community forums

* Advocating for use of the project

**How to become one:** Find the Google Earth Enterprise repository on GitHub

NOTE: before a developer’s first patch is put into the repository they must sign a [Contributor License Agreement](https://cla.github.com/) or assignment agreement. The patch can be submitted and discussed but it can’t actually be committed to the repository without signed paperwork.

## Collaborator - Read Access

Collaborators with Read Access are granted more privileges within the project than those with Public Access. In general, these collaborators are those who have an interest in the project and want to contribute on a more regular basis. Read Access Collaborators can request specific issues to work and will have the issue assigned to them in Git. In addition, they can be assigned as a code reviewer for a specific issue. Collaborators who continue to engage with the project and its community will often find themselves becoming more and more involved. Such users may then go on to become a Collaborator with Write Access, as documented below.

**How to become one:** Anyone who wants to work a specific issue or code review can request Read Access by asking in GitHub or in the GEE Slack channel.

## Collaborator - Write Access

Collaborators with Write Access are developers who have shown dedication to the project, high technical prowess and the ability to work well with the community. In particular, these collaborators formally decide on whether patches are entered into the main code repository and merge those requests. They may also modify the issues in a Milestone and give labels to Issues in the backlog. These collaborators are expected to be active in discussing issues on Slack or GitHub and help resolve basic technical questions from the community. 

**How to become one:** Show proficiency in coding and resolving issues. A Collaborator can then request for Write Access and then it will be up to the discretion of the other collaborators and project owner.

## Owner

There is a single Owner to the Earth Enterprise repository who has administrator rights over the project. The Owner grants Read or Write access to Collaborators and remove access if there is a need. Further, the Owner can configure the repository in GitHub and manage the settings for the OpenGEE.org website.

## Developer Guide

Every individual has their own preferences for code style and formatting. However, in an effort to standardize the codebase, the OpenGEE project will create a coding standard so that every developer can create similar looking code. Having an accepted standard for code improves ease of understanding and prevents the need for ongoing discussions about formatting quirks. This guide will be created and updated on the Github page for the project. For the current time the formatting that exists in the current codebase should be maintained as much as possible. If there are further questions about a particular style they can be raised to the group in the Slack channel.

## Git Guidelines

Developers add contributions to the project using git. Git is a very powerful tool that allows for a high level of customization. Guidelines for branching, forking and creating pull requests will be outlined on the Github wiki. This will ensure that all developers follow good source control standards when contributing.

# Lazy Consensus

Lazy consensus is a very important concept within the project. It is this process that allows a large group of people to efficiently reach consensus, as someone with no objections to a proposal need not spend time stating their position, and others need not spend time reading such mails.

For lazy consensus to be effective, it is necessary to allow at least 72 hours before assuming that there are no objections to the proposal. This requirement ensures that everyone is given enough time to read, digest and respond to the proposal. This time period is chosen so as to be as inclusive as possible of all participants, regardless of their location and time commitments.

## Transparency

Building community trust in the governance of an open-source project is vital to its success. To that end, decision making must be done in a transparent, open fashion. No decisions about the project’s direction, bug fixes or features may be done without community involvement and participation. Discussions must begin at the earliest possible point on a topic; the community’s participation is vital during the entire decision-making process.

# Communication

Communication is vital to keeping the project alive and flourishing. The majority of communication will take place in the OpenGee Slack channel. This provides everyone from contributors to sustainers a place to discuss technical issues, design ideas and everything in between. In addition, there is a [Google Group](https://groups.google.com/forum/#!forum/google-earth-enterprise) available to discuss the project as well. The OpenGEE.org website will be updated with more user friendly documentation and major project releases. Lastly, the [wiki page](https://github.com/google/earthenterprise/wiki) contains links to all the aforementioned communication means and will be updated as new forums become available.

# Roadmap - Milestones

One important aspect of any project is a clearly defined roadmap. When this project has reached a more stable point a roadmap will need to evolve to plan out future work. In the spirit of transparency, the roadmap will be laid out on the public OpenGee.org site so that anyone interested in the project can view it. The slack channel and google group provide developers and contributors a good way to provide feedback on the road map or suggest future considerations.

Currently, releases will be tracked via the Milestones tab in the GitHub Issues page. A number of features will be be added to each Milestone and prioritized. Then any person with Public Access can view and work on issues in that Milestone. Once all the issues in a Milestone are completed and merged a new release can be created.

# License

The OpenGEE project will abide by the Apache v2 license. [https://www.apache.org/licenses/LICENSE-2.0](https://www.apache.org/licenses/LICENSE-2.0)

The Apache License (ASL) is a permissive free software license written by the Apache Software Foundation (ASF) The Apache License requires preservation of the copyright notice and disclaimer. Like other free software licenses, the license allows the user of the software the freedom to use the software for any purpose, to distribute it, to modify it, and to distribute modified versions of the software, under the terms of the license, without concern for royalties.

*This work is based upon "**[Meritocratic Governance Mode*l](http://www.oss-watch.ac.uk/resources/meritocraticGovernanceModel)*" by University of Oxford.*
