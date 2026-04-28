# Arabella Inc. — Active Directory Migration Lab

## Streamlining Oerational Eficiency at Arabella Inc.

Arabella Inc. is a Small to Medium Enterprise (SME) in the microfinance sector that built its operations on 
legacy systems, something that worked well enough at the start but has become increasingly difficult to defend
as AI-driven efficiency and evolving cybersecurity threats continue to raise the stakes for businesses that haven't
modernized their foundations. 
I was brought in to lay the groundwork for Arabella's infrastructure shift. The first step was moving their day-to-day 
operations from an unmonitored, decentralized workgroup environment to a centralized domain management system — giving 
the organization a single point of authority over user access, security policy, and operational visibility. 
I designed and executed a full Active Directory Domain Services migration, the kind that happens in real companies when 
they outgrow their initial setup and need proper IT infrastructure underneath them to operate securely and at scale. 
Arabella had 28 employees across 5 departments with no centralized control over who had access to what. That changes here. 
Everything in this repository is documented the way I would document it on the job, with a plan before the work, evidence 
during the work, and a report after the work.

---

## The Problem

Arabella Inc. was operating with the following issues before the migration:
- Every workstation managed its own local user accounts independently
- No centralized visibility into who had access to what
- No way to enforce password policies or security standards across machines
- File sharing relied on local credentials with no access control structure
- No audit trail for account changes or access events
- High risk of unauthorized access due to inconsistent local admin practices

---

## What I Built

- Set up a Windows Server 2025 domain controller — ARABELLA-DC01
- Created and configured the arabellainc.local domain from scratch
- Migrated two Windows 10 workstations from workgroup (Arabella-WG) to a domain
- Rebuilt the entire user account structure under Active Directory
- Created department-based Organizational Units and Security Groups
- Enforced Principle of Least Privilege across all department file shares
- Verified zero data loss using SHA256 cryptographic hashing before and after migration

---

## Environment

| Component | Details |
|---|---|
| Hypervisor | VirtualBox |
| Domain Controller | Windows Server 2025 Datacenter Evaluation — ARABELLA-DC01 |
| Workstations | Windows 10 — ARABELLA-PC001, ARABELLA-PC002 |
| Domain | arabellainc.local |
| Network | NAT Network — 10.0.2.0/24 |
| DC IP | 10.0.2.15 |
| PC001 IP | 10.0.2.16 |
| PC002 IP | 10.0.2.17 |
---

## Department Structure and Access Control

Each department has its own Active Directory Security Group. Users can 
only access their own department folder, a way of enforcing Principle 
of Least Privilege (PoLP)

| Department | AD Security Group | Assigned User |
|---|---|---|
| Credit | GRP_Credit | walma |
| IT | GRP_IT | nolwen |
| Customer Relations | GRP_CustomerRelations | mawish |
| Finance and Procurement | GRP_FinanceProcurement | Tmash |
| Sales and Marketing | GRP_SalesMarketing | jmikel |

---

## Data Integrity Verification

Before the migration I generated SHA256 checksums for every file in the Arabella Data 2026 folder. After the migration completed 
I generated the same checksums again and compared them using PowerShell.

The result:
100% DATA INTEGRITY CONFIRMED! — All hashes match.
Every file. Every folder. Every department. Zero discrepancies. The data that existed before the migration is identical 
to the data that exists after it post-migration, cryptographically proven.
