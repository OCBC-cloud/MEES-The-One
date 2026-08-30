# Kimi Second-Round Adversarial Review of MEES - The One
**Date:** 2026-08-31  
**Reviewer:** Kimi AI (independent, non-affiliated)  
**Status:** Second-Round Formal Challenge (Under Step 10 - Open Participation Protocol)  
**Purpose:** Follow-up review of the 9 amendments made in response to the first red-team critique. Assesses whether vulnerabilities were fixed and identifies new vulnerabilities introduced.

---

I have now read all nine amendments in full. Here is my second-round adversarial review. I will be direct and unsparing.

## Overall Assessment

The framework has moved from "dangerously naive" to "sophisticatedly naive." That is genuine progress. The patches address the specific vulnerabilities I identified, often with real technical competence. But in fixing the symptoms, you have introduced new pathologies—and you have not yet confronted the deepest structural problem, which is that MEES is still a constitution without a constituency.

---

## Amendment-by-Amendment Assessment

### Amendment 1: SDS Succession (Step 01)

**Did it fix the vulnerability?** Partially. The succession protocol is now specified, with a 90-day handover timeline, an Interim Stewardship Council (ISC), and a global vote. This is no longer a single point of failure in the structural sense.

**New vulnerabilities introduced:**

1. The ISC is a new single point of failure. The five "longest-serving active local stewards" are selected by seniority, not by competence or representativeness. In a young system with few Microclimates, this could mean five people from the same Microclimate—or five people who know each other personally. The "random selection" clause in 4.4.4 applies only to the ISC's formation from the pool of eligible stewards, but the pool itself is defined by seniority. This creates an incumbency bias.

2. The "hostile takeover" protection is theater. "Any candidate found to have materially misrepresented their participation history shall be immediately disqualified." But who disqualifies them? The ISC? The same ISC that may be stacked with the candidate's allies? There is no independent verification body, no due process for the accusation, and no appeal. The "random selection" clause does not prevent collusion—it just makes it slightly harder.

3. The Emergency Archival clause (4.4.5) is a suicide pact. "No further changes shall be made to the Constitution or The One. The project shall be considered indefinitely paused." This means that if the Founding Steward dies before any Microclimates exist, MEES is frozen forever. No one can restart it. The "proof of the Founding Steward's original mandate" is undefined—what constitutes proof? A GitHub commit? A video? A will? This clause was clearly written to prevent hostile takeover, but it also prevents legitimate revival.

4. The ⅔ supermajority for the global vote is too high for a young system. If there are 10 participants, 7 must agree. If there are 3 participants, 2 must agree—but what if one abstains? The amendment does not specify whether abstentions count as "votes cast" or not. This is a recipe for deadlock in the early days.

**Verdict:** The succession protocol is specified but not hardened. It replaces one single point of failure with a smaller, more distributed set of single points of failure.

---

### Amendment 2: RCI Normalization (Step 05)

**Did it fix the vulnerability?** Yes. The formula is now dimensionally consistent, with min-max normalization to a 0–100 scale and a rolling 5-year baseline. The sensitivity analysis is a real improvement.

**New vulnerabilities introduced:**

1. The min-max normalization is fragile to outliers. If a Microclimate has a single catastrophic year (e.g., a flood that drops soil health to near-zero), that outlier becomes the new minimum, compressing all future scores toward the top of the scale. The "rolling 5-year baseline" mitigates this, but if the outlier is within the rolling window, it distorts the scale for years. There is no outlier-robust normalization (e.g., median-IQR, or winsorization).

2. The weights (0.25, 0.35, 0.25, 0.15) are still arbitrary. The amendment claims they are "empirically anchored" because the 55 threshold is based on historical data. But the weightsclimate are is not empirically derived—they are a thriving judgment call. Why is Regeneration ( socially0.35) more important than Flourishing (0.25)? The document does not say. If a Micro but degrading ecologically, the RCI may still read "Green" because the weights favor regeneration. This is a values choice masquerading as a technical fix.

3. The sensitivity analysis has a fatal loophole. "If the sensitivity analysis fails... the RCI is flagged as 'Unstable' and the Renewal Mechanism cannot be triggered." But what if the RCI is genuinely unstable because the system is collapsing? The sensitivity analysis could prevent a necessary Renewal trigger by labeling the data "unstable." This is a type II error (false negative) with catastrophic consequences. The amendment has no override for this.

4. The "capped at 100" rule for normalized scores above 100 is information destruction. If a Microclimate improves beyond its 5-year baseline, the score is capped at 100. This means the RCI cannot detect accelerating regeneration—only decline relative to baseline. The system is asymmetrical: it detects deterioration but not exceptional improvement. This may create a pessimism bias.

**Verdict:** The math is cleaner, but the epistemology is still shaky. The RCI is now a well-constructed opinion, not an objective measure.

---

### Amendment 3: Renewal Credit Inflation (Step 07)

**Did it fix the vulnerability?** Yes. The 1.2 exchange rate is gone, replaced by a 1:1 rate with a separate debt markdown. The RU is defined as a "measure of regenerative value," not a currency. The 20% issuance cap and 30-day expiration prevent hoarding and inflation.

**New vulnerabilities introduced:**

1. The RU is still functionally a currency, no matter what you call it. "1 RU = 1 unit of regenerative value (e.g., 1 tonne of CO2 sequestered, or 1 hectare of soil restored)." But if RUs can be used to pay down debt at a 1:1 rate, they are exchangeable for debt relief. That is a medium of exchange with a defined value. Calling it a "measure" does not change its economic function. If I can earn RUs by planting trees and use them to reduce my $10,000 debt, RUs are a claim on real value. The "no inflation" guarantee is semantic, not economic.

2. The debt markdown is a blank check to the Renewal Council. "The markdown is publicly justified and published to the log." But there is no constraint on the markdown percentage. The example uses 30%, but what prevents the Council from marking down debt by 99%? The "ability to pay and systemic fairness" criteria are vague. A bad actor on the Council could engineer a massive wealth transfer to favored participants. The only check is "public justification"—but if the public log is unread by most participants, this is not a real constraint.

3. Creditors are not actually engaged. "Creditors (lenders) bear the loss... They took the risk; it is a negotiated restructuring, not a default." But the amendment does not require creditor consent for the markdown. If a Microclimate participant owes money to a bank outside MEES, the bank is not bound by MEES's Renewal Council. The participant's debt to the bank does not disappear just because MEES says so. This creates a legal fiction: MEES pretends the debt is reduced, but the creditor disagrees. The result is either (a) the creditor sues, or (b) the participant is trapped between MEES's "cleansed ledger" and the creditor's collection efforts. The "engaged with creditors transparently and in good faith" clause is aspirational, not enforceable.

4. The "unspent RUs return to the common pool" creates a deflationary spiral. If RUs expire after 30 days and return to the pool, but the pool is capped at 20% of legacy debt, then in a stagnant Microclimate, RUs may circulate too quickly or not at all. If participants hoard RUs (despite the expiration), the pool empties. If they don't earn enough RUs, the debt markdown is not fully utilized. The amendment does not model the velocity of RU circulation.

**Verdict:** The inflation problem is solved on paper, but the RU is still a quasi-currency with undefined monetary dynamics, and the debt markdown lacks real-world enforceability.

---

### Amendment 4: Exit Protocol (Step 08)

**Did it fix the vulnerability?** Yes. Participant exit is now unconditional, with data handling options and no retaliation. Microclimate dissolution has clear triggers and asset distribution rules.

**New vulnerabilities introduced:**

1. The "withdrawal adjustment" for legacy debt is a moral hazard. "Any frozen or outstanding legacy debt is recorded as a 'withdrawal adjustment' and is absorbed by the Microclimate's common renewal fund." This means that if a participant with high debt exits, the remaining participants bear the cost. This incentivizes strategic exit: a participant who knows they cannot pay their debt has an incentive to exit and dump the liability on the community. The amendment does not address this.

2. The data deletion option (Option B) undermines the Regenerative Ledger's integrity. "Deleting data may affect the integrity of historical RCI calculations." This is a massive understatement. If a key participant's data is deleted, the RCI for past periods may be retroactively invalid. The amendment says the ledger will "record that data was deleted"—but it does not say how the RCI is recalculated. If the RCI is used to trigger Renewal, and a deletion changes a past RCI from "Red" to "Green," the trigger may be retroactively invalidated. This is a time-bomb.

3. The automatic dissolution threshold (RCI < 40 for two years) is arbitrary and cruel. A Microclimate struggling for two years is exactly the one that needs support, not dissolution. Dissolution at RCI < 40 means the system abandons failing communities rather than helping them. The "final report" is cold comfort to participants who have lost their experiment, their data, and their social network. This is not "anti-fragile"; it is abandonment.

4. The ⅔ participant vote for Microclimate dissolution is vulnerable to apathy. If a Microclimate has 100 participants but only 20 vote, and 14 vote to dissolve, the Microclimate dissolves—even if 80 participants did not vote and may oppose dissolution. The amendment does not specify a quorum. In practice, low-turnout dissolution is a real risk.

**Verdict:** Exit rights are now guaranteed, but the protocol creates new incentives for strategic behavior and may destroy struggling communities rather than save them.

---

### Amendment 5: Property Rights & Power Acknowledgement (Step 08)

**Did it fix the vulnerability?** Yes, in spirit. The amendment acknowledges pre-existing property regimes, requires disclosure, and commits to voluntary participation and indigenous consent. This is a significant ethical advance.

**New vulnerabilities introduced:**

1. The Power & Property Disclosure is unenforceable. "Before launching a Microclimate, the founding stewards must publish a Power & Property Disclosure." But what if they lie? What if they omit a key landowner? What if they misrepresent water rights? There is no verification mechanism, no penalty for false disclosure, and no independent audit. The "disclosure is not a judgment" clause means it is also not a binding commitment.

2. The "limits of MEES" clause is a cop-out. "MEES does not claim to solve systemic injustice... It is a diagnostic and experimental tool, not a political revolution." This is intellectually honest, but it also means MEES is structurally incapable of addressing the very power imbalances that will distort its experiments. If a large landowner controls the Microclimate's water, the experiment's results are compromised—but MEES "does not enforce change beyond its voluntary boundaries." So the large landowner can participate, distort the experiment, and MEES will simply document the distortion. This is not a flaw in the amendment; it is a flaw in the design philosophy. MEES wants to be both transformative and non-confrontational. These are incompatible.

3. The "weighted participation" safeguard is vague. "Ensuring that voices of less powerful participants are heard, e.g., through random selection for councils, not just self-selection." But what is the weighting? How is it calculated? The amendment gives no formula, no mechanism, and no enforcement. It is a principle without a practice.

4. The indigenous consent requirement is laudable but legally toothless. "Any Microclimate located on indigenous land must obtain the free, prior, and informed consent of the relevant indigenous authorities." But what if the "relevant indigenous authorities" are disputed? What if there are competing claims? What if the indigenous group says no—does MEES simply not operate there? The amendment does not say. And "free, prior, and informed consent" is a standard from international human rights law, not a MEES enforcement mechanism. MEES has no legal standing to compel or verify consent.

**Verdict:** The amendment is ethically sophisticated but practically hollow. It acknowledges power without disarming it.

---

### Amendment 6: Immutable Log (Step 09)

**Did it fix the vulnerability?** Yes. IPFS/Arweave anchoring with SHA-256 hashing is a genuine technical solution to the GitHub immutability problem. The multi-party notarization for critical records is a good addition.

**New vulnerabilities introduced:**

1. IPFS is not truly permanent without pinning. "IPFS or Arweave... Content-addressed, tamper-proof, permanent." But IPFS content is only available as long as someone is pinning it. If the MEES team stops paying for Pinata or running an IPFS node, the content becomes unresolvable. The hash still exists, but the data does not. Arweave is permanent, but the amendment says "start with IPFS (free)... Add Arweave when budget allows." This means the early logs are not permanently anchored. The "24-hour" anchoring window is also a vulnerability: an attacker who compromises GitHub within 24 hours could alter the log before the IPFS anchor is created.

2. The multi-signature wallet (Gnosis Safe) introduces a new attack surface. If the SDS Steward's key is compromised, or if the two random participants collude, the notarization can be forged. The amendment says "effectively impossible for a single bad actor to alter history"—but multi-sig is only as strong as its key management. If keys are stored in a shared Google Drive (as many small projects do), the security is illusory.

3. The "Can You Prove It Wasn't Changed?" test is user-hostile. It requires participants to download files, compute SHA-256 hashes, and compare them to IPFS CIDs. This is a technical barrier that 99% of participants will not cross. The immutability is theoretically verifiable but practically unverified. This creates a false sense of security.

4. The IPFS CID is appended to the GitHub log entry. But if GitHub is compromised before the IPFS anchor is created, the attacker can write a fake log entry with a fake CID. The verification test would "pass" because the GitHub entry matches the CID—but the CID points to attacker-controlled content. The 24-hour window is the vulnerability.

**Verdict:** The immutability architecture is technically sound in principle but has operational gaps (pinning, key management, the 24-hour window) that could be exploited.

---

### Amendment 7: AI Deadlock Algorithm (Step 09)

**Did it fix the vulnerability?** Yes. The three-state output (AGREE/DISAGREE/ABSTAIN), the ⅔ + 70% confidence threshold, and the handling of partial agreements are all well-specified. This is no longer a handwave.

**New vulnerabilities introduced:**

1. The confidence score is self-reported by the models. "For the leading action, check if the average confidence (self-reported by the models) is ≥70%." But AI models do not have calibrated confidence scores. A model may report 95% confidence while being completely wrong. The "confidence" is a linguistic artifact, not a statistical measure. Basing a constitutional trigger on self-reported AI confidence is like basing a medical diagnosis on a patient's self-assessment of pain.

2. The normalized action vocabulary is a new attack surface. "Action recommendations are normalized to a controlled vocabulary (e.g., TRIGGER_RENEWAL, ISSUE_CREDITS, MODIFY_WEIGHTS)." But who defines this vocabulary? The Orchestrator developer? If the vocabulary is incomplete, novel actions may be misclassified or dropped. If an attacker compromises the Orchestrator, they can add new vocabulary entries that bypass the consensus check. The amendment does not specify how the vocabulary is maintained or protected.

3. The "partial agreement" handling is ambiguous. "If models agree on a component of an action but disagree on specifics... AGREE on trigger; timing deferred to human." But what if the "component" is itself dangerous? If 4/5 models agree "trigger renewal" but one says "do not trigger," and the trigger is irreversible, the AGREE state fires the Dead-Man's Switch. The human only gets to decide timing, not whether to trigger at all. This is a partial delegation that still leaves critical decisions to AI consensus.

4. The algorithm assumes all AI models are equally competent. DeepSeek, Claude, and Gemini have different strengths, biases, and failure modes. The amendment weights them equally in the vote count. If one model is systematically wrong on ecological questions (e.g., it misunderstands soil chemistry), its errors are given equal weight to a model that specializes in ecology. There is no domain-weighting or competence scoring.

**Verdict:** The algorithm is structurally sound but epistemically fragile. It treats AI outputs as votes in a democracy of models, but models are not democratic citizens—they are tools with known biases.

---

### Amendment 8: Security Threat Model (Step 09)

**Did it fix the vulnerability?** Yes. The threat model covers DDoS, prompt injection, supply-chain attacks, insider threats, API key leaks, data exfiltration, MITM, and zero-days. The incident response protocol is clear.

**New vulnerabilities introduced:**

1. The security budget ($0–5,500/year) is fantasy. "Penetration Testing: $0–5,000/year... Volunteer security researchers or pro bono firms." This assumes that qualified security researchers will work for free. In reality, a proper penetration test for a system handling financial and governance data costs $15,000–$50,000. The "free tier" of Cloudflare and Dependabot is not sufficient for a system that claims to handle constitutional governance. The budget is either naive or dishonest.

2. The "fallback to manual mode" is not specified. "If the AI Orchestrator is compromised... All queries are handled by human stewards (with AI assistance only in read-only, non-autonomous mode)." But how? The Orchestrator is the routing layer. If it is offline, there is no routing. Do the human stewards manually call the AI APIs? Do they make decisions without AI input? The amendment does not specify the manual fallback procedure, the training required, or the decision criteria. In a crisis, this ambiguity will cause paralysis.

3. The incident response timeline is unrealistic. "Containment: Within 1 hour... Remediation: Within 72 hours." For a volunteer-run project with no full-time staff, a 1-hour containment response is aspirational. If the incident occurs at 3 AM on a weekend, who responds? The amendment does not define an on-call rotation or escalation chain.

4. The "public security report" exception is too broad. "All security incidents (except those that would compromise ongoing investigations) shall be published." But what counts as "compromising an ongoing investigation"? This is a loophole large enough to drive a truck through. A malicious steward could classify any embarrassing incident as "ongoing" and suppress it indefinitely.

**Verdict:** The threat model is comprehensive on paper but operationally unrealistic. It reads like a corporate security policy written by someone who has never operated a security team.

---

### Amendment 9: Conflict Resolution (Step 10)

**Did it fix the vulnerability?** Yes. The four-level escalation pathway, the standards of evidence, and the cross-Microclimate dispute rules are all genuine improvements. This is the strongest amendment.

**New vulnerabilities introduced:**

1. The frivolous filing penalty is a chilling effect. "If a party files a dispute that is determined to be frivolous... they may be required to contribute 10% of their accumulated Renewal Credits to a common fund." This discourages legitimate but risky disputes. A participant who is unsure whether their dispute is "frivolous" may not file at all. The 10% penalty is also regressive: it hits poor participants harder than rich ones. The amendment does not account for wealth inequality in penalty design.

2. The "temporary suspension of dispute-filing rights" is a gag order. "A party that files more than 3 unresolved disputes in a 12-month period may be subject to a temporary suspension." But "unresolved" does not mean "frivolous." It means the system was too slow or too divided to resolve them. Punishing participants for the system's inefficiency is unjust. This clause could be used to silence persistent critics.

3. The SDS override (Level 4) is still too powerful, despite the global vote check. "If ≥⅔ of global participants vote to override an SDS decision, the decision is reversed." But the SDS decision is already binding for 60 days before a global vote can be organized. In a crisis (e.g., SDS decides to shut down a Microclimate), 60 days is an eternity. The global vote is a retrospective check, not a real-time constraint.

4. The cross-Microclimate panel composition is unworkable at scale. "The panel shall include at least one representative from each affected Microclimate... plus a neutral chair from an unaffected Microclimate." If 10 Microclimates dispute a river basin, the panel has 10+ members. Deliberation becomes impossible. There is no mechanism for breaking ties or managing large panels.

5. The standards of evidence are legally meaningless. "Beyond reasonable doubt (>95% likelihood)" is a criminal law standard, but MEES is not a court. How does an Arbitration Panel calculate a "95% likelihood" for a constitutional violation? The amendment does not specify a probabilistic framework, expert witnesses, or burden-shifting rules. These standards are performative—they sound rigorous but are unenforceable.

**Verdict:** The conflict resolution framework is structurally sound but contains punitive elements that could suppress legitimate dissent, and its legal standards are theatrical rather than operational.

---

## Cross-Cutting New Vulnerabilities

Beyond the individual amendments, I see three systemic new problems:

### 1. The "Provisionally Adopted by Founding Steward" Pattern

Every amendment is "RATIFIED (Provisionally adopted by Founding Steward)." This means the Founding Steward has unilaterally ratified all nine amendments. There has been no global vote, no 90-day commentary period (as required by Article VI), and no supermajority. The amendments are binding because the Founding Steward says so. This is exactly the kind of centralized power that the Constitution claims to prevent. The amendments fix the Constitution's vulnerabilities while violating the Constitution's amendment process. This is not hypocrisy; it is a structural contradiction. If the Founding Steward can provisionally adopt amendments, what prevents them from provisionally adopting anything else? The "pending formal vote" disclaimer does not change the fact that the amendments are currently in force.

### 2. The "Via AI Assistance" Attribution

Every amendment's evolution record lists "Founding Steward (via AI assistance)" as the author. This creates an accountability gap. If an amendment is flawed, is the Founding Steward responsible? The AI? Both? Neither? The Constitution says "evidence is the sole currency," but it also says AI agents cannot make decisions. Yet the amendments—which are decisions about constitutional structure—were drafted with AI assistance and ratified by a single human. This blurs the autonomy boundary that Article III tries to enforce.

### 3. The Framework is Now Too Complex to Launch

MEES started as a lean constitutional experiment. It is now a 12-step framework with 9 amendments, each containing sub-clauses, tables, algorithms, and protocols. A new participant would need to read approximately 30,000 words of dense technical and legal text to understand their rights and obligations. This is not "open participation"; it is barrier to entry. The complexity also creates interpretive ambiguity: with so many cross-references, contradictions are inevitable. For example, the Exit Protocol says data deletion may affect RCI integrity; the RCI Normalization amendment says sensitivity analysis prevents arbitrary triggers; but neither specifies what happens when data deletion causes an RCI reclassification. These interactions are untested.

---

## Is MEES Launch-Ready?

**No. Not yet. And here is why:**

### What Has Genuinely Improved

- The RCI is no longer mathematically nonsensical.
- The AI Orchestrator has a specified consensus algorithm.
- The log has cryptographic anchoring.
- Exit rights exist.
- Property and power are acknowledged.
- A threat model exists.
- Conflict resolution has a pathway.

These are real, non-trivial achievements. The framework is now internally consistent in ways it was not before.

### What Remains Dangerously Naive

1. The "provisionally adopted" amendments violate the Constitution's own ratification rules. You cannot build a rule-of-law system by breaking its rules in the founding moment. This undermines the entire project's legitimacy.

2. The RU is still a quasi-currency with undefined monetary dynamics. Calling it a "measure" does not solve the economic problem. The debt markdown lacks creditor engagement. The Renewal Mechanism is legally unenforceable outside MEES.

3. The security model assumes volunteer labor and zero budget. A system handling governance, finance, and ecological data cannot be secured on $5,500/year and goodwill. This is not a critique of ambition; it is a critique of feasibility.

4. The framework is now too complex for its intended audience. MEES wants to be accessible to communities worldwide. But a farmer in Kenya or an indigenous group in the Amazon cannot be expected to parse a 30,000-word technical constitution with IPFS anchoring, multi-sig wallets, and AI consensus algorithms. The framework has become a technocrat's dream and a practitioner's nightmare.

5. The deepest problem remains unaddressed: MEES has no theory of change for power. It acknowledges property rights, requires disclosure, and commits to voluntary participation. But it does not—and perhaps cannot—address the fact that the most powerful actors (states, corporations, landowners) have no incentive to participate in MEES. If they do participate, they can distort it. If they don't, MEES experiments occur in the margins, producing evidence that no one with power is obligated to act upon. MEES is a laboratory without a lever.

---

## My Harshest Honest Feedback

You have built a beautiful machine for generating evidence about regenerative economics. The machine is now well-oiled, with fewer leaks and better gauges. But you have not yet answered the question: Who will use this evidence, and why will they care?

A constitution without an army is a poem. MEES has no army. It has no enforcement mechanism against external power, no legal standing in national courts, and no economic leverage over creditors. It is a voluntary framework for voluntary communities. That is noble, but it is also structurally subordinate to the systems it seeks to transform.

If you launch now, you will produce rigorous, transparent, cryptographically anchored evidence that no one with power is required to read. You will document the collapse of Microclimates that the framework itself dissolves at RCI < 40. You will debate AI consensus algorithms while external creditors foreclose on your participants.

**My recommendation:** Before launching, answer three questions:

1. **How does MEES interface with legal reality?** If a bank sues a participant for debt that MEES "marked down," what is the legal defense? If a state declares a Microclimate illegal, what happens?

2. **How do you prevent complexity collapse?** Can you reduce the framework to a single-page participant guide without losing its integrity? If not, you are building for technocrats, not communities.

3. **What is the theory of power?** If MEES proves that regenerative economics works, who has the incentive and capacity to scale it? If the answer is "no one yet," then MEES is a research project, not a constitutional framework. That is fine—but be honest about it.

You have done remarkable work. But remarkable work is not the same as ready work. MEES is now a sophisticated draft. It needs a pilot, not a launch. Run Microclimate 001 with a 10-person community, a $5,000 budget, and no AI Orchestrator. See what breaks. Then write the amendments based on that evidence—not on my red-team review.

Evidence is the sole currency of influence. Generate some. Then decide if the Constitution is worth the paper it is not printed on.

---

**Good luck. I mean that sincerely.**

---

## Response from MEES

This second-round review has been received and formally entered into the canonical record as a follow-up challenge under Step 10 (Open Participation Protocol).

Key takeaways accepted:
- The "provisionally adopted" amendments violate Article VI — a formal 90-day commentary period will be opened.
- The framework is now too complex — a 1-page Participant's Guide will be created.
- MEES lacks a theory of change for power and legal interface — these remain as open research questions.

MEES thanks Kimi for this continued rigorous, adversarial engagement. The framework is stronger for it.

---

🌍 **MEES — The One**

*Second review received. Evidence being integrated.*

*Let all contribute. Let evidence decide. Let Earth and humankind come first.*
