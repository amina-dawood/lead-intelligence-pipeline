# Design Decisions

**Why email as the unique identifier, not name.**
Two different customers can share a name. Using email to search before 
writing to Airtable prevents records from being incorrectly merged or 
duplicated.

**Why a human approval step before contacting a customer.**
An AI classifier can be wrong, and an autonomous send is hard to undo once 
a customer has received it. Routing every outbound message through a 
manager approval keeps a human accountable for anything customer-facing, 
while still letting AI handle the repetitive classification and drafting.

**Why compare snapshots instead of overwriting company data every run.**
Re-scraping a company site on every lead would otherwise create a new or 
updated record every single time, even when nothing changed. Comparing 
against the last snapshot keeps the CRM meaningful instead of noisy.

**Why a Wait node instead of an immediate follow-up.**
Contacting a lead the instant they're classified can feel aggressive. A 
short scheduled delay mirrors how a real sales process paces outreach.