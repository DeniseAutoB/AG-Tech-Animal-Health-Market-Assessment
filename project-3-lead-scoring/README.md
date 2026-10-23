# Project 3: Lead Scoring

Part 3 of 5 in a GTM pipeline built in Clay: ICP and account list → lead enrichment → **lead scoring** → signal-based prospecting → cold email campaign.

## Goal

Give every contact a score from 0 to 100 so outreach can start with the best-fit, most reachable people first, using a rule that is transparent and easy to explain.

This is a test build on public company data. **No names, emails or LinkedIn URLs are stored in this repo.**

## The rubric (100 points)

| Group | Factor | Points |
|---|---|---|
| **Account fit (60)** | Hand-verified fit | 30 if the company passed my hand check, 15 if it was not checked, 0 if it failed |
| | Company size | 15 for 11-50 employees, 10 for 51-200 |
| | Ownership | 15 privately held, partnership or self owned; 5 public company |
| **Reachability (40)** | Persona (from job title) | 25 founder, owner, CEO, managing director, general manager, or sales, commercial or revenue leader; 20 marketing or growth; 15 business development or operations; 5 other |
| | Email | 15 if an email was found, 0 if not |

**Tiers (preset cutoffs, not validated):** A is 80 or more, B is 60 to 79, C is below 60.

## Method

1. Scored in the **people table**, because the campaign emails people, so one row is one email.
2. Pulled company fields (type, size, verification status) from the linked company record instead of copying values, so the company table stays the single source of truth.
3. Built four formula columns so each part of the score is visible: **Fit Points**, **Reach Points**, **Lead Score** and **Tier**.
4. Checked the formulas against hand calculations on sample rows before filling the table.

## Results

| Measure | Result |
|---|---|
| Contacts scored | 26 |
| Score range | 70 to 100 |
| Tier A / B / C | 19 / 7 / 0 |
| Top score | 100 (3 contacts tied) |
| Companies hand-verified | 8 of 26 |
| Contacts with an email | 23 of 26 |

**What drives the differences:** hand verification (+15), an email on file (+15) and the persona. The score ranks "verified and reachable" above "unverified," not "likely to buy."

**Why contacts land in Tier B:** three have no email, three have weaker personas (a marketing lead, a CFO who also covers business development, and a COO), and one has low company points (unverified, 51-200 and a public company).

## Lessons learned

1. **Dropdown fields store IDs, not labels.** My size comparison matched nothing because the company size is stored as an option ID, not the text "11-50". Inspecting the cell details showed the real value, and I mapped the two size options to their IDs.
2. **Unverified is not failed.** I hand-checked only 20 companies at the start, so most show "Incomplete". The rubric scores them neutral (15 of 30) so they are not penalized for missing evidence.
3. **Split the score into columns.** Separate fit and reachability columns make the number explainable and easy to debug.
4. **Preset cutoffs did not discriminate.** The list was already filtered and verified, so most contacts landed in Tier A. I am reporting that as a finding, not tuning the cutoffs to look better.
5. **Out-of-date flags are not errors.** Some formula cells showed a clock icon after upstream data finished updating. Re-running the formula columns clears them.

## Limitations

- **The weights are my assumptions.** I have no reply or meeting data, so the score's predictive power is unproven. It is a transparent rubric, not a validated model.
- **Cutoffs are presets** and were not tested against an independent ranking.
- **Verification coverage is 8 of 26 companies,** so the "hand-verified" factor separates only a minority.
- **"Public company" is a rough proxy.** Some small companies carry that label and lose points for it.
- **Persona matching uses title keywords,** so unusual titles can be mis-scored (for example a "Vice President" outside sales).
- **The size mapping depends on this table's option IDs** and would need updating if those options were recreated.

## What I would do next at scale

- Calibrate the weights against real reply and meeting data.
- Hand-verify the remaining companies, or use an AI column to judge livestock relevance for every row and spot-check it.
- Add intent signals (hiring, funding, news) as a third scoring group.

## Cost and effort
- Credits used for this project: 11.6 (starting balance 988, ending balance 976.4). 

## Screenshots

![Find People List](screenshots/complete-and-final-people-list/png)

The campaign setup uses these scores to decide who is contacted first.
