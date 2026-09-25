# trooth-eval-harnesses

Five checklists a company works through against its own systems, in YAML.

Trooth operates the Trooth Network: one public, signed, machine-readable record per company, carrying its identity, products and demos, commercial terms, domain and marketing links, people, documents, security and privacy posture, AI practices, procurement terms and relationships. It is Trooth's only product and it is free.

**Trooth witnesses and dates facts. It does not score, rate, rank or certify anyone.**

## Who runs these, and who does not

You do. A harness is a list of questions about your own organization and your own AI systems, and answering them means going and looking. You keep the answers, and you publish the ones you want a buyer to be able to read.

Trooth does not run them for you, does not receive the answers, and does not grade the output. Nothing in this repository sends anything anywhere: there is no code in it. The `trooth` command-line reader does two things (`trooth check <domain>` reads a published record, and `trooth lint` reads what your own infrastructure declares, locally), and neither command takes a framework or reads a harness.

Working through a harness is also not compliance with the framework it is drawn from. Whether an organization meets NIST CSF 2.0, the NIST AI RMF, the EU AI Act, the GDPR or the CCPA is settled, where it can be settled at all, by an assessor or by the relevant regulator (the two NIST frameworks are voluntary, and NIST does not certify conformance to either). A YAML file cannot settle it, and neither can Trooth.

## What is in this repository

Eight files: five checklists, an Apache 2.0 `LICENSE`, a `.github/CODEOWNERS`, and this README. No runner, no parser, no JSON Schema for the format, no continuous integration.

| Framework | File | Categories | Items |
|---|---|---|---|
| NIST Cybersecurity Framework 2.0 | [`harnesses/nist-csf-2.0/checklist.yaml`](harnesses/nist-csf-2.0/checklist.yaml) | 6 | 23 |
| NIST AI Risk Management Framework 1.0 | [`harnesses/nist-ai-rmf-1.0/checklist.yaml`](harnesses/nist-ai-rmf-1.0/checklist.yaml) | 5 | 26 |
| EU AI Act, Regulation (EU) 2024/1689 | [`harnesses/eu-ai-act/checklist.yaml`](harnesses/eu-ai-act/checklist.yaml) | 6 | 28 |
| GDPR, Regulation (EU) 2016/679 | [`harnesses/gdpr/checklist.yaml`](harnesses/gdpr/checklist.yaml) | 7 | 25 |
| CCPA as amended by the CPRA, Cal. Civ. Code 1798.100 et seq. | [`harnesses/ccpa/checklist.yaml`](harnesses/ccpa/checklist.yaml) | 6 | 20 |

122 items across 30 categories. Each file carries `reviewed: 2026-06-08`, which is the date the file gives for its last reading against the source text. That field is the honest measure of how current a file is; read it before you rely on one.

The categories follow the source document rather than a house structure. `nist-csf-2.0` is the six CSF functions, `GV` through `RC`. `nist-ai-rmf-1.0` is Govern, Map, Measure, Manage plus a fifth category for the Generative AI Profile, NIST AI 600-1. `eu-ai-act` runs scope and definitions, prohibited practices, high-risk systems, Article 50 transparency, general-purpose AI models, and post-market monitoring and serious-incident reporting. `gdpr` runs the Article 5 principles, legal bases, special categories, data-subject rights, accountability, security and breach notification, and international transfers. `ccpa` runs applicability, notice at collection, consumer rights, service providers and contractors, reasonable security, and governance.

## The file format

One YAML document per framework. A `framework` block, then `categories`, each with `items`.

```yaml
framework:
  id: nist-csf-2.0
  name: NIST Cybersecurity Framework
  version: "2.0"
  published: 2024-02-26
  source: https://www.nist.gov/cyberframework
  reviewed: 2026-06-08
  notes: |
    Free text saying what the framework is and what this file covers.

categories:
  - id: GV
    name: Govern
    description: Establish, communicate, and monitor the cybersecurity risk-management strategy.
    items:
      - id: GV.OC-01
        title: Organizational mission is understood and informs cybersecurity risk management
        evidence_type: documentation
        how_to_demonstrate: A current Information Security Policy that references the company's mission and risk appetite.
```

Every item in all five files carries exactly those four keys, and no others: `id`, `title`, `evidence_type`, `how_to_demonstrate`. There is no per-item `description` and no per-item `references` array. The only link in a file is the one `source` URL in the `framework` block, so you take an item back to the source text yourself. In `nist-csf-2.0` the item `id` is the CSF's own subcategory identifier. In the other four files it is this repository's own label, so what you look up is the article, section or function named in the item or in its category.

`evidence_type` takes one of three values, and the split across the 122 items is 70 `documentation`, 31 `technical`, 21 `process`. It says what kind of thing would answer the item (a written document, a system setting or a check you can run, or a repeatable practice), so you know whether the item belongs to whoever owns policy, whoever owns the systems, or whoever owns the process.

`how_to_demonstrate` is a short statement, usually one sentence, naming the artifact that would answer the item. It is the most useful field in the file and the most opinionated: it is one way of answering, not the only one.

Every `framework` block carries `id`, `name`, `version`, `source`, `reviewed` and `notes`. Four of the five also carry `published`; `ccpa`, `eu-ai-act` and `gdpr` carry `effective`, and `ccpa` adds `cpra_effective`.

## Using one

Walk a file top to bottom. For each item, find the artifact `how_to_demonstrate` describes, or write down that you do not have it. What you do not have is your backlog. What you do have is what you can hand an assessor, or link from your Trooth record, instead of rebuilding it under time pressure.

The files are plain YAML with stable identifiers, so an item can be tracked in whatever you already use. Nothing here depends on a Trooth account or a Trooth tool.

## What these files deliberately are not

They are summaries. Each one covers the obligations most often asked about in a vendor review, not every obligation in the source. Four of the five say as much in their own `notes` field; the CCPA file's `notes` describes the statute's applicability thresholds and says nothing about its own coverage. An item that is missing here is not an item that does not apply to you.

They also carry no result. There is no field for a verdict, a severity, a weight or a figure, and none is computed anywhere. Counting answered items into a number would turn a reading into a rating, and Trooth does not publish a rating about any company.

## Contributing

Useful pull requests: refreshing an item against a newer revision of a source and moving the `reviewed` date with it, correcting a citation, clarifying a `how_to_demonstrate` that names the wrong artifact, or adding a framework as a new directory under `harnesses/` in the same shape. Open an issue before adding a framework, so the coverage question is argued about before the YAML is written. Contributions are licensed under Apache 2.0.

`.github/CODEOWNERS` in this repository assigns review to `@troothllc/maintainers`, a team that does not exist yet, so it currently assigns pull requests to nobody. That is named here rather than left for a contributor to discover when their pull request sits unreviewed.

## Security

Report a vulnerability through the [Vulnerability Disclosure Policy](https://trooth.co/security/vulnerability-disclosure-policy).

## Links

- The Network: [trooth.co/network](https://trooth.co/network)
- Publish your own record, free: [trooth.co/get-started](https://trooth.co/get-started)
- How witnessing works, and what Trooth does not read: [trooth.co/methodology](https://trooth.co/methodology)
- Developers: [trooth.co/developers](https://trooth.co/developers)
- Contact: [trooth.co/contact](https://trooth.co/contact)

## License

Apache License 2.0. See [LICENSE](LICENSE). You may use these files in commercial or non-commercial work under the terms of that license, which include keeping a copy of it with any copy of the files you redistribute.

Trooth signs what it witnessed. It never signs on a company's behalf.
