# 50 Days of Azure - Day 12: Implementing Cloud Governance with Tags

## Task Overview
To improve resource organization and cost tracking within the expanding Nautilus infrastructure, I implemented metadata tagging on a critical Linux Virtual Machine instance.

## Objective
Apply the tag `Environment=dev` to the virtual machine named `nautilus-vm` to systematically categorize it under development workloads.

## Technical Details
* **Target Resource:** `nautilus-vm`
* **Tag Key:** `Environment`
* **Tag Value:** `dev`
* **Purpose:** Environment Classification & Governance

## Real-World Scenario
Imagine walking into a massive storage warehouse where thousands of identical cardboard boxes are stacked. If none of them have labels, finding the specific parts for a "development project" vs a "production launch" would take hours. Cloud tagging is exactly like slapping a color-coded label on those boxes. It allows the financial team to see exactly how much money the development environment is costing compared to production.

## Lessons Learned
1. **Metadata-Driven Management:** Tags do not alter the performance or state of a resource, but they are crucial for filtering and automation scripts.
2. **Cost Allocation:** Learned that tags allow enterprises to generate granular billing reports, splitting costs by department (`Dept=Finance`), owner (`Owner=Vihanga`), or environment.
3. **Enforcing Policies:** Moving forward, organizations can use Azure Policy to block engineers from creating *any* resource unless they include required tags like `Environment`.

---
*Created as part of the 50 Days of Azure Challenge.*
