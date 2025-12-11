# PATH: 03-filing-documents/README.md
# PURPOSE:
# - Contains completed RDTI filing forms, submissions, and correspondence with tax authorities.
# - Final documents ready for submission or already submitted.

# ROLE IN ARCHITECTURE:
# - Submission layer: completed filing materials ready for or submitted to tax authorities.

# MAIN EXPORTS:
# - Completed RDTI forms
# - Submission packages
# - Correspondence records

# NON-RESPONSIBILITIES:
# - Does NOT contain templates (see 05-templates/)
# - Does NOT contain draft documents (use version control or archive)

# NOTES FOR FUTURE AI:
# - Maintain clear version control for filing documents
# - Keep copies of all submissions and correspondence
# - Never commit sensitive tax information to public repositories
# - Archive completed filings to 06-archive/ after processing

---

# Filing Documents

This directory contains completed RDTI filing forms, submissions, and correspondence.

## Required Documents

### RDTI Forms
- **RDTI Claim Form**: Main filing form with project details and costs
- **Project Descriptions**: Detailed descriptions for each R&D project
- **Cost Schedules**: Breakdown of all R&D costs being claimed
- **Supporting Schedules**: Additional required documentation

### Submission Package
- **Cover Letter**: Introduction and summary of filing
- **Document Index**: List of all submitted documents
- **Evidence Package**: Organized evidence supporting the claim

### Correspondence
- **Submission Receipts**: Confirmation of filing submission
- **Authority Correspondence**: Questions, responses, and clarifications
- **Assessment Notices**: Tax authority decisions and assessments

## Document Naming Convention

Use format: `YYYY-MM-DD_[document-type]_[version].ext`

Examples:
- `2024-04-01_rdti-claim-form_v1.0.pdf`
- `2024-04-01_submission-package_v1.0.zip`
- `2024-05-15_authority-correspondence_question-1.pdf`

## Filing Process

1. **Preparation**: Use templates from `05-templates/` to prepare documents
2. **Review**: Ensure all required information is complete
3. **Finalization**: Create final versions in this directory
4. **Submission**: Submit to tax authority
5. **Archive**: Move completed filings to `06-archive/` after processing

## Version Control

- Use version numbers (v1.0, v1.1, etc.) for iterations
- Keep all versions until filing is finalized
- Archive superseded versions to `06-archive/`

## Checklist

- [ ] All required forms completed
- [ ] Project descriptions accurate and complete
- [ ] Cost schedules match financial evidence
- [ ] Evidence properly referenced and organized
- [ ] Submission package complete
- [ ] Copies of all submissions retained
- [ ] Correspondence logged and filed

---

## Future Notes

- Consider creating automated checks for form completeness
- Set up reminders for filing deadlines
- Create templates for common correspondence
- Establish clear process for handling authority questions
