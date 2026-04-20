# Project Roadmap

## Phase 1 — Submission Tracker (Current Focus)

**Goal:** Build a web application that submits documents to the VA Benefits Intake API and logs every submission with a permanent audit record.

**Components:**
- [ ] POST /uploads endpoint wrapper (generate upload slot)
- [ ] PUT document upload to S3 location
- [ ] PostgreSQL submissions table (guid, timestamp, document_name, status, file_path)
- [ ] React frontend — upload form + submission log table
- [ ] Save and display all historical submissions

**API Used:** VA Benefits Intake API v1
**Endpoint:** `https://sandbox-api.va.gov/services/vba_documents/v1/uploads`

---

## Phase 2 — Status Poller

**Goal:** Monitor submitted GUIDs and alert when the VA changes a document's status.

**Components:**
- [ ] GET /uploads/{guid} status check endpoint
- [ ] Scheduled polling job (cron)
- [ ] Status change detection and logging
- [ ] Email or webhook alert on status change

**API Used:** VA Benefits Intake API v1
**Endpoint:** `https://sandbox-api.va.gov/services/vba_documents/v1/uploads/{guid}`

---

## Phase 3 — Evidence Package Builder

**Goal:** Guide a veteran through building and submitting a complete evidence package.

**Components:**
- [ ] Multi-step claim narrative form
- [ ] Multi-document PDF bundler
- [ ] Submission preview before sending
- [ ] Full package submission via Intake API
- [ ] Submission confirmation and GUID storage

---

## Phase 4 — Public Conduct Registry

**Goal:** A structured, searchable public record of documented administrative conduct by VA employees and other public officials acting in their official capacity. Not a complaint board. Not a forum. A factual registry.

**What it records:**
- Name and title of the public official (public record — officials acting in official capacity have no privacy expectation regarding those actions)
- The VA office, department, or apparatus they operate within
- The specific federal regulation, law, or stated VA policy they were asked to follow
- The action they took instead
- The outcome for the veteran
- Supporting documentation (uploaded PDFs, correspondence, case numbers)

**What it does not do:**
- It does not editorialize
- It does not allow anonymous unsubstantiated claims
- It does not file complaints with agencies that will not act on them
- It does not ask permission from the institution it documents

**Why this matters:**
OIG complaints go nowhere. Whistleblower filings are absorbed by the same institutional body they name. The mechanism that is supposed to hold federal employees accountable reports to the same administrative structure those employees serve. Private citizens in 2026 have the infrastructure to create a public record that operates entirely outside that loop — one that is factual, sourced, and permanent.

A public official who closes a veteran's case under a term that does not exist in federal regulation has created a documented fact. This tool ensures that fact has a permanent home that is findable, citable, and beyond the reach of the institution that created it.

**Components:**
- [ ] Official registry database (name, title, office, action, regulation cited, outcome)
- [ ] Document upload and attachment per record
- [ ] Public search interface
- [ ] Record verification layer (no anonymous unsubstantiated entries)
- [ ] Export individual records as sourced PDF for legal use

---

## Future Considerations

- Integration with VA Claims Status API (currently internal-only — monitoring for public access)
- VSO dashboard for managing multiple veteran submissions
- Export audit log as PDF for legal proceedings
- Mobile-responsive interface
- Cross-agency expansion beyond VA — the same administrative conduct patterns exist across all federal and state agencies
