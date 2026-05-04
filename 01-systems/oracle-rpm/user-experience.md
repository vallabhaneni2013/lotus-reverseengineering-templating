---
system: oracle-rpm
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

# User Experience Context — Oracle RPM

## Purpose
Map legacy UI/UX for pricing and promotions to inform user-centric rewrite design.

## Key User Workflows
- **Price Event Creation**: Multi-step form with validations; users report slow load times (evidence: interview notes).
- **Promotion Setup**: Complex overlap rules UI; high error rates for precedence (evidence: screen captures).
- **Approval Dashboard**: Tabular view of pending prices; lacks mobile support.

## UX Pain Points
- **Usability**: Nested menus for zone pricing; evidence shows user confusion in SME feedback.
- **Accessibility**: No screen reader support; potential ADA compliance gaps.
- **Performance**: UI freezes during large promotion loads.

## Target UX Recommendations
- Redesign to single-page apps with drag-and-drop for promotions.
- Add responsive design and accessibility features.
- Confidence: Medium—based on screen evidence; validate with user testing.

## Open Questions
- Which workflows need mobile-first design? (Owner: UX SME)