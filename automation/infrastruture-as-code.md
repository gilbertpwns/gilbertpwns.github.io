# Infrastructure as Code (IaC)

## Why Traditional Networking Breaks at Scale

* Snowflake Device Problem
* Configuration Entropy
* Scaling Beyond 100 Devices
* Change Window Fear
* Audit & Compliance Limitations

## Systems Thinking for Infrastructure

* Deterministic vs Non-deterministic Systems
* Imperative vs Declarative
* Desired State vs Current State
* State Comparison Logic
* Convergence Theory and Fixed-point
* Reconciliation Loops & Idempotency as Convergence Guarantee

## Infrastructure Automation Principles

* Source of Truth & Version Control
* State Awareness & Drift Management
* State Engines & Reconciliation
* Control Plane Interaction Models
* Event-Driven Automation
* Automation Risk Management
* Ownership & Domain Boundaries

## Snowflake Device Problem

A snowflake device is a network device whose configuration:

* is manually built
* has documented changes
* is slightly different from every other similar device
* cannot be reproduced deterministically
* exists as a unique, fragile artifact

Like a snowflake: 

* it looks normal
* it works
* but no two are identical
* and if it breaks, you can't recreate it easily

The most important difference and perspectice:

A snowflake device is infrastructure whose state is not derived from a single authoritative source of truth and cannot be deterministically reconstructed.

### Key Phrases:

* not declaratively defined
* not version controlled
* not reproducible
* not convergent

## Why Snowflakes Exist in Networking

* **Traditional Networking** encourages snowflakes because :




---
