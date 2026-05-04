---
system: oracle-rms
artifact_type: user_experience
status: example
confidence: medium
validated_by:
  - screen_capture
  - user_interviews
source_evidence:
  - ui_screenshots
  - workflow_diagrams
---

# User Experience Context — Oracle RMS

## Purpose
Map legacy UI/UX for merchandising and master data to inform user-centric rewrite design.

## Key User Workflows
- **Item Master Creation**: Multi-step form with validations; users report slow load times (evidence: interview notes).
- **Supplier Setup**: Complex contract UI; high error rates for cost entries (evidence: screen captures).
- **PO Dashboard**: Tabular view of pending orders; lacks mobile support.

## UX Pain Points
- **Usability**: Nested menus for item attributes; evidence shows user confusion in SME feedback.
- **Accessibility**: No screen reader support; potential ADA compliance gaps.
- **Performance**: UI freezes during large item loads.

## Target UX Recommendations
- Redesign to single-page apps with drag-and-drop for item hierarchies.
- Add responsive design and accessibility features.
- Confidence: Medium—based on screen evidence; validate with user testing.

## Open Questions
- Which workflows need mobile-first design? (Owner: UX SME)