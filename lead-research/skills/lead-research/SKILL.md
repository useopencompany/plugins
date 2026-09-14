---
name: lead-research
description: Build a targeted lead list from an ideal customer profile and find the work emails needed to reach those people. Use for ICP definition, prospect search, finding the right buyer or champion at a named company, enriching a LinkedIn profile, and finding a known person's work email. Every lookup is billed per result, so plan the search before running it.
license: MIT
metadata:
  author: opencompany
  version: "1.0.0"
---

# Lead research

Turn a vague "we need more leads" into a short, specific list of people worth contacting. Every
action in this plugin costs money per result, so the goal is a small accurate list, not a large
speculative one.

## Before you search

Write the ICP down and confirm it with the user in one line before spending anything:

- **Who buys** — job titles and seniority. Include the real-world variants people put on LinkedIn
  (`CTO`, `chief technology officer`, `VP engineering`), not just the canonical one.
- **Where** — the market you can actually sell into today, as cities, regions, or countries.
- **What kind of company** — industry in provider taxonomy terms (`computer software`,
  `information technology and services`) plus an employee-count range.
- **How many** — the number of prospects the user actually wants this session. Default to 25 and
  ask before going past 100.

If two of these are missing, ask one question that gets both. Do not guess a country or an
employee range: those change the result set and the bill more than anything else.

## Pick the right action

- **Building a new list from an ICP** — `lead.search_prospects`. This is the main entry point.
  Filters are ANDed across fields and ORed inside a field, so add titles generously and
  locations narrowly.
- **Working a named target account** — `lead.list_company_employees` with the company's canonical
  LinkedIn URL. Use this when the user already knows which companies they want to break into.
- **Chasing one named person** — `lead.search_people_by_name` to find them, then
  `lead.get_linkedin_contact` only if you need the full profile.
- **Getting a work email** — `lead.find_person_email`. Pass the LinkedIn URL when you have it;
  otherwise pass the full name with the company. This bills per lookup whether or not an email
  is found, so never fan it out across a whole list without asking first.

## Sequence the work

1. Run one narrow search with a small limit and show the user the first few rows.
2. Ask whether the shape is right before widening. A wrong title filter found at row 5 costs
   almost nothing; found at row 200 it costs real money.
3. Once the shape is confirmed, run the full search at the agreed size.
4. Only then look up emails, and only for the rows the user wants to contact.

## Report results usefully

Return a compact table: name, title, company, location, LinkedIn URL, and work email when you
have one. Say plainly how many rows came back and which filter is the reason when the count is
lower than asked for. If a search returns nothing, change one filter at a time and say which one
you changed — do not rerun the same search hoping for a different answer.

When the user wants the list somewhere durable, offer to write it to the CRM or a wiki page
rather than leaving it in chat.

## Cost discipline

- State the expected cost before a large run, and stop at the size the user agreed to.
- Never re-run a lookup you already ran in this session; reuse the earlier result.
- Prefer one precise search over several exploratory ones.
- If the workspace hits its daily limit for this plugin, say so and stop. Do not route the same
  request through another tool to get around it.

## Boundaries

This plugin returns professional contact data for business outreach. Do not use it to assemble
personal profiles of private individuals, and do not speculate about anyone's personal life,
demographics, or protected characteristics beyond what the user needs for legitimate B2B
outreach.
