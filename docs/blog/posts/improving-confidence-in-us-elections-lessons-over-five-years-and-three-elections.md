---
 
date: 2024-04-19
categories:
  - electionguard
  - product
  - open-source
authors:
    - rc-sea
---
# Improving Confidence and Participation in US Elections: Lessons from Five Years and Three Elections with ElectionGuard

# Abstract #

ElectionGuard is an open-source software development kit that enables election system vendors to implement end-to-end verifiable elections (e2e-v) in their systems.  Its intent is to increase participation in elections and confidence in election outcomes.
Unlike previous e2e-v systems, ElectionGuard is designed to be integrated into other voting systems and existing election procedures, and does not add any steps to the core voting process.
This article outlines some of the key learnings in deploying ElectionGuard with multiple election vendors in three different US elections over five years of software development, including how success was measured and what was learned from user testing and voter interaction.  
In addition to the work preparing the core software capability and services with vendor partners VotingWorks and Hart InterCivic, the ElectionGuard team and the Center for Civic Design worked extensively with election administrators to develop usable and useful documentation, poll-worker training, and voting procedures that presented ElectionGuard as an aspect of the entire voting process, not a standalone technology.  Enhanced Voting hosted the confirmation code lookup site, and MITRE wrote two independent verifiers.
Due to the small sample size and qualitative nature of the user research, it is difficult to say definitively that confidence was improved, and even if it were how much would be attributable to ElectionGuard. However it is reasonable to say the community was supportive of the efforts and appreciated the investment in voting and elections generally. In addition, finding the proper ways to articulate the value and importance of a complex technology to a universal audience is critical for scaling adoption and understanding going forward.

# What does it mean to increase confidence and participation? #

Confidence refers to the perception of the administrative conduct of elections:  were votes properly counted? Research shows voters have a distinct impression of election administration separate from the political environment or actors around it [^11].
Many factors contribute to a voter's confidence. Voters are generally more confident about their local elections than those in other jurisdictions or that use different voting methods [^12]. The "winner-loser gap" shows that voters who vote for a winning candidate, especially in major elections such as US President, tend to have more confidence in the election outcome than those who voted for the losing candidate [^13]. Confidence can be affected by a voters' personal experience with the voting process, especially as relates to waiting in lines or interactions with poll workers [^15].
During the elections, feedback was collected from voters through exit interviews, post-election surveys, observations in the polling place, and monitoring the use of the confirmation code lookup website.  While there was not sufficient volume and robust enough sampling to make any declarations with scientific rigor, anecdotal review speaks to support for investing in election technology generally as valuable. Many voters appreciated the mission of the endeavor if not its technical nuances. Few criticisms were voiced other than concerns about funding, and all the election administrators found the experience worthwhile.

# Implementing ElectionGuard #

ElectionGuard is a free open-source software development kit (SDK) that enables voting system manufacturers to incorporate end-to-end verifiable election capabilities into their systems. It is not a voting system in and of itself. It is deployed as a component of a voting system and enables elections produced by that system to be end-to-end verifiable.
The configuration of an ElectionGuard election can vary based on the voting method, the integration approach used, as well as any relevant voting regulations and processes concerning what can be printed on paper ballots, whether rescans are allowed, etc.
ElectionGuard was initiated and incubated within Microsoft's Democracy Forward initiative in 2018 and has been used in three elections since: Fulton, Wisconsin (2020); Preston, Idaho (2022), and College Park, Maryland (2023). Enhanced Voting has incorporated ElectionGuard as part of its Electronic Ballot Return solution that is currently being used in several US states. ElectionGuard is also used in multiple European voting systems.
A fully-realized ElectionGuard SDK would support all voting methods: paper-based, electronic, remote/portable[^fn1] and in-person. This extends to different tally methods and electoral systems: plurality, ranked-choice, approval voting, and more. By extending across all the voting methods used within any jurisdiction, the full election record generated becomes a public resource that can identify areas of potential tampering but hopefully mostly serve as a publicly verifiable validation of the released tallies.

# Key Lessons #

## First, do no harm ##

ElectionGuard is a software development kit (SDK) for adding the feature of end-to-end election verification; it does not and should not change the core voting process.
Several end-to-end verifiable elections have been previously held in the US, each using different methods to record e2e-v ballots.[^fn2] They all imposed additional steps to the voting process itself: to successfully cast a vote, the voter had to engage with the e2e-v methodology. Studies of these approaches reinforced the core notion that "voters expect the steps required to vote with an e2e system to be roughly the same as voting with a standard paper ballot or electronic voting machine."[^fn3] 
In all of the elections, from the perspective of voter, the ElectionGuard "experience" consisted solely of receiving an accompanying confirmation code printout. The actions the voter had to perform were solely for the purpose of voting.
Voters could also perform a BallotCheck challenge, but that process was purposefully identical to the process by which voters who make a mistake or wish to change their ballot before casting it follow. ElectionGuard created a procedural wrinkle about whether all spoils would be treated as challenges, but the software supported either approach. The core process from the voter's perspective in either case was identical, however.

## Analogies matter ##

People use analogies to make sense of new experiences. With ElectionGuard, the action of printing the confirmation code during voting is similar to generate a tracking number used to track packages: you can't see what is being delivered, just whether it has been.  Anecdotal evidence from both Preston and College Park voters indicated confidence increased for some solely based the fact of the printed confirmation code because of its familiarity and latent promise of fulfillment; that it could be used was sufficient [^18].
The voting system and the ElectionGuard encryption process reinforced each other. The combination of having a ballot scanner’s (in the case of the Hart system)  interpretation of the ballot on a review screen and that the confirmation code came from the same device made the association of the two actions clear. Even the pause before the review screen was displayed – waiting for the confirmation code to begin printing - helped focus voters’ attention on this final moment to confirm their votes before casting and establish that the confirmation code was already committed.

## The Proper Value Prop ##

ElectionGuard, and end-to-end verifiability in general, are complex systems using advanced cryptography and security practices in a fully open source environment. However, those features may not resonate when explaining the value of ElectionGuard to the voting public.
In testing voter education messages before the elections, both ad hoc and formally, it emerged that discussions of security as a benefit can backfire because they often call attention to the potential negative outcomes the security procedure is designed to protect against.  In the worst case, doubt can be introduced where previously there was none. 
The results of user testing unambiguously resonated around the individual agency and transparency benefits ElectionGuard afforded:
•	Voters could use confirmation codes to demonstrate to themselves that their ballot was included.
•	Making the entire election record public and verifying it independently increases transparency, enabling better scrutiny

## Bite. Snack. Meal. ##

There's a tendency when discussing a complex topic to feel the need to to try to explain it so people fully understand. Even if that were advisable, end-to-end verifiability in full scope is an intimidating topic. When it came to explaining what ElectionGuard was, it was almost impossible to strike a balance between being explicitly technically accurate while using language everyday voters could understand. Discussing ElectionGuard's technical rationale or capabilities could confuse and thus quickly alarm a voter we were hoping to excite.
People are showing up to vote, not to participate in the launch of a new technology. Voters really only need to understand how to vote if they don't already (the voting system itself was new to voters in Fulton and College Park elections). Beyond that, the minimum viable takeaway was for voters to understand the meaning of the confirmation code printout generated by the voting process. 
In Wisconsin, the separately printed confirmation code page provided a place to provide additional information explaining its purpose. Because we had a fully standard separate page for printing the code, we included explanatory information and where to find more on the entire process. 
For Preston and College Park, because the printout size of the code was much smaller, receipt-holders were pre-printed for each voter to store the printout generated by the scanner. The receipt-holders explained what the confirmation code was for and how to check their ballot was included, and where to go for more information if they're interested.
Poll workers needed to know more because they had to be prepared to answer questions from voters. Even still, they were spared discussions of homomorphic encryption and cryptography; the goal was to help them feel confident about what they're imparting to voters. In this case it was easier to articulate a value proposition than an explainer: what the process was supposed to accomplish rather than how it worked. The point of the confirmation code printout was so the voter could check their ballot was included in the published election results. All poll workers needed to tell the voter was to tear the printout off and put it in the sleeve we handed them, and that the sleeve had all the info they needed to know if they had any questions.
This bite --> snack --> meal approach permeated all discussions and documentation. The ballot challenge process is another example. Rather than tell the voter they could "challenge a ballot", they were told they could run a BallotCheck. The term was intentionally made to sound like a generic product innovation than explicitly a zero trust exercise to prove no malicious actor was present.

## It takes an Ecosystem ##

ElectionGuard is an open source SDK. It ultimate success resides in those who contribute to and adopt it for real-world use. The election administrators who green-lighted ElectionGuard for use in their locales took risks they didn't have to, and took work upon themselves they likely didn't realize the full scope of when work began. 
VotingWorks, Hart InterCivic, and Enhanced Voting dedicated significant resources to working with and QA-ing different aspects of the voting codebase to integrate ElectionGuard into their systems. And MITRE independently wrote two distinct verifiers to support the Preston and College Park elections. 
The Center for Civic Design provided user research, documentation and training materials, and exit polling. InfernoRed developed the production codebase and admin software of the SDK, and numerous academics and open source researchers contributed to the security techniques and cryptographic review along the way. This project wouldn't be successful without all their contributions.

## An iterative process ##

Election administrators will often use multiple voting methods to address different voting populations or phases of an election. ElectionGuard will be its most effective when it can address all of the voting methods and configurations in common use, but achieving that capability will necessarily take many iterations across elections of different makeup and size.
Each election to date has presented operational and regulatory differences. Innocuous regulatory requirements can render ElectionGuard ineligible, such as a requirement to re-scan all the ballots scanned previously when a scanner is taken out of service [^fn4].  The largest impediments to wider adoption are regulatory-driven requirements that prevent modification of certified systems to accommodate new features such as ElectionGuard without triggering recertification of the entire system.

# Conclusions and recommendations #

## Success at the local level ##

With each of the three elections the ElectionGuard program has been involved in to date, the local populace has been supportive of the effort. Some voters were happy to see any investment in voting technology, others were happy Microsoft was involved. Most voters found positive things to say about the experience even if it wasn't directly related to ElectionGuard. 
That is unambiguous good news, even if it isn't solely due to ElectionGuard itself. If the goal of the endeavor is increasing confidence in election outcomes with the voting public, it some sense it doesn't matter whether that confidence manifests in checking a confirmation code or challenging a ballot. The awareness of  being able to matters in providing emotional confidence. Seeing investment in election technology at all can also be the "source" of confidence [^fn5]. 
In many ways a better test of efficacy is not how much ElectionGuard was noticed as part of an election, but how much it wasn't. It didn't get in the way of voters' productivity. It didn't cause confusion for voters. It looked like it was part of the voting system. 
Exposure to ElectionGuard over time should allow it to be seen in its own analytic light, but that it can coexist peacefully with the base system is its own accomplishment considering the significance of the code and cryptographic principles being applied.

## Bolstering the Secret Ballot ##

The secret ballot is a cornerstone of modern democratic voting, and arguably the last major widespread voting innovation in the voting process itself introduced in the last hundred years. However, voting and the secret ballot introduce actions and conditions not common in a voter's daily experience. Voters concerned about coercion place confidence in the system not to reveal their preferences. Voters unconcerned about coercion can still be concerned that their votes are processed accurately, and the lack of visibility into whether and how the system processed their vote can diminish confidence on its own.
ElectionGuard and e2e-v bolster and complement the secret ballot. 
Having a confirmation code is analogous to having a shipping receipt from Fedex and UPS. The emotional weight of surety of delivery is significant for packages, and so, too, potentially, with voting. It is reasonable to assume a similar emotional benefit accrues, especially for voters voting remotely or using systems that use centralized tabulation. Voters that take the extra step of challenging a ballot can test the system entrusted with keeping it secret, and in doing so help ensure that it does.

## Other potential benefits ##

ElectionGuard and e2e-v enable election systems to exhibit software independence, a capability recognized by the Election Assistance Commission for systems to comply with the VVSG 2.0 election system guidelines. End-to-end verifiability and paper-based systems are the only two mechanisms recognized.  
Paper-based systems do not serve many voting populations well, especially for the core criteria of voting independently. Electronic voting systems can serve multiple populations simultaneously, especially when combining capabilities such as visual, language, and audio support simultaneously, or integrating with voters' adaptive controllers. ElectionGuard could provide the software independence component of innovative accessible electronic systems while also working with paper-based systems to achieve the real systemic benefit of transparency and independent verifiability. 
Voters tend to trust their local elections and election officials more than those of other methods and states. Were ElectionGuard to become truly widespread while maintaining or building confidence along the way, it offers the potential to become a connective link across elections that increases confidence in the system overall.

## Only active e2e-v project ##

ElectionGuard is currently the only e2e-v offering being developed for use in US elections for e2e-v purposes [^fn6].  More ElectionGuard elections should be supported and encouraged to build on the foundation established by these three: additional voting methods and vendors, more complex elections supporting multiple methods simultaneously, and larger elections generally.

[^fn1]: discuss difference between

[^fn2]: references to each

[^fn3]: Mike Meyer UX article reference

[^fn4]: subsequent scans would generate a different confirmation code

[^fn5]: reference charles stewarts voting investment

[^fn6]: discussion of all other e2e-v use cases as being deployed for remote electronic voting.