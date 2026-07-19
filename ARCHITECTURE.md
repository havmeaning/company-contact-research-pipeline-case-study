# Conceptual Architecture

## Pipeline

```text
Input validation
  → Candidate discovery
  → Source classification
  → Company identity verification
  → Official-domain verification
  → Contact-page retrieval
  → Field extraction
  → Source binding
  → Contact validation
  → Confidence gate
  → Publication or unresolved status
  → Audit output
```

This is a conceptual description, not executable pseudocode. Implementation details are intentionally excluded.

## Evidence progression

The architecture distinguishes four claims that are easy to collapse accidentally:

1. **Evidence that a page mentions a company**  
   A name, address, registration reference, or descriptive text connects a page to the organization as a subject.

2. **Evidence that the page is operated by the company**  
   Domain, ownership, operator disclosures, and corroborating signals support that the organization controls the source.

3. **Evidence that a contact field belongs to that company**  
   The field is present in a context that attributes it to the intended organization, remains bound to that source, and is not owned by an intermediary.

4. **Evidence sufficient for publication**  
   Identity, operator/domain, source binding, field validation, and confidence requirements all meet the defined threshold.

A later claim cannot be assumed from an earlier one. Mention does not prove operation; operation does not automatically prove that every displayed value is a company contact; a plausible field is not necessarily publishable.

## Stage responsibilities

### Input validation

Validate record boundaries and header expectations before research begins. Reject or flag ambiguous input instead of silently shifting rows.

### Candidate discovery

Collect possible sources without treating search rank as proof. Discovery expands possibilities; it does not authorize publication.

### Source classification

Identify whether a candidate is an official site, directory, register, municipal page, social platform, PDF, portal, or unrelated source. The class determines what the source can legitimately prove.

### Company identity verification

Evaluate whether the candidate refers to the intended organization rather than a namesake or neighboring entity.

### Official-domain verification

Assess whether the organization operates the candidate domain or whether an intermediary controls it.

### Contact-page retrieval and field extraction

Retrieve relevant pages and form candidate fields while maintaining domain isolation. Extraction produces hypotheses, not final facts.

### Source binding

Retain the originating source and its verification context for each candidate field. Do not allow a value to inherit evidence from another domain.

### Contact validation

Evaluate plausibility, attribution, operator ownership, and consistency with the verified organization.

### Confidence gate

Translate evidence strength—not field count—into a publication decision. Missing required proof leads to unresolved.

### Publication and audit output

Publish only supported values. Record unresolved outcomes and the decision basis so review can distinguish missing evidence from processing failure.

## Why name and address matching were not enough

Third-party directories often reproduce correct organization names and addresses. That can establish that a page refers to the company, but not that the company operates the page. The same page may display a portal-owned telephone number, a relay email address, an advertising contact, or information belonging to another entity.

Name-and-address similarity is therefore an identity clue, not a contact-ownership proof. V2.1 requires separate operator/domain verification and field-level source binding before publication.

## Trust boundaries

- **Input boundary:** spreadsheet structure and record identity.
- **Search boundary:** unverified candidate discovery.
- **Domain boundary:** one candidate operator at a time.
- **Evidence boundary:** each field remains attached to its source.
- **Publication boundary:** only evidence-qualified claims leave the system.
- **Release boundary:** private evidence and public-safe documentation remain separate.

## Scope qualification

This architecture was validated as an intermediate release against a controlled, risk-based 30-company regression sample. It has not been demonstrated as production-ready or generalized to all approximately 499 records.
