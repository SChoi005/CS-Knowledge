# Open Source SW

## The Beginnings of Free and Open Source Software

### Early Software
* 1940s ~ 1970s 
  * Develope driven by universities or company labs. e.g., MIT, AT&T Bell Labs
  * Openness and Collaboration culture
  * "Software is a tool to use hardware.
  * System users in person make software and share that.

### UNIX
* The beginning in Bell Labs in 1969.
* Version 4 - rewritten in C (1973)
  * Disappear need to produce OS for each hardware - The First Portable OS
* Version 6 (1975)
  * Start licensing for universities and companies.
  * Restrict "software as a business" due to US government antitrust
* UNIX SYSTEM V (1983)
  * Commercialization of UNIX -> UNIX WARS

### PC (1980s)
* Market domination of IBM hardware & Microsoft OS
  * not need source code due to standardized PC system structure. 
* Shareware
  * software that is distributed free on a trial basis with the understanding that the user may need or want to pay for it later.
  * "Try before you buy"
  * not Open Source

### Disruption of Hacker Culture
* MIT AI Lab
  * "Pure hacker paradise"
  * US Copyright Act of 1976
    * Program productor stop providing source code
  * Lisp Progrmming Language
    * Commercialization (1979)
    * Symbolics vs Lisp Machin Inc. War

### GNU
* By Richard Stallman (1983)
  * Unix-compatible
  * A world where can be lived even with free software
* GNU Public License (GPL, 1989)
  * In case of distribution by revising GPL program, must release source code.
  * Copyleft, reciprocal licence

### Server OS competition : Unix vs. Windows
* In past, produce OS specified various hardware
* As become standardizing hardware as Intel x86 architecture, occur competition for domination for os market
* Microsoft
  * OS/2 with IBM (1985) : fail due to opinion difference with IBM
  * Windows NT (1993) : Due to convenience of installation and using, be more competitive

### Internet Age

* World Wide Web (1990)
  * popularization of Internet
* Distributed computing trend
  * One large System (scale-up) -> Many small systems (scale-out)   
* OS for Internet Servers
  * Researchers and DIY users prefer modularity of unix
  * Declination other OS like BSD UNIX.
  * New Challenger : LINUX

### LINUX
* Linus Torvalds, Finland undergraduate student, start as hobby.
* Unix-like OS based on the Linux kernel, GPL licenced
  * Free download, UNIX program and skills compatible
  * Explosive growth by getting popularity for students, research institute.
* Advent of Internet companies (Google, Amazon, Facebook)
  * prefer software that can be customization as low price
  * Open source is best

### Distruptive Innovation
> By developing and starting from providing technologies for Low-end customers, process that pushes existed competitors that are in high-end.<br/>

![image](https://user-images.githubusercontent.com/64727012/169639390-59bb97fc-dc40-4948-8bca-2a27de0894e5.png)

### 21 century open source
* Ecosystem suitable for innovation
  * Cloud computing, big data, containers, AI
  * e.g. Hadoop MapReduce + Apache Spark + Ceph
* Destruction of Software Monolith
  * Minimaize License fee, installation cost and tying 
* Distributed and flexible computing landscape
  * Mix and match
  * Focus on implementation than Standard setting

## Open Source Contracts and Management

### Free Software
* Richard Stallman
  * GNU Manifesto (1985)
  * Philosophy against of commercialization of software 
* Free as in beer vs. <strong>free as in freedom</strong>
  * Share source code
  * Freely revision, distribution

### Open Source
> "Open Source Summit" - Tim O'Reilly (1998)

* Include widely range of concept than free software.
  * organization, collaboration, innovation, development 
  * Pragmatism / Commercialism
    * Active investment of big companies. e.g. IBM
    * Laying the foundation for Internet service in the late 1990s

### Open Source Licensing
* Open Source Initiative (OSI)
  1. Free redistribution
  2. Source code
  3. Allow modifications
  4. No prohibitions about who or why
  5. e.g. "Educational purposes only" - impossible!

### Copyleft vs. Permissive
* Copyleft License
  * GNU General Public License (GPL): GCC, Linux
  * If revise or distribute program, must distribute with source code of revised one. (reciprocity requirement)
  * Prevent Free rider : tragedy of the commons
* Permissive Licensee
  * Apache, BSD, MIT License: Swift, Angular.js
  * Users grant authority that is freely available to program.
  * Can use commercially through Copyright
  * Focus on activating community
* Trend that prefer to Permissive License.
* Flexibility
  * Convenient for companies to use Open Source and closed source program together.
* License Compatibility Problem
  * Permissive license project can be granted GPL, but once it becomes GPL, it never come back.
  * “Linux is a cancer” - Steve Ballmer, CEO of Microsoft (2001)
* Participation
  * The more users, the easier it is to activate
* License is only requirement, activating of open source project is contingent on governance.

### Governance
* Operational methods that drive user compliance
* First step : Policy
  * Organize available license list and scope of use
  * Preliminary investigation not to be problem legally
* Second step : Process
  * Continuing while project live
  * By using scanning tool, organize license conflict and dependency between software component

### Projects vs. Products
* Projects (upstream)
  * Code that developers contribute to 
  * Community : core contributors, mailing lists, websites
* Products (downstream)
  * product made for solving costomer's business problem.
  * Combine, sell and support project according to specific usage
* Project and product are interdependent

### Support
* Product is concept that includes support to service by project satisfying customer's requirements
  * Basic customer service : installation, solving error.
  * Offering solution and required documentation when Several open source projects are connected 
  * Life-cycle support : Version control, dependency solution
  * Legal support : Management of intellectual property disputes, etc.
  * e.g. Red Hat: Enterprise Linux subscription service

### Security
> “Security through obscurity is not true security”
* Not guarantee security even if implementation is opaque
* Because cyber attack penetrates already known weakness
* "Many Eyes" : can recongnize and revise problem of project fastly
* Continuously need security activity even if there are many users.

### How to participate Open Source develop
1. Start new Open Source Project develop
   * Is new project needed?
   * What is business objective through project?
   * What is project develop requirement?
   * Stand-alone project, foundation/company-backed?
     * Linux Foundation, OpenStack Foundation, CNCF, etc. 
   * Hosting / communication / governance model …
2. Participate existed Open Source Project
   * Identify community stucture and, lurk to understand norm and culture 
   * Start small : indirect participation (documentation, funding)
   * Code talks: quality, quantity, consistency of contributions
   * Occasionally, companies contribute bug fixes and feature updates created for business needs.
3. Need considerable time and effort to understand Licensing, compliance, and participation, etc.

## Open Source Develop Model
* A Toolbox of Practices
  * Not one of standardized model, but change according to objective and requirement 
* Success factor of Linux
  * System that can release by applying numerous user feedback fastly
  * In early days, frequently updating more than twice a day

### The Cathedral and the Bazaar
* The Cathedral
  * According to a prior plan, skilled workers divide the labor
  * Thoroughly management toward fixed destination
  * e.g. GCC (GNU C Compiler)
* The Bazaar
  * No central control
  * The quality of work varies and the efficiency may be lowered
  * Value wide participation and experimentation, and continue organic evolution
  * e.g. Linux
* It is difficult to say that a certain system is superior
  * Because insight comes about from individual, need develop model that recongnizes and reward good insight

### Governance
* Social and decision-making framework for a project
  * Decision formation process
  * Project's core principles
  * Project's core goals
  * community
* Some decisions are required at the beginning of the project (License, IP, Goal, Range, Role assignment), but it is effective that most  decision is taken over to community

### Decision-making approaches

* Benevolent Dictator for Life (BDFL)
  * A principal has right of final decision(mainly project initiator) about main matter
  * e.g. Linux(Linus Torvalds)
  * Generally the way in small project
  * It is difficult for companies to participate
    * May not be benevolent to new developer
    * If not be recognized to BDFL, occur second-class citizen issue
  * Risk of fragmentation between BDFL and community
* Meritocracy
  * If be recognized ability, be granted permmision of code repository from develop community.
  * e.g. Apache Foundation
  * Merit is evaluated mainly based on experience and knowledge
* Consensus (a.k.a. liberal contribution model)
  * Get bigger effectness according to recent contribution 
  * Decision is made through consensus process like vote, etc.

### Basic Principle of Open Source
* Open First
  * Make decision related project openly
  * Transparency, openness and encouraging participation are important 
* Separate between skill and business decision
  * Open source projects should be steered, at least in part, by those contributing the code
  * Upstream development handled by contributors, downstream product decisions lead by companies
* Example : Kubernetes

### Set Goal
* Should be detail and clear by giving direction
  * What value do we make?, How?, For Who? 

### Community
* Leaders
  * Have right of final decision about feature, release, etc.
  * BDFL, committee, or voting group 
* Maintainers
  * Maintain/manage the part of the project you are responsible for
  * close to editor than programmer
  * Legal work, event planning, bug tracker management, etc.
* Committers
  * Developers who can summit in person to code base
  * Reviewed by maintainer
* Contributors
  * All Contributions are reviewed before submission 
  * Reflect review, feedback and resubmission by passing through more than one time
  * Occasionally, program user becomes contributor

### Encouraging New Contributors
> As it is frequent that contributor gets out project, community should always receive new contributor
1. Exchange control for influence
   * The more freely it is, the more contributions there are
2. Reducing Friction of Tools
   * Develop environment or infrastructure could form barriers to entry
   * simplify set-up by using virtual machine, container
   * Through modular design, give environment that contributor can develop independently from other parts
3. Mentoring
   * Short term expense is occured by requiring mentor's time investment and sincerity, but it is necessary to maintain project in the long run
   * Start from giving a small work
   * Prompt feedback and update are important
4. Culture 
   * Culture orienting empathy, respect, and inclusiveness
   * Members could feel as sense of belonging is reward 

### Evaluation criteria (Metrics and Data)
> “Humans adjust their behavior based on the metrics”

* Selection of evaluation criteria
  * e.g. batting average vs. On-Base Percentage (Moneyball) 
  * An important metric selection process required
* Interpretation of indicators
  * e.g. Are bug report increments always bad? What if the number of users increased? 
* Soft Metrics
  * Elements that occur costs, such as surveys and interviews, but are necessary for the project to be sustainable in the long run. 
  * Community Composition: What is the ratio of independent developers to enterprise developers? Isn't the influence of developers from specific companies too great?.
  * How satisfied is the community? Is communication between members working well?




<strong>Reference</strong>
* Gordon Haff, "How Open Source Ate Software"
