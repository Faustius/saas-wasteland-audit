🧟‍♂️ The SaaS Wasteland Audit (aka: The Zombie Subscription Hunt)
"30% of SaaS spend in the average SMB is wasted on unused licenses."

📖 Overview
The SaaS Wasteland Audit is an open-source framework designed to help System Administrators, CFOs, and Business Owners identify, isolate, and terminate "Zombie" software subscriptions.

At Monadic, L.L.C., we believe in the "Linux Philosophy" of business: Clarity over Complexity. We are releasing our internal audit protocols to the public to help businesses stop the slow bleed of recurring revenue.

🎯 The Problem
Modern businesses suffer from SaaS Sprawl:

Zombie Accounts: Paying for licenses for employees who were offboarded months ago.

Shadow IT: Software purchased on company cards without IT oversight.

Redundancy Loops: Paying for two tools that do the same thing (e.g., Zoom + Microsoft Teams).

🛠 Usage
You can fork this repository to customize the audit for your own organization, or simply use the provided checklists below.

Phase 1: The Credit Card Sweep (SQL / CSV Export)
Goal: Identify unauthorized recurring charges.

Run a query on your expense management system (QuickBooks, Xero, Expensify) filtering for:

Vendor Category = Software / Web Services

Amount < $100 (These fly under the radar)

Frequency = Monthly

The "Usual Suspects" Grep List:

[ ] Dropbox / Box / iCloud (Storage Redundancy)

[ ] Adobe Creative Cloud (Check: Does this user actually open Photoshop?)

[ ] Zoom / Webex (Check: Do they have a corporate license elsewhere?)

[ ] Squarespace / Wix / GoDaddy (Check: Are these domains active?)

Phase 2: The Offboarding Gap
Goal: Reclaim licenses from terminated users.

The Protocol: When a user (User_X) leaves the organization:

Disable Email: (Standard procedure).

Revoke License: (The missed step).

Microsoft 365: Remove E3/Business Premium License immediately. Convert mailbox to "Shared Mailbox" (Free Tier).

Salesforce/CRM: Deactivate user to free up the "Seat."

Adobe: Reassign the license to the replacement hire or cancel.

Phase 3: The Redundancy Check (Logic Gate)
Goal: Elimination of duplicate feature sets.

Apply the following logic to your stack:

Code snippet
graph TD
    A[Do you pay for Microsoft 365?] -->|Yes| B(You have Teams)
    B --> C{Do you pay for Zoom?}
    C -->|Yes| D[❌ REDUNDANCY DETECTED]
    C -->|No| E[✅ Optimized]

    A -->|Yes| F(You have OneDrive 1TB)
    F --> G{Do you pay for Dropbox?}
    G -->|Yes| H[❌ REDUNDANCY DETECTED]
    G -->|No| I[✅ Optimized]
📂 Repository Contents
audit-checklist.md - The printable Markdown checklist for manual audits.

offboarding-protocol.json - A sample JSON structure for automating user offboarding via API.

LICENSE - MIT License (Free to use, modify, and distribute).

🤝 Contributing
This is a living document. If you find new "Zombie" patterns or have scripts to automate license checking (PowerShell, Python), please submit a Pull Request.

🔗 About Monadic
We are a Strategic IT Partner based in Louisiana, focusing on Systems Engineering and Resilience.

Web: www.monadic-llc.com

Blog: The Holographic Business
