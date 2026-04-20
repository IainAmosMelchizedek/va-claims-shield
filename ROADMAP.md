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

## Future Considerations

- Integration with VA Claims Status API (currently internal-only — monitoring for public access)
- VSO dashboard for managing multiple veteran submissions
- Export audit log as PDF for legal proceedings
- Mobile-responsive interface
