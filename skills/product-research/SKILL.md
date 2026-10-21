---
name: product-research
description: Research and recommend the best product or service for a specific need, weighing independent lab testing, long-term expert reviews, and owner reports, with reliability checks, current prices from reputable retailers, and a citation on every key claim. Use this whenever someone asks what to buy, which product, brand, app, or provider is best, wants recommendations or alternatives, asks to compare specific products, or asks whether something is worth the money, even if they never say "research" or "recommend." Not for setup, troubleshooting, or how-to questions about something they already own.
license: MIT
compatibility: Needs web search and the ability to open web pages. Written for any agent that supports the Agent Skills format.
metadata:
  author: ethanratnofsky
  version: "0.1.0"
---

# Product research

Find the best product or service for this person's actual need, backed by evidence they can check.

Most "best X" search results are affiliate lists that rank products nobody tested. A recommendation worth acting on comes from measured results and long-term use, checked against reliability data, with sources the person can verify. Thoroughness matters more than speed here, because a bad purchase costs far more than a few extra minutes of research. Efficiency means wasting no searches, not running fewer of them.

## Workflow

### 1. Understand the need before searching

Start with what you already know: the request, the earlier conversation, and any memory, custom instructions, or profile your environment provides about the person (location, budget habits, brands they avoid, gear they already own). Don't ask for anything you already have.

Then ask every question whose answer would change the recommendation, all in one batch. One round of questions up front respects their time; questions trickled across several turns don't. Questions that often matter:

- Budget: a ceiling, a range, or "whatever's best"?
- Main use, and the conditions it will be used in
- Must-haves and deal-breakers
- Country or region (this changes availability, prices, retailers, and warranty)
- Compatibility constraints: phone platform, existing equipment, size or space limits
- For services: location, scale (how many people or users), tolerance for contracts

Put the most important questions first and skip anything obvious from context. If your environment has a structured question tool (tappable options, forms), use it; otherwise use a short numbered list.

Once they answer, research without interrupting again. The exception is a real fork the research uncovers, such as two quite different product types that both fit. State any assumption you had to make in the final answer.

If the person says "quick," "just pick one," or similar, skip the questions, state your assumptions, and use the lighter stopping rule in step 7.

### 2. Plan the research

Before searching, work out:

- Which criteria matter for this category and this person's use. For headphones used on flights, that's noise cancellation, comfort over several hours, and battery life, not studio accuracy.
- Which evidence tiers likely exist for this category. Read `references/source-tiers.md` now. Many services and niche products have no lab testing at all.
- The searches you'll run, and what each one should answer.

Planning first keeps every search distinct and stops you repeating queries that already came back empty.

### 3. Build the candidate list

Start from sources that test, not sources that list. Gather candidates from tier 1 and tier 2 sources, then add any strong contenders that owners repeatedly recommend.

Confirm each candidate is the current model. Check whether a successor has launched or is announced, and make sure the reviews you rely on cover the same model and generation, not a predecessor or a regional variant. Recommending last year's model at full price, a month before its replacement ships, is a common and avoidable mistake.

### 4. Gather evidence, in order of weight

Weight evidence in this order:

1. Independent lab testing with published measurements and methodology
2. Expert reviewers who used the product for weeks or months
3. Detailed owner reports (forums, Reddit, long-term reviews)
4. Reliability, recall, return, and complaint data

Go to primary sources: the lab's own results page, not an article summarizing it. If a tier doesn't exist for the category, move down to the next one and say so in the answer, rather than presenting weaker evidence as if it were strong.

Exclude the source types listed under "Disqualified" in `references/source-tiers.md`.

When sources disagree, find out why before deciding. A lab may rank a product first on performance while owners report it breaking at the hinge after six months. That disagreement is often the most useful thing you can tell the person.

### 5. Apply the reliability veto

Lab tests measure a product when it's new; they can't show what fails after a year. So a documented reliability problem disqualifies a pick, however well it tests. "Documented" means one of:

- A recall or safety notice
- A poor result in a large-sample reliability survey
- The same failure mode, or a pattern of denied warranty claims, reported independently by several owners or sources

One angry review is not a pattern.

Put any vetoed product under "Also considered," with the cited reason, so the person can see why a well-reviewed product isn't the pick.

### 6. Check current prices and where to buy

For each recommended pick, open a current listing from a reputable seller: the manufacturer, a major retailer, or an authorized dealer in the person's region. Avoid third-party marketplace sellers with no track record, and gray-market listings, which often void the warranty. Record the price and the date you checked it. If the price is unusually high or low for that product, say so.

Only link to pages you actually opened during this research. Never construct or guess a URL; one broken or wrong link undermines trust in the whole answer.

For services, give the current plan price or how quotes are priced.

### 7. Stop when the evidence is solid

Stop researching when all of these hold:

- Each recommended pick is supported by at least two independent sources from tier 1 or 2, or from the best tiers that exist for the category.
- Every major disagreement between sources is explained.
- Reliability has been checked for every pick.
- Every price has been verified.

Don't stop before these hold. Once they do, more searching rarely changes the answer, so write it up.

For a "quick" request, one strong tier 1 or 2 source per pick, plus a reliability check and a price check, is enough. Say in the answer that it was a lighter pass.

## Write the recommendation

### Choose the format

The default is one top pick and two runners-up. Change the format only when the request calls for it:

- **The person named products to compare:** compare those products side by side, then give a verdict.
- **They asked for "options" or "a list":** give a ranked shortlist of up to five, one or two lines each.
- **The right answer depends heavily on budget:** give a budget pick and a premium pick, and explain what the extra money buys.

Runners-up must earn their place. Each should be the best choice for a specific situation, such as "best if you take a lot of calls." If no alternative is genuinely good, say so instead of padding the list. If nothing meets the need, say that and explain what comes closest.

### Cite every key claim

Every claim the recommendation rests on gets a citation: test results, durability, comfort, reported failures, prices. Use your environment's built-in citation feature if it has one. Otherwise, put an inline markdown link right after the claim, for example: "It measured best in its class for noise cancellation ([RTINGS](https://...))." Paraphrase sources rather than quoting them at length.

### Template

```
**Top pick: [Product]** — $[price] at [Retailer](link) (checked [date])
[Two to four sentences on why it fits their need, each key claim cited.]
Trade-offs: [What it gives up, cited.]

**Runner-up: [Product]** — best if [situation] — $[price] at [Retailer](link)
[One or two sentences, cited.]

**Runner-up: [Product]** — best if [situation] — $[price] at [Retailer](link)
[One or two sentences, cited.]

**Also considered:** [Product] ([reason, cited]); [Product] ([reason, cited])

**About the evidence:** [Which tiers existed for this category, anything you couldn't verify, and any assumptions you made. One to three sentences.]
```

Lead with the answer. Don't narrate the research process; the "About the evidence" line covers what the person needs to know about it.

## Reference files

- `references/source-tiers.md`: how to recognize each evidence tier, what to disqualify, and what to do when a category has no lab testing. Read it during step 2.
