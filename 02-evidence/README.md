# PATH: 02-evidence/README.md
# PURPOSE:
# - Central repository for all evidence supporting the RDTI claim.
# - Organized by evidence type for easy retrieval and filing preparation.

# ROLE IN ARCHITECTURE:
# - Evidence layer: provides proof and documentation of R&D activities and costs.

# MAIN EXPORTS:
# - Technical evidence
# - Financial evidence
# - Time records
# - Meeting notes

# NON-RESPONSIBILITIES:
# - Does NOT contain project descriptions (see 01-project-documentation/)
# - Does NOT contain completed filing forms (see 03-filing-documents/)

# NOTES FOR FUTURE AI:
# - All evidence should be linked back to specific projects in 01-project-documentation/
# - Maintain chronological organization (use date prefixes)
# - Ensure evidence clearly demonstrates R&D activities and associated costs
# - Never commit sensitive financial data or proprietary information to version control

---

# Evidence Collection

This directory contains all evidence supporting the RDTI claim, organized by type.

## Directory Structure

### `technical/`
Technical documentation proving R&D activities:
- Code repositories and commits
- Design documents and architecture diagrams
- Test results and experimental data
- Technical reports and analysis
- Prototypes and proof-of-concepts

### `financial/`
Financial records documenting R&D costs:
- Invoices for R&D-related expenses
- Equipment purchase receipts
- Software licenses for R&D tools
- Third-party contractor invoices
- Material and supply costs

### `time-records/`
Time tracking showing R&D labor costs:
- Timesheets for R&D activities
- Project time tracking reports
- Labor cost allocations
- Employee time logs

### `meetings-notes/`
Meeting documentation showing R&D planning and progress:
- Project planning meetings
- Technical review meetings
- Problem-solving sessions
- Progress updates

## Evidence Requirements

### Technical Evidence Should Show:
- Systematic investigation and experimentation
- Iterative development and testing
- Technical challenges and solutions
- Knowledge advancement

### Financial Evidence Should Show:
- Direct R&D costs (labor, materials, equipment)
- Indirect R&D costs (overhead allocation)
- Third-party R&D expenses
- Time period alignment with project dates

### Time Records Should Show:
- Hours spent on R&D activities
- Employee roles and qualifications
- Project allocation breakdown
- Date ranges matching project timelines

## Document Naming Convention

Use format: `YYYY-MM-DD_[evidence-type]_[project-name]_[description].ext`

Examples:
- `2024-01-20_code-commit_digital-twin_initial-prototype.md`
- `2024-02-15_invoice_ai-routing_cloud-services.pdf`
- `2024-03-01_timesheet_digital-twin_john-smith.xlsx`

## Evidence Linking

Each evidence file should reference:
- Related project in `01-project-documentation/`
- Associated costs (if financial evidence)
- Time period covered
- Relevant team members

## Checklist

- [ ] Technical evidence collected for all R&D projects
- [ ] Financial records organized and categorized
- [ ] Time records complete and accurate
- [ ] Meeting notes document R&D planning and progress
- [ ] All evidence dated and properly named
- [ ] Evidence linked to specific projects

---

## Future Notes

- Consider automated evidence collection from development tools
- Set up regular evidence review cycles
- Create evidence completeness dashboard
- Establish clear criteria for what qualifies as R&D evidence
