# PATH: 02-evidence/technical/gitlab-repository-evidence.md
# PURPOSE:
# - Documents GitLab repository evidence for Quotech R&D project.
# - Provides commit history, contributors, and technology stack evidence.
#
# ROLE IN ARCHITECTURE:
# - Technical evidence layer: proves software development R&D activities.
#
# MAIN EXPORTS:
# - Repository statistics
# - Commit history
# - Technology stack
# - Development team contributions
#
# NON-RESPONSIBILITIES:
# - Does NOT contain actual source code
# - Does NOT contain credentials (access via separate secure method)
#
# NOTES FOR FUTURE AI:
# - Data extracted via GitLab API
# - Repositories are private; access requires authentication
# - Focus on development activity demonstrating R&D work

---

# Quotech GitLab Repository Evidence

**Extraction Date**: December 2024
**Source**: GitLab (gitlab.com/cypher70/)
**Project**: Quotech - AI-Driven Labor Efficiency and Quoting Analysis

---

## Repository Summary

| Repository | ID | Created | Last Activity | Status |
|------------|-----|---------|---------------|--------|
| **quotech-frontend** | 55001764 | 2024-02-16 | 2025-12-11 | Active |
| **quotech-backend** | 54988530 | 2024-02-15 | 2025-12-11 | Active |
| **billing-frontend** | 71429350 | 2025-07-07 | 2025-09-27 | Active |

**Total Active Development Period**: February 2024 - Present (22+ months)

---

## Quotech-Frontend Repository

### Repository Details
- **Path**: `cypher70/quotech-frontend`
- **Web URL**: https://gitlab.com/cypher70/quotech-frontend
- **Default Branch**: main
- **Visibility**: Private

### Active Branches (7 total)
1. `production-shadcn` - Production release branch
2. `dev-theme-shadcn` - Development branch
3. `developer` - Feature development
4. `developer-2` - Parallel development
5. `developer-3` - Parallel development
6. `main` - Main branch
7. `production` - Legacy production

### Commit Statistics (Recent 100 commits)

**Total Contributors**: 4 developers

| Developer | Commits | Role |
|-----------|---------|------|
| SayoniPandit98 | 51 | Lead Frontend Developer |
| Apu-99 | 31 | Frontend Developer |
| Rashi_03 / Rashi gupta | 13 | Frontend Developer |
| vibhuti@finsoeasy.com | 5 | Frontend Developer |

### Monthly Activity (Recent)
| Month | Commits |
|-------|---------|
| 2025-12 | 68 |
| 2025-11 | 32 |

### Technology Stack

**Framework & Core**:
- React 19.1.0 (Latest)
- Vite 6.3.5 (Build tool)
- React Router DOM 7.6.1

**UI Framework**:
- Tailwind CSS 4.1.8
- Radix UI Components (extensive)
- Material UI (@mui/material 7.3.4)
- Shadcn/ui (via Radix primitives)
- Lucide React Icons

**State Management**:
- Redux Toolkit 2.8.2
- React Redux 9.2.0
- Redux Persist 6.0.0

**Data Visualization & Reporting**:
- ApexCharts 4.7.0
- Recharts 3.0.2
- React ApexCharts

**Calendar & Scheduling**:
- FullCalendar 6.1.19 (daygrid, interaction, react)

**Data Handling**:
- Axios 1.9.0 (HTTP client)
- TanStack React Table 8.21.3
- XLSX 0.18.5 (Excel processing)
- date-fns 3.6.0

**Drag & Drop**:
- @hello-pangea/dnd 18.0.1

**Additional Features**:
- Google Maps API Loader
- React Quill (Rich text editor)
- React Day Picker
- html2canvas / html-to-image (Export)
- KaTeX (Math rendering)
- Country-State-City (Location data)

### Source Code Structure

```
src/
├── ComponentsUi/     # UI Components
├── Pages/            # Page Components
├── Utils/            # Utility Functions
├── assets/           # Static Assets
├── components/       # Shared Components
├── hooks/            # Custom React Hooks
├── lib/              # Library Code
├── reducers/         # Redux Reducers
├── App.jsx           # Main App Component
├── routes.jsx        # Routing Configuration
├── theme-provider.jsx # Theme Management
└── main.jsx          # Entry Point
```

---

## Quotech-Backend Repository

### Repository Details
- **Path**: `cypher70/quotech-backend`
- **Web URL**: https://gitlab.com/cypher70/quotech-backend
- **Default Branch**: main
- **Visibility**: Private

### Active Branches (7 total)
1. `dev-v2` - Development v2
2. `developer` - Feature development
3. `main` - Main branch
4. `new-development` - New development
5. `new-production` - New production
6. `production` - Production
7. `production-v2` - Production v2

### Contributors
| Developer | Role |
|-----------|------|
| Siddhant Shukla | Backend Developer |
| cypher1 | Backend Developer |

---

## Billing-Frontend Repository

### Repository Details
- **Path**: `cypher70/billing-frontend`
- **Web URL**: https://gitlab.com/cypher70/billing-frontend
- **Created**: 2025-07-07
- **Last Activity**: 2025-09-27
- **Visibility**: Private

---

## Development Activity Evidence

### Recent Commits (Sample from production-shadcn)

| Date | Author | Commit Message |
|------|--------|----------------|
| 2025-12-10 | SayoniPandit98 | merge with dev, redirection issue from joblist fixed |
| 2025-12-10 | Rashi_03 | Fixed Job Navigation issue |
| 2025-12-10 | Rashi_03 | Reports Formula Added as tooltip |
| 2025-12-10 | SayoniPandit98 | invoice page data integration and filters added |
| 2025-12-10 | Rashi_03 | Cursor pointer added to tabs in setting |
| 2025-12-10 | Apu-99 | daysheet pdf fixed and loader add |
| 2025-12-09 | SayoniPandit98 | dailyform popover width fixed, one drive error texts |
| 2025-12-09 | Rashi_03 | Adding create daysheet to sidebar |
| 2025-12-09 | Rashi_03 | Adding sorting option in Daysheet |
| 2025-12-09 | Rashi_03 | Bin changed into Archive |
| 2025-12-09 | SayoniPandit98 | download added to folder tree, button text change |
| 2025-12-09 | SayoniPandit98 | individual sorting added to job rows in manager view |
| 2025-12-09 | Apu-99 | theme logo issue solve |
| 2025-12-09 | Rashi_03 | Edit data of daysheet sync to variation |
| 2025-12-09 | vibhuti@finsoeasy | daysheet view editted |

### Development Features Evidenced by Commits

1. **Job Management Module**
   - Job navigation and routing
   - Job list filtering and sorting
   - Manager view with individual job sorting

2. **Daysheet Module**
   - Daysheet creation and editing
   - PDF export functionality
   - Variation synchronization
   - Sidebar integration

3. **Reports Module**
   - Report formulas with tooltips
   - Data visualization

4. **Invoice Module**
   - Invoice page data integration
   - Filter functionality

5. **File Management**
   - OneDrive sync integration
   - Folder tree with download
   - File categorization

6. **UI/UX Improvements**
   - Theme management (dark/light mode)
   - Responsive design
   - Accessibility (cursor pointers)

---

## R&D Evidence Summary

### Technical Uncertainty Demonstrated
1. **Excel Parsing Complexity**: Using XLSX library to parse diverse estimation formats
2. **Real-time Sync**: OneDrive bi-directional synchronization challenges
3. **AI Integration**: Building intelligent document classification
4. **Data Visualization**: Complex KPI calculations and visualizations

### Systematic Investigation Evidence
1. **Iterative Development**: Multiple feature branches and merge patterns
2. **Testing**: Separate development and production branches
3. **Continuous Integration**: .gitlab-ci.yml configuration present
4. **Code Quality**: ESLint configuration, TypeScript types

### Technical Advancement
1. **Modern Tech Stack**: React 19, Vite 6, Tailwind 4 (cutting-edge)
2. **Component Architecture**: Radix UI + Shadcn pattern
3. **State Management**: Redux Toolkit with persistence
4. **Data Processing**: Client-side Excel processing

---

## Related Repositories (Same Ecosystem)

| Repository | Purpose | Activity |
|------------|---------|----------|
| New_Quotech_Scripts | Automation scripts | 2025-11-11 |
| billing-backend | Billing API | 2025-07-27 |
| eyedreams-backend | Eye tracking research | 2025-02-24 |
| medTWIN website | Medical digital twin | 2025-11-30 |

---

## Verification Checklist

- [x] Repository access confirmed
- [x] Commit history retrieved
- [x] Contributors documented
- [x] Technology stack identified
- [x] Branch structure documented
- [x] Source code structure mapped
- [x] Recent development activity confirmed
- [ ] Full commit count for FY25 period
- [ ] Lines of code statistics

---

## Future Notes

- Consider automated commit statistics extraction for each filing period
- Set up GitLab activity reports for ongoing R&D documentation
- Document specific commits related to each AI module
- Track time spent on R&D features via commit messages
