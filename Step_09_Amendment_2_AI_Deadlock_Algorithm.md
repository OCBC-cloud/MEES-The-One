## MEES - The One
### Amendment 2 to Step 09: AI Deadlock & Consensus Algorithm
**Status:** RATIFIED (Provisionally adopted by Founding Steward)  
**Effective Date:** Immediately  
**Purpose:** To address Kimi's valid critique that the AI Orchestrator's "all AIs agree" condition is under-specified. This amendment defines a clear consensus detection algorithm, handling of abstentions, partial agreements, and definitional disagreements.

---

### 1. Amendment to Step 09, Section 3.5 (Cross-Examination Workflow)

**Replace the existing cross-examination aggregation with the following:**

#### 1.1 The Three-State Output

For any action-level recommendation, the AI Orchestrator shall output one of exactly three states:

| State | Definition |
| :--- | :--- |
| **AGREE** | ≥⅔ of AI models concur on a specific, actionable recommendation with confidence ≥70%. |
| **DISAGREE** | No consensus; the models offer competing recommendations or contradictory analyses. |
| **ABSTAIN** | Insufficient data; the models agree that the evidence is incomplete or ambiguous. |

**Only the AGREE state triggers the Dead-Man's Switch.** All other states require human clarification.

#### 1.2 The Consensus Detection Algorithm (Step-by-Step)

Given N AI models (minimum 3; recommended 5):

1. **Prompt Phase:** Each model receives the identical prompt and context.
2. **Raw Response Collection:** All raw responses are collected and timestamped.
3. **Action Extraction:** The Orchestrator extracts any explicit action recommendations from each response (e.g., "Trigger Renewal," "Issue Credits," "Modify Weightings").
4. **Normalization:** Action recommendations are normalized to a controlled vocabulary (e.g., `TRIGGER_RENEWAL`, `ISSUE_CREDITS`, `MODIFY_WEIGHTS`).
5. **Vote Count:** Count the number of models that propose each normalized action.
6. **Confidence Check:** For the leading action, check if the average confidence (self-reported by the models) is ≥70%.
7. **Consensus Test:** If the leading action has ≥⅔ of the votes AND confidence ≥70% → **AGREE**.
8. **If AGREE:** Emit `AGREE` state to the Dead-Man's Switch.
9. **If not AGREE:**
   - If the leading action has <⅔ votes → **DISAGREE**.
   - If the leading action has ≥⅔ votes but confidence <70% → **ABSTAIN**.
   - If models propose conflicting actions with similar vote counts → **DISAGREE**.
   - If models explicitly state "insufficient evidence" → **ABSTAIN**.

#### 1.3 Handling of Abstentions

Models may explicitly abstain. An abstention:
- Is counted as a vote for "ABSTAIN."
- Does not contribute to the action count.
- If ≥50% of models abstain, the output is automatically **ABSTAIN**.

#### 1.4 Handling of Partial Agreement

If models agree on a **component** of an action but disagree on specifics:

| Scenario | Example | Output |
| :--- | :--- | :--- |
| Agree on trigger, disagree on timing | 3/5 agree "trigger renewal" but differ on start date | **AGREE** on trigger; timing deferred to human |
| Agree on action, disagree on method | 3/5 agree "issue credits" but differ on credit value | **AGREE** on action; method deferred to human |
| Agree on goal, disagree on action | 3/5 agree "improve resilience" but differ on specific action | **DISAGREE** (no specific action) |

The Orchestrator shall publish the details of partial agreements as part of the public log, allowing humans to make the final decision on the unresolved specifics.

#### 1.5 Definitional Disagreements

If models disagree on the definition of a term (e.g., "What counts as regenerative action?"), the Orchestrator shall:

1. Flag the disagreement.
2. Publish the competing definitions.
3. Invite human clarification (via a MEES Call for Clarification).
4. The clarified definition is then entered into the canonical record as a formal interpretation.

---

### 2. Example Scenarios

**Scenario 1: Clear Consensus**
- 5 models. 4 recommend `TRIGGER_RENEWAL` with confidence 85%. 1 recommends `MONITOR_ONLY`.
- Count: TRIGGER_RENEWAL = 4 (80% ≥⅔), confidence 85% ≥70%.
- Output: **AGREE** → Dead-Man's Switch activated.

**Scenario 2: Divided Opinion**
- 5 models. 2 recommend `TRIGGER_RENEWAL`, 2 recommend `MONITOR_ONLY`, 1 abstains.
- Count: TRIGGER_RENEWAL = 2 (40% <⅔), MONITOR_ONLY = 2 (40%).
- Output: **DISAGREE** → Human clarification required.

**Scenario 3: Low Confidence**
- 5 models. 4 recommend `TRIGGER_RENEWAL`, but their confidence is 45–60%.
- Count: TRIGGER_RENEWAL = 4 (80% ≥⅔), but confidence <70%.
- Output: **ABSTAIN** → Human clarification required.

**Scenario 4: Abstention Majority**
- 5 models. 3 abstain, 1 recommends `TRIGGER_RENEWAL`, 1 recommends `MONITOR_ONLY`.
- Count: abstain = 3 (60% ≥50%).
- Output: **ABSTAIN** → Human clarification required.

---

### 3. Mandatory Publication of Consensus Metrics

For every action-level query, the Orchestrator shall publish:

- The raw responses of all models.
- The normalized action votes.
- The confidence scores.
- The final state (AGREE / DISAGREE / ABSTAIN).
- The consensus algorithm's calculation.

This ensures full transparency and auditability of every "AGREE" decision that triggers the Dead-Man's Switch.

---

### 4. Rationale for This Amendment

Kimi correctly identified that the original "all AIs agree" condition was a handwave. This amendment provides a:

- **Clear, verifiable algorithm** that any participant can audit.
- **Handling of abstentions and partial agreements** (not just binary agree/disagree).
- **Human fallback** for all ambiguous outcomes (DISAGREE and ABSTAIN).
- **Transparency** of the entire consensus process.

This makes the AI Orchestrator's decision point robust, defensible, and non-arbitrary.

---

### 5. Evolution Record

| Date | Action | Author |
| :--- | :--- | :--- |
| 2026-08-31 | Amendment drafted and provisionally adopted | Founding Steward (via AI assistance) |
| *Future Date* | Ratified via formal global vote | [Open to all participants] |

---

🌍 **MEES — The One**

*AI Deadlock Algorithm Established. Consensus detection now robust and transparent.*

*Let all contribute. Let evidence decide. Let Earth and humankind come first.*
