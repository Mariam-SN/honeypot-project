# honeypot-project
Educational Kubernetes honeypot project – Phase 1 &amp; Phase 2

# Honeypot Project – Phase 1 & Phase 2

## Overview
This project implements a **deceptive honeypot environment** designed to observe attacker behavior
without exposing real production infrastructure.

The environment simulates a corporate setup using a believable external-facing web portal (DMZ),
planted configuration artifacts, and realistic internal trust relationships.

The primary goal is **behavioral analysis**, not exploitation training.

---

## Architecture Summary

**Phase 1 – DMZ Foothold**
- External corporate-style web portal
- No visible indicators of testing or labs
- Authentication-enabled entry point
- Internal configuration artifacts planted on the host
- Credentials and internal hostnames exposed intentionally

**Phase 2 – Internal HR Pivot (Planned)**
- Credential reuse and lateral movement
- HR service simulation
- Trust expansion analysis

---

## Phase 1 – What Was Implemented

- Customized web portal based on a Node.js application
- Frontend rebranding to remove training indicators
- Backend deception through:
  - `/etc/app/config.yaml`
  - Internal database credentials
  - LDAP references
  - Service user artifacts
- No direct Remote Code Execution (by design)

> Static assets are served without execution to enforce realistic attacker decision-making.

---

## Attacker Walkthrough (Phase 1)

1. Attacker discovers external HTTP service
2. Authenticates into a corporate-style portal
3. Enumerates application behavior
4. Discovers internal configuration artifacts
5. Identifies internal credentials and service accounts
6. Attempts lateral movement toward internal HR systems

Phase 1 ends when the attacker is **motivated to pivot**, not when exploitation occurs.

---

## Design Decisions

- **No direct RCE**:  
  The application stack correctly serves static assets without execution.
  This forces attackers toward credential abuse and pivoting, which is more realistic.

- **Deception over exploitation**:  
  The environment prioritizes believability and attacker psychology.

---

## Repository Structure

