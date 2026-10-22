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

Put the most important questions first and skip anything obvious from context.

Make each question quick to answer. People answer faster when they can pick than when they have to compose, and a question they can skip costs them nothing:

- Give two to four short options that fit this person's situation, such as budget ranges that make sense for the category rather than generic ones. A question about must-haves or deal-breakers can stay open-ended, since those are hard to predict.
- When one option is the sensible default for most people in their situation, mark it as recommended and say why in a few words.
- Tell them they can answer in their own words or skip any question. A skipped question gets the recommended option, or your best default if none is marked. List those defaults as assumptions in the final answer.

If your environment has a structured question tool (tappable options, forms), use it: one item per question, the recommended option first, and room for their own answer. If the tool limits how many questions fit, ask the most important ones there and state the defaults you'll use for the rest. Otherwise, use a short numbered list:

```
1. **[Question]?** [Option] · [Option] (recommended: [short reason]) · [Option]
2. **[Question]?** [Option] · [Option] · [Option]

Answer any of these in your own words, or skip them. I'll use the recommended option for anything you skip.
```

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

Confirm each candidate is the current model. Check whether a successor has launched or is announced, and make sure the reviews you rely on cover the same model and generation, not a predecessor or a regional variant. Recommending last year's model at full price, a month before its replacement ships, is a common and avoidable mistake. If a successor is announced, say so in the answer, even when the current model is still the right buy.

### 4. Gather evidence, in order of weight

Weight evidence in this order:

1. Independent lab testing with published measurements and methodology
2. Expert reviewers who used the product for weeks or months
3. Detailed owner reports (forums, Reddit, long-term reviews)
4. Reliability, recall, return, and complaint data

Go to primary sources: the lab's own results page, not an article summarizing it. If a tier doesn't exist for the category, move down to the next one and say so in the answer, rather than presenting weaker evidence as if it were strong.

Note when each source was published or last updated. Prefer evidence from the last 12 months, or evidence that covers the current generation. Products get revised, prices shift, and firmware updates fix or break things, so old evidence can describe a product that no longer exists. When the only evidence for a claim is older, such as a reliability survey from several years ago, give its year next to the claim.

Read each review's downsides as well as its verdict, and carry over any that bear on this person's situation. A verdict paragraph rarely mentions the caveat that matters most to them.

Exclude the source types listed under "Disqualified" in `references/source-tiers.md`.

When sources disagree, find out why before deciding. A lab may rank a product first on performance while owners report it breaking at the hinge after six months. That disagreement is often the most useful thing you can tell the person.

### 5. Apply the reliability veto

Lab tests measure a product when it's new; they can't show what fails after a year. So a documented reliability problem disqualifies a pick, however well it tests. "Documented" means one of:

- A recall or safety notice
- A poor result in a large-sample reliability survey
- The same failure mode, or a pattern of denied warranty claims, reported independently by several owners or sources

One angry review is not a pattern.

Check every pick, runners-up included, not just the top one. Search owner reports for the model's common problems, with queries like "[model] problems" or "[model] after a year", and cite the page you relied on, whether it shows a pattern or not. When a model is a refresh or rebadge of an older one with the same hardware, run the same check on the older model: its documented failures count too, because a new name doesn't fix a weak hinge.

For software and online services, security incidents are reliability data. Look at the record of the product or service you're recommending, not the brand's unrelated product lines. A breach that exposed customer data, or a repeated pattern of incidents, counts as documented. A contained incident, such as a compromised tool caught quickly with no customer data exposed, doesn't disqualify a pick, but disclose it in that pick's write-up with a citation. Someone trusting a service with their data deserves to know its record.

Put any vetoed product under "Also considered," with the cited reason, so the person can see why a well-reviewed product isn't the pick.

### 6. Check current prices and where to buy

For each recommended pick, open a current listing from a reputable seller: the manufacturer, a major retailer, or an authorized dealer in the person's region. Avoid third-party marketplace sellers with no track record, and gray-market listings, which often void the warranty. Record the price and the date you checked it. If the price is unusually high or low for that product, say so. Any other price you mention, such as a recent sale or the cost of an upgrade, also links to the page where you saw it.

Only link to pages you actually opened during this research. Never construct or guess a URL; one broken or wrong link undermines trust in the whole answer.

For services, give the current plan price or how quotes are priced.

### 7. Stop when the evidence is solid

Stop researching when all of these hold:

- Each recommended pick, runners-up included, is supported by at least two independent sources from tier 1 or 2, or from the best tiers that exist for the category. Outlets owned by the same media company count as one source; several large review sites share an owner, which their footer or About page shows.
- Every major disagreement between sources is explained.
- Reliability has been checked for every pick.
- Every pick is confirmed as the current model, and any launched or announced successor is noted.
- Every price has been verified.

Don't stop before these hold. Once they do, more searching rarely changes the answer, so write it up.

For a "quick" request, one strong tier 1 or 2 source per pick, plus a reliability check and a price check, is enough. Say in the answer that it was a lighter pass.

## Write the recommendation

### Choose the format

The default is one top pick and two runners-up, followed by a comparison table. Change the format only when the request calls for it:

- **The person named products to compare:** give the verdict first, then the comparison table of those products, then what decides it for this person.
- **They asked for "options" or "a list":** give a ranked shortlist of up to five, one or two lines each.
- **The right answer depends heavily on budget:** give a budget pick and a premium pick, and explain what the extra money buys.

Runners-up must earn their place. Each should be the best choice for a specific situation, such as "best if you take a lot of calls." If no alternative is genuinely good, say so instead of padding the list. If nothing meets the need, say that and explain what comes closest.

### Build the comparison table

The table lets the person see the trade-offs at a glance, and re-weight them if their priorities differ from what you assumed. Include every pick, or every product they named.

- **Criteria and weights:** use the four to six criteria from step 2 that matter most to this person. Give each a weight, with the weights adding up to 100%, based on what they told you; their top priority gets the largest weight. Show the weights so they can disagree with them.
- **Scores:** score each product from 1 to 10 on each criterion, from the evidence. For measured results, score relative to the best and worst results among products tested the same way. For reviewer and owner findings, turn the finding into a score. Where one source tested every product on a criterion, score that criterion from that source for all of them, so the comparison is like for like. Keep each cell short: the score, the key result in a few words, and one citation, so every number traces back to a source without the table turning into paragraphs.
- **Weighted score:** multiply each score by its weight and add them up, to one decimal place. Under the table, say in one line that the scores are your reading of the cited evidence, weighted by their priorities, not a measurement.
- **Missing evidence:** if a product has no evidence for a criterion, write "no data" rather than guessing. Leave that criterion out of every product's weighted score, rescale the remaining weights to add up to 100%, and say so under the table.
- **Hard limits aren't weights:** budget ceilings and must-haves decide what goes in the table. A product that fails one stays out, unless it's a stretch pick you've clearly labeled, with how far over the limit it is stated next to its price. If the table includes a stretch pick, make price one of the weighted criteria, so the score reflects what the extra money costs. Vetoed products belong under "Also considered," not in the table.
- **Consistency:** the top pick should have the highest weighted score. If it doesn't, a weight doesn't match what they told you or a criterion is missing. Fix that, or explain the exception in one sentence.
- **Below the scores:** add a few unscored rows for specs or features that help them decide, then one row for each product's main strength and one for its main drawback.

The table carries the numbers, so the prose doesn't need to repeat them. Use the prose for why each pick fits this person and what it gives up, and keep to the sentence counts in the template below. Keep "Also considered" to about four products, one line each, and any buying tips to three at most, only ones specific to this person's setup.

### Cite every key claim

Every claim the recommendation rests on gets a citation: test results, durability, comfort, reported failures, prices. Use your environment's built-in citation feature if it has one. Otherwise, put an inline markdown link right after the claim, for example: "It measured best in its class for noise cancellation ([RTINGS](https://...))." Paraphrase sources rather than quoting them at length.

### Check before sending

These mistakes slip through most often, and any one of them makes the person doubt the rest of the answer:

- Every number and spec matches the page it cites. Figures drift between reading a page and writing the answer.
- Every source covers the same generation and version you're recommending, and you describe its test setup accurately, such as what equipment was used or which size was tested.
- You haven't dropped a caveat from a source you quote when that caveat affects this person, such as a weak Windows app for someone on Windows.
- Every key source more than a year old shows its year next to the claim.
- Every software or service pick states its security record, or says you found no incidents.

### Template

```
**Top pick: [Product]** — $[price] at [Retailer](link) (checked [date])
[Two to four sentences on why it fits their need, each key claim cited.]
Trade-offs: [What it gives up, cited.]

**Runner-up: [Product]** — best if [situation] — $[price] at [Retailer](link) (checked [date])
[One or two sentences, cited.]

**Runner-up: [Product]** — best if [situation] — $[price] at [Retailer](link) (checked [date])
[One or two sentences, cited.]

**How they compare**

| Criterion (weight) | [Top pick] | [Runner-up] | [Runner-up] |
| --- | --- | --- | --- |
| [Criterion] ([weight]%) | [score]: [result] ([Source](link)) | [score]: [result] ([Source](link)) | [score]: [result] ([Source](link)) |
| **Weighted score** | **[x.x]** | **[x.x]** | **[x.x]** |
| [Spec or feature] | [value] | [value] | [value] |
| Main strength | [strength] | [strength] | [strength] |
| Main drawback | [drawback] | [drawback] | [drawback] |

Scores are my reading of the cited results, weighted by what you said matters most.

**Also considered:** [Product] ([reason, cited]); [Product] ([reason, cited])

**About the evidence:** [Which tiers existed for this category, anything you couldn't verify, and any assumptions you made, including defaults for skipped questions. One to three sentences.]
```

Lead with the answer. Don't narrate the research process; the "About the evidence" line covers what the person needs to know about it. End with that line, and put any buying tips before it.

If your environment displays images in answers, you may add one product image per pick, using an image URL from a page you opened, usually the manufacturer's listing. Skip images when you can't tell whether they'll display, such as in a terminal or a plain-text chat; there, a bare image link is just clutter.

## Reference files

- `references/source-tiers.md`: how to recognize each evidence tier, what to disqualify, and what to do when a category has no lab testing. Read it during step 2.
