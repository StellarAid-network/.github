# Security Policy

## Reporting a vulnerability

**Never open a public issue for a vulnerability.**

Report security issues privately using either of these channels:

- Email **security@stellaraid.example**
- Use GitHub's **private vulnerability reporting** on the affected repository
  (Security -> Report a vulnerability)

Include as much of the following as you can:

- A description of the issue and its impact
- Reproduction steps or a proof of concept
- Affected repository, versions, and network (testnet/mainnet)
- Any suggested fix or mitigation

## Our commitment

- We aim to **acknowledge reports within 72 hours**.
- We will keep you informed as we investigate and work on a fix.
- We will credit reporters who wish to be acknowledged once a fix is released.

## Scope

The following are in scope: the Soroban contracts, the TypeScript SDK, the API and
indexer, and the web application.

Please do not:

- Access, modify, or exfiltrate other users' data
- Perform denial-of-service or resource-exhaustion attacks
- Test against mainnet with real funds

## Handling

- Contracts will be **independently audited before any mainnet deployment**. Audit
  reports are published in the `contracts` repository under `audits/`.
- A bug bounty program will launch alongside mainnet.
- Once a fix is ready, we will coordinate disclosure with the reporter.
