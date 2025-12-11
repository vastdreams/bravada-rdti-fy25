# PATH: Info_Files/README.md
# PURPOSE:
# - Receiving directory for raw information dumps and source files.
# - Staging area for incoming RDTI materials before organization.
#
# ROLE IN ARCHITECTURE:
# - Input layer: receives raw data before processing into structured folders.
#
# MAIN EXPORTS:
# - Raw source files
# - Previous filings
# - Quotech project details
#
# NON-RESPONSIBILITIES:
# - This is NOT the final location for documents
# - Documents should be moved to appropriate folders after processing
#
# NOTES FOR FUTURE AI:
# - Process files from here and move to appropriate structured folders
# - For Excel files, read entire file in code
# - Maintain original files until confirmed organized

---

# Info_Files - Raw Data Staging Area

This directory is for incoming raw data dumps before organization into the proper structure.

## Expected Contents

Based on the information provided, this folder will receive:

### RDTI Information
- [ ] Previous RDTI filings
- [ ] RDTI guidelines and requirements
- [ ] ATO correspondence

### Quotech Project Details
- [ ] Technical specifications
- [ ] Development documentation
- [ ] Project history

### Financial Data
- [ ] Excel files with detailed workings
- [ ] XERO exports
- [ ] Cost breakdowns

## Processing Instructions

1. **For Excel Files**: Read entire file in code to extract all data
2. **For PDFs**: Extract key information and organize
3. **For Images**: Process and document relevant information
4. **Move processed files** to appropriate directories:
   - Technical docs → `02-evidence/technical/`
   - Financial records → `02-evidence/financial/`
   - Timesheets → `02-evidence/time-records/`
   - Agreements → `04-supporting-materials/contracts/`
   - Previous filings → `06-archive/`

## Files Awaiting Upload

| File Type | Description | Target Location | Status |
|-----------|-------------|-----------------|--------|
| RDTI Info | Previous filings | `06-archive/` | Pending |
| Quotech Details | Project documentation | `01-project-documentation/` | Pending |
| Excel Files | Financial workings | `02-evidence/financial/` | Pending |

---

## Notes

- Keep originals here until confirmed organized
- Document any processing done on files
- Flag any unclear or incomplete data
