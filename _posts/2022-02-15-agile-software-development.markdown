---
layout: "post"
title: "Agile Software Development"
description: Learn about Agile Software Development
date: "2022-02-15 19:05"
author: Kautsar Virzawan
categories: [QA Knowledge, Agile Tester]
tags: [Learning]
---
## The Fundamentals of Agile Software Development
### The Agile Manifesto

Agile Manifesto developed in 2001, it contains four statements of values:
* Individuals and interactions _over_ processes and tools
* Working software _over_ comprehensive documentation
* Customer collaboration _over_ contract negotiation
* Responding to change _over_ following a plan

The Agile Manifesto argues that although the concepts on the right have value, those on the left have greater value.

**Individuals and interactions**  
Agile development is very people-centered. Teams of people build software, and it is through continuous communication and interaction, rather than a reliance on tools or processes.

**Working Software**  
From a customer perspective, working software is much more useful and valuable than the overly detailed documentation and it provides and opportunity to give the development team rapid feedback, agile development can confer significant time-to-market advantage. Agile development is useful in rapidly changing business environments where the problems or solutions are unclear.

**Customer Collaboration**  
Collaborating directly with the customer improves the likelihood of understanding exactly what the customer requires. While having contracts with customer may be important, working in regular and close collaboration with them is likely bring more success to the project.

**Responding to Change**  
Change is inevitable in software projects. The environment in which the business operates, legislation, competitor activity, technology advances, and other factors must be accomodated by the development process. Having flexibility in work practices to embrace change is more important than simply adhering rigidly to a plan.

**Principles**  
The core Agile Manifesto values are captured in twelve principles:
1. Our highest priority is to satisfy the customer through early and continuous delivery of valuable Software.
2. Welcome changing requirements, even late in development. Agile process harness change for the customer's competitive advantage.
3. Deliver working software frequently, at intervals of between few weeks to a few months, with a preference to the shorter timescale.
4. Business people and developers must work together daily throughout the project.
5. Build projects around motivated individuals. Give them the environment and support they need, and trust then to get the job done.
6. The most efficient and effective method of conveying information to and within a development team is a face-to-face conversation.
7. Working software is the primary measure of progress.
8. Agile Processes promote sustainable development. The sponsors, developers, and users should be able to maintain a constant pace indefinitely.
9. Continuous attention to technical excellence and good design enhances agility.
10. Simplicity is essential
11. The best architectures, requirements, and designs emerge from self-organizing teams.
12. At regular intervals, the team reflects on how to become more effective, then tunes and adjusts its behaviour accordingly

### Whole-Team Approach

The whole-team approach means involving everyone with the knowledge and skills necessary to ensure project success. The team includes representatives from the customer and other business stakeholders who determine product features. The team should be relatively small as few as three people and as many as nine. Ideally, the whole team shares the same workspace, as co-location strongly facilitates communication and interaction. The whole-team approach is supported through the daily stand-up meetings involving all members, where work progress is communicated and any impediments to progress are highlighted.  

Whole-team approach benefits in Agile development:  
* Enhancing communication and collaboration within the team.
* Enabling the various skill sets within the team to be leveraged to the benefit of the projects
* Making quality everyone's responsibility

The whole team is responsible for quality in Agile projects. Testers will work closely with both developers and business representatives to ensure that the desired quality levels are achieved. This includes supporting and collaborating with business representatives to help them create suitable acceptance tests, working with developers to agree on the testing strategy, and deciding on test automation approaches.

### Early and Frequent Feedback

Agile projects have short iterations enabling the project team to receive early and continuous feedback on product quality throughout the development lifecycle. One way to provide rapid feedback is by continuous integration.

When sequential development approach are used, the customer often does not see the product until the project is nearly completed. At that point, it is often too late for the development team to address any issue the customer may have. By getting frequent customer feedback, Agile teams can incorporate most new changes into product development process. Early and frequent feedback helps the team focus on the features with the highest business value, or associated risk, and these are delivered to the customer first.  

The Benefits of early and frequent feedback:  
* Avoiding requirements misunderstandings, which may not have been detected until later in the development cycle when they are more expensive to fix.
* Clarifying customer feature requests, making them available for customer use early. This way, the product better reflects what the customer wants.
* Discovering (via continuous integration), isolating, and resolving quality problems early.
* Providing information to the Agile team regarding its productivity and ability to deliver.
* Promoting consistent project momentum.

---

## Aspects of Agile approaches

There are a number of Agile approaches in use by organizations. This subsection describes some of the agile approaches.

### Agile Software Development Approaches

**Extreme Programming**  
Originally introduced by Kent Beck, is an agile approach to software development described by certain values, principles, and development practices. XP embraces five values to guide development:
1. Communication
2. Simplicity
3. Feedback
4. Courage
5. Respect

XP describes a set of principles as additional guidelines:
1. Humanity
2. Economics
3. Mutual benefit
4. Self similarity
5. improvement
6. Diversity
7. Reflection
8. Flow
9. Opportunity
10. Redundancy
11. Failure
12. Quality
13. Baby steps
14. Accepted responsibility

XP describes thirteen primary practices:
1. Sit together
2. Whole team
3. Informative workspace
4. Energized work
5. Pair programming
6. Stories
7. Weekly cycle
8. Quarterly cycle
9. Slack
10. Ten-minute build
11. Continuous integration
12. Test first programming
13. Incremental design

**Scrum**  
Scrum is an Agile management framework which contains the following constituent instruments and practices:
* Sprint: Scrum divides a project into iterations (called sprints) of fixed length (usually 2-4 weeks).
* Product Increment: Each sprint results in a potentially releasable product.
* Product Backlog: Product owner manages a prioritized list of planned product items. The product backlog evolves from sprint to sprint (called backlog refinement).
* Sprint Backlog: At the start of each sprint, Scrum team selects a set of highest priority items from product backlog.
* Definition of Done: Defines appropriate criteria for sprint completion.
* Timeboxing: If the development team cannot finish a task within a sprint, the associated product features are removed from sprint and the task moved back into product backlog. Also applies for enforcing meeting start and end times.
* Transparency: The development team reports and updates sprint status on a daily basis at a meeting called daily scrum, it makes the progress of the sprint more visible to the team.

Scrum defines three roles:
* Scrum Master: Ensures that Scrum practices and rules are implemented and followed, and resolves any violations, resource issues, or other impediments that could prevent the team from following the practices and rules. This person is not the team lead, but a coach.
* Product Owner: Represents the customer, and generates, maintains, prioritizes the product backlog. This person not the team lead.
* Development Team: Develop and test the product. The team is self-organized, there is no team lead, so the team makes the decisions.

Scrum (as opposed to XP) does not dictate specific software development techniques (e.g., test first programming). In addition, Scrum does not provide guidance on how testing has to be done.

**Kanban**  
Kanban is a management approach that is sometimes used in Agile projects. The general objective is to visualize and optimize the flow of work within a value-added chain. Kanban utilizes three instruments:
* Kanban Board: The value chain to be managed is visualized by a Kanban board. Each column shows a station, which is a set of related activities, e.g., development or testing. The items to be produced or tasks to be processed are symbolized by tickets moving from left to right across the board through the stations.
* Work-in-Progress Limit: The amount of parallel active tasks is strictly limited. This is controlled by the maximum number of tickets allowed for a station for the board. Whenever a station has free capacity, the worker pulls a ticket from predecessor station.
* Lead Time: Kanban is used to optimize the continuous flow of tasks by minimizing the lead time for the complete value stream.

Iterations or sprints are optional in Kanban. The Kanban process allows releasing its deliverables item by item, rather than as part of a release. Timeboxing as a synchronizing mechanism, therefore, is optional, unlike in scrum, which synchronizes all tasks within a sprint.

### Collaborative User Story Creation

Poor specifications are often a major reason for project failure. Specification problems can result from the users lack of insight into their true needs, absence of a global vision for the system, redundant or contradictory features, and other miscommunications. In agile development, user stories are written to capture requirements from the perspectives of developers, testers, and business representatives. In sequential development, this shared vision of a feature is accomplished through formal reviews after requirement are written. In Agile development, this shared vision is accomplished through frequent informal reviews while the requirements are being written.

The collaborative authorship of the user story can use techniques such as brainstorming and mind mapping. The tester may use the INVEST technique:
* Independent
* Negotiable
* valuable
* Estimable
* Small
* Testable

According to the 3C concept, a user story is the conjuction of three elements:
* Card: The card is the physical media describing a user story. It identifies the requirement, its criticality, expected development and test duration, and the acceptance criteria for that story.
* Conversation: The conversation explains how the software will be used. The conversation can be documented or verbal. Conversations begins during the release-planning phase and continues when the story is scheduled.
* Confirmation: The acceptance criteria, discussed in the conversation, are used to confirm that the story is done. These acceptance criteria may span multiple user stories. Both positive and negative tests should be used to cover the criteria

### Retrospectives

Retrospectives is a meeting held at the end of each iteration to discuss what was successful, what could be improved, and how to incorporate the improvements and retain the successes in future iterations.  

Retrospectives can result in test-related improvement decisions focused on test efectiveness, test productivity, test case quality, and team satisfaction. Root cause analysis of defects can drive testing and development improvements. In general, teams should implement only a few improvements per iteration. This allows for continuous improvement at a sustained pace.

The timing and organization of the retrospective depends on the particular Agile method followed. Business representatives and the team attend each retrospective as participants while the facilitator organizes and runs the meeting. In some cases, the teams may invite other participants to the meeting.

### Continuous Intergration

Delivery of a product increment requires reliable, working, integrated software at the end of every sprint. Continuous integration addresses this challenge by merging all changes made to the software and integrating all changed components regularly, at least once a day. Since developers integrate their work constantly, build constantly, and test constantly, defects in code are detected more quickly.  

Continuous Integration process consists of the following automated activites:
* Static code analysis: executing static code analysis and reporting results
* Compile: compiling and linking the code, generating the executable files
* Unit test: executing unit tests, checking code coverage and reporting test results
* Deploy: installing the build into a test environment
* Integration test: executing the integration tests and reporting results
* Report (dashboard): posting the status of all these activities to a publicly visible location or e-mailing status to the team

An automated build and test process takes place on a daily basis and detects integration errors early and quickly. Continuous integration allows Agile testers to run automated tests regularly, in some cases as part of the continuous integration process itself, and send quick feedback to the team on the quality of the code. Automated regression testing can be continuous throughout the iteration. Good automated regression tests cover as much functionality as possible, including user stories delivered in the previous iterations.  

Continuous integration can provide the following benefits:
* Allows earlier detection and easier root cause analysis of integration problems and conflicting changes
* Gives the development team regular feedback on whether the code is Working
* Keeps the version of the software being tested within a day of the version being developed
* Reduces regression risk associated with developer code refactoring due to rapid re-testing of the code base after each small set of changes
* Provides confidence that each day's development work is based on a solid foundation
* Makes progress toward the completion of the product increment visible, encouraging developers and testers
* Eliminates the schedule risks associated with big-bang integration
* Provides constant availability of executable software throughout the sprint for testing, demonstration, or education purposes
* Reduces repetitives manual testing activities
* Provides quick feedback on decisions made to improve quality and testers

Continuous integration risks and challenge:
* Continuous Integration tools have to be introduces and maintained
* The continuous integration process must be defined and established
* Test automation requires additional resources and can be complex to established
* Thorough test coverage is essential to achieve automated testing advantages
* Teams sometimes over-rely on unit tests and perform too little system and acceptance testing

### Release and Iteration Planning

Release planning looks ahead to the release of a product, often a few months ahead of the start of a project. Release planning defines and re-defines the product backlog, and may involve refining larger user stories into a collection of smaller stories. Release planning provides the basis for a test approach and test plan spanning all iterations. Release plans are high-level.  

In release planning, business representatives establish and prioritize the user stories for the release, in collaboration with the team.  

Testers are involved in release planning and especially add value in the following activites:
* Defining testable user stories, including acceptance criteria
* Participating in project and quality risk analyses
* Estimating testing effort associated with the user stories
* Defining the necessary test levels
* Planning the testing for the Release

After release planning is done, iteration planning for the first iteration starts. Iteration planning looks ahead to the end of a single iteration and is concerned with the iteration backlog.  

In iteration planning, the team selects user stories from the prioritized release backlog, elaborates the user stories, performs a risk analysis for the user stories, and estimates the work needed for each user story. If a user story is too vague and attempts to clarify it have failed, the team can refuse to accept it and use the next user story based on priority. The business representatives must answer the team’s questions about each story so the team can understand what they should implement and how to test each story.

The number of stories selected is based on established team velocity and the estimated size of the selected user stories. After the contents of the iteration are finalized, the user stories are broken into tasks, which will be carried out by the appropriate team members.  

Testers are involved in iteration planning and especially add value in the following activities:
* Participating in the detailed risk analysis of user stories
* Determining the testability of the user stories
* Creating acceptance tests for the user stories
* Breaking down user stories into tasks
* Estimating testing effor for all testing tasks
* Identifying functional and non-functional aspects of the system to be tested
* Supporting and participating in test automation at multiple levels of testing

Release and iteration planning should address test planning as well as planning for development activites. Particular test-related issues to address include:
* The scope of testing, the extent of testing for those areas in scope, the test goals, and the reasons for these decisions
* The team members who will carry out the test activities
* The test environment and test data needed
* The timing, sequencing, dependencies, and prerequisites for the functional and non-functional test activities
* The project and quality risks to be addressed
