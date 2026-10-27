# Livestock Ag-Tech Market Assessment: A GTM Engineering Pipeline

I built a five-stage go-to-market pipeline in Clay and Instantly for one niche: **B2B companies that sell to livestock producers** (herd management, livestock monitoring, animal health, genetics and marketplaces). Each stage is its own project with its own write-up, and each one measures its results.

This is a **test build on public company data**. There is no client data, and **no emails were sent**, so the numbers below are process metrics (list quality, accuracy, cost, setup quality), not sales outcomes. No names, emails or LinkedIn URLs are stored in this repo.

## The pipeline

```
ICP and account list  →  Lead enrichment  →  Lead scoring  →  Signals  →  Campaign setup
   (Project 1)            (Project 2)         (Project 3)     (Project 4)   (Project 5)
```

## Results at a glance

| Project | What I built | Headline result |
|---|---|---|
| [1. ICP and Account List](./project-1-icp-account-list) | A written ICP and a 50-account target list sourced in Clay | Hand-checked pass rate rose from **30% to 60%** (70% on relevance alone) after I changed the search from industry labels to description keywords |
| [2. Lead Enrichment](./project-2-lead-enrichment) | Decision-makers and work emails for the accounts | **26 of 50** companies with a hand-verified contact (52%); **23 emails** found, all validated; about **0.9 credits per contact** |
| [3. Lead Scoring](./project-3-lead-scoring) | A transparent 100-point rubric with fit and reachability groups | 26 contacts scored from **70 to 100**; 19 in Tier A, 7 in Tier B; the score columns cost no credits |
| [4. Signal-based Prospecting](./project-4-intent-signal-based-prospecting) | Hiring and news signals added to the score | Signals are sparse in this niche: **0 of 23** companies hiring for sales or marketing, **3 of 23** with fresh news |
| [5. Campaign Setup](./project-5-cold-email-campaign-setup) | Two audience-specific draft campaigns with deliverability settings | 23 contacts split into 20 and 3 so no one is emailed twice; SPF, DKIM and MX pass, DMARC monitor-only; **nothing sent** |

The whole build used about **36 of 1,000 free Clay credits** (roughly 4%).

## What this shows

- **Define the rule first.** Fit criteria, "fresh news" and "hiring" were all written down before I looked at results, so I could not bend them to fit the data.
- **Test small, then scale.** Every paid lookup ran on 5 rows first, with the cost estimate read and the balance checked, before I ran the rest.
- **Hand-check and report honestly.** I verified samples by hand (companies, contacts, news articles, job postings) and reported misses: 52% coverage, sparse signals, a 30% first pass rate.
- **Work around tool limits.** A function with no title filter, dropdown fields stored as IDs, a 50-row table cap and a location filter that matched any office each changed how I built things.
- **Protect people and sender reputation.** One contact per company, no personal data in the repo, tracking off, text-only email, a low daily limit, and campaigns left unlaunched until warm-up and compliance are ready.

## Biggest lessons

1. **Industry labels are too broad for a niche.** Description keywords found the right companies; the industry filter pulled in crop tech and hydroponics.
2. **Verified is not the same as predictive.** My score ranks "verified and reachable," and its weights are assumptions. It needs reply data to calibrate.
3. **Empty results are results.** Most companies had no hiring signal and no fresh news, and reporting that is more useful than forcing a signal.
4. **Check for double sends.** My first draft campaigns held the same contacts, so I split the lists before anything could launch.

## Tools and skills

Clay (company and people search, email waterfall enrichment, formula columns, Sandbox, signals, usage tracking), Instantly (campaign sequencing, deliverability settings, DNS checks), JavaScript formulas, GitHub documentation, and cost control.

## What I would do next

- Warm up a mailbox on a matching domain and send a small US-only batch of the top-scored contacts.
- Calibrate the scoring weights against real reply data.
- Run a broader second pass for the 23 companies with no contact, and refresh signals on a schedule.

## About

Built by Denise B as part of a move into GTM Engineering. Connect on LinkedIn: https://www.linkedin.com/in/deniseb7
