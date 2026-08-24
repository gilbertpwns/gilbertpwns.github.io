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

* **Traditional Networking** encourages snowflakes because:
    + Imperative CLI Configuration
        - Engineers configure devices step-by-step:
    
```
conf t
vlan 10
name SALES
interface Gi0/1
switchport access vlan 10
```

* each device evolves based on:
    + who configured it
    + when
    + what ticket
    + what emergency fix
* there is no global system enforcing consistency
* **human drift**
    + over time:
        - temporary changes become permanent
        - emergency fixes are never reverted
        - interface descriptions differ
        - routing metrics vary
        - VLAN naming conventions change
    + small inconsistencies accumulate
    + this is called **configuration entropy**
    + entropy always increases without a controlling system
* **no source of truth**
    + in snowflake networks:
        - the device IS the source of truth
        - there is no canonical model of intended state
        - you cannot regenerate the device from a data model
    + from IaC perspective, that is the **core violation**

## Why Snowflakes are Dangerous

* **non-deterministic behavior**
    + two "identical" branch routers behave differently
    + why?
        - slight ACL difference
        - hidden route-map
        - extra static routes
        - different timers
    + there is no deterministic model
* **no reproducibility**:
    + if a router dies, you cannot:
        - regenerate it from data
        - guarantee identical state
        - validate consistency automatically
    + you must manually reconstruct
    + that is **not** IaC
* **no convergence model**
    + in **IaC** systems:
        - you define desired states
        - systems converge toward it
    + in **snowflake** networks:
        - there is no convergence loop
        - there is only ad-hoc changes

## Snowflake vs IaC Devices

| Snowflake | IaC Device|
|:-:|:-:|
| Config built manually | Config is rendered from data model|
| Device is truth | Git is truth |
| Changes undocumented | Changes version-controlled |
| Drift invisible | Drift detectable |
| Recovery manual | Recovery automated |
| Unique per device | Pattern-based |

## The Core Technical Issue: Lack of State Control

* snowflake networks lack:
    + state modeling
    + state comparison logic
    + reconciliation loops
* they are **procedural systems**, not **declarative systems**


---
