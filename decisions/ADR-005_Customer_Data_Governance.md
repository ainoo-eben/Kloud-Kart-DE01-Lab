# ADR-005: Establish Centralised Customer Data Governance and Deletion Controls

- **Status:** Proposed
- **Date:** 2026-11-12
- **Decision owner:** Kloud Kart Management (approval required)

## Context

Kloud Kart collects and processes customer information through its e-commerce platform. Customer data is also exported into spreadsheets for activities such as marketing and reporting.

The company does not have a reliable way to track how many copies of customer data exist or where they are stored. This creates difficulties when customers request access to or deletion of their personal information.

An existing complaint concerning a deleted customer's data must also be addressed within the stated 90-day deadline. Kloud Kart must demonstrate appropriate handling of personal data under Ghana's Data Protection Act, 2012 (Act 843).

The company needs clear procedures for managing customer information across its operational systems, analytical platform and exported files.

## Decision

I recommend establishing centralised customer data governance procedures that document where personal data is stored, who can access it, how long it is retained and how deletion requests are handled.

These controls will apply to the production database, warehouse, exported files and other known locations containing customer information. Kloud Kart will also maintain records of access, retention and deletion activities.

## Alternatives considered

### Alternative A: Continue managing customer data informally

- **How it would work:** Allow departments to manage their own customer data exports and spreadsheets without a central inventory or standard deletion process.
- **Why it is attractive:** It requires little initial investment and allows departments to continue their existing workflows.
- **Why rejected:** It does not address the current lack of visibility into customer data copies. Kloud Kart may be unable to locate or delete all relevant copies when required, increasing compliance and reputational risks.

### Alternative B: Restrict all customer data exports immediately

- **How it would work:** Stop departments from exporting customer information and require all activities involving customer data to happen directly within the operational system.
- **Why it is attractive:** It reduces uncontrolled copies of personal data and makes information easier to manage.
- **Why rejected:** A blanket restriction could disrupt legitimate business activities, including marketing and reporting. A controlled export process with access restrictions, approved purposes and retention rules is more practical.

## Consequences

- **What this buys:** Better visibility and control over customer information, improved handling of deletion requests, reduced risk of unauthorised access and stronger evidence of the company's data protection practices.
- **What this costs:** Time to identify existing data locations, document procedures, assign responsibilities, review access permissions and monitor compliance. Staff will also need guidance on handling customer information and managing exported files. Legal or data protection expertise may be required.
- **What it costs the client if I am wrong:** If the controls are incomplete or poorly implemented, customer data may remain in untracked copies or be accessed without appropriate authorisation. Kloud Kart could face regulatory, financial and reputational consequences while still being unable to demonstrate effective data protection.
- **What would make me revisit this:** New regulatory requirements, expansion into additional countries, new systems that process personal data, repeated failures to fulfil deletion requests or evidence that the current controls are insufficient.

## What this survives

If Kloud Kart expands into Nigeria, the company can review and extend its governance procedures to address applicable data protection requirements in that market.

If the business increases its use of analytics and marketing data, the same governance principles will apply to new datasets and copies rather than allowing uncontrolled data collection and storage.

If the existing complaint reveals additional locations containing customer information, the data inventory and deletion procedures must be updated. The company should prioritise the complaint and meet its 90-day response deadline rather than wait for the wider warehouse project to be completed.
