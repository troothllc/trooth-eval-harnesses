# trooth-eval-harnesses

[![License: Apache 2.0](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![Frameworks](https://img.shields.io/badge/frameworks-5-D97706)](#)

Open evaluation harnesses for software and AI companies. Five structured checklists, one per framework, that you can use to self-evaluate against the controls before a formal audit. Free under Apache 2.0.

## Why these exist

Every company we have worked with hits the same wall: the framework documents are dense, run hundreds of pages each, and do not tell you what evidence you need to collect. These harnesses translate each framework into a structured checklist that gives you the control or article reference, a plain-English description of what the framework expects, the type of evidence you need (technical, documentation, or process), how to demonstrate it, and links back to the source text.

You read the harness, you self-evaluate, you collect evidence. When the formal auditor shows up, you hand them a folder instead of starting from scratch.

## What's included

| Framework | File | Source | Status |
|---|---|---|---|
| NIST Cybersecurity Framework 2.0 | [`harnesses/nist-csf-2.0/checklist.yaml`](harnesses/nist-csf-2.0/checklist.yaml) | [NIST](https://www.nist.gov/cyberframework) | Stable |
| NIST AI Risk Management Framework 1.0 | [`harnesses/nist-ai-rmf-1.0/checklist.yaml`](harnesses/nist-ai-rmf-1.0/checklist.yaml) | [NIST](https://www.nist.gov/itl/ai-risk-management-framework) | Stable |
| EU AI Act (Regulation 2024/1689) | [`harnesses/eu-ai-act/checklist.yaml`](harnesses/eu-ai-act/checklist.yaml) | [EUR-Lex](https://eur-lex.europa.eu/eli/reg/2024/1689/oj) | Stable |
| GDPR (Regulation 2016/679) | [`harnesses/gdpr/checklist.yaml`](harnesses/gdpr/checklist.yaml) | [EUR-Lex](https://eur-lex.europa.eu/eli/reg/2016/679/oj) | Stable |
| CCPA / CPRA (California Civil Code 1798.100) | [`harnesses/ccpa/checklist.yaml`](harnesses/ccpa/checklist.yaml) | [oag.ca.gov](https://oag.ca.gov/privacy/ccpa) | Stable |

## File format

Each checklist is a YAML file with this shape:

```yaml
framework:
  id: nist-csf-2.0
  name: NIST Cybersecurity Framework
  version: "2.0"
  source: https://www.nist.gov/cyberframework
  reviewed: 2026-06-08

categories:
  - id: GV
    name: Govern
    items:
      - id: GV.OC-01
        title: Organizational mission is understood and informs cybersecurity risk management
        description: ...
        evidence_type: documentation
        how_to_demonstrate: ...
        references:
          - https://...
```

This format is human-readable, machine-parseable, and easy to extend. Tools, including the Trooth CLI, can consume these files directly to drive automated evaluation.

## How to use

### As a checklist

1. Open the YAML file for your framework
2. 2. Walk each item top to bottom
   3. 3. For each, mark internally whether you have the evidence on hand
      4. 4. The gaps are your remediation backlog
        
         5. ### As input to automated tooling
        
         6. The checklists are machine-parseable YAML. Automated evaluators, including the [Trooth CLI](https://github.com/troothllc/trooth-cli) (`npm i -g trooth`), can consume them to drive coverage checks.
        
         7. ### As a starting point for your own framework
        
         8. Fork this repo. Add a new YAML under `harnesses/your-framework/`. The format is intentionally simple, so you can use it for internal frameworks, customer-specific contracts, or sector regulations such as HIPAA, PCI DSS, and SOX.
        
         9. ## Important caveats
        
         10. **These harnesses are reference implementations, not legal opinions.** Compliance with a framework is determined by an accredited auditor or the relevant regulator, not by a YAML file.
        
         11. **The frameworks change.** We refresh these harnesses on the cadence in the `reviewed:` field of each YAML. If you find that an item is out of date with the source text, open an issue or a pull request.
        
         12. **Coverage of each framework is summarized, not exhaustive.** We include the items most commonly asked about in vendor reviews. Some frameworks, especially the EU AI Act, have hundreds of micro-obligations that we do not enumerate individually.
        
         13. ## Contributing
        
         14. We welcome pull requests that refresh items to match newer revisions of a framework, add references to authoritative guidance, improve plain-English descriptions of complex items, or add new framework harnesses such as HIPAA, PCI DSS, SOX, ISO 27001, and ISO 42001. See `CONTRIBUTING.md`.
        
         15. ## License
        
         16. Apache License 2.0. You can use these harnesses in commercial or non-commercial products without attribution.
        
         17. ## About Trooth
        
         18. Trooth is the witnessed trust network for software and AI companies. A company gets witnessed once, across identity, security, privacy, and AI practices, each with a source and a date, and buyers and their AI agents read a current, signed record with no login. Get witnessed at [trooth.co/signup](https://trooth.co/signup).
        
         19. [trooth.co](https://trooth.co) · [Security](https://trooth.co/security)
         20. 
