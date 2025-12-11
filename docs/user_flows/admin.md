# User Flow: Admin / Director

> **Persona**: Admin / Director / Owner  
> **Primary Modules**: Onboarding, Users, Settings, BI

---

## Role Summary

System configuration, user management, business oversight.

| Responsibility | Module |
|----------------|--------|
| Initial setup | Onboarding |
| User management | Users |
| System config | Settings |
| Business overview | BI & Reporting |

---

## Onboarding Flow

```
1. Sign Up → Company Profile → Connect OneDrive → Choose Folder Template
2. → Customize Categories → Create Users → Connect Email (optional)
3. → Create First Job → Ready
```

### Onboarding Steps

| Step | Action |
|------|--------|
| Company Profile | Name, ABN, Logo, Timezone |
| OneDrive | OAuth connection |
| Folder Template | Waterproofing, Steel, General |
| Cost Categories | Customize if needed |
| Users | Invite team with roles |
| Email | Optional Outlook connection |

---

## User Management

### Roles

| Role | Access |
|------|--------|
| Admin | Full access, manage users, settings |
| PM | Jobs, variations, day sheets, reports |
| Estimator | Quotes, variations |
| Supervisor | Day sheets, timesheets, QA |
| Accounts | Invoicing, billing, suppliers |
| Viewer | Read-only |

### Actions

```
Add User → Enter Email, Name → Assign Role → Send Invite
```

---

## Business Dashboard

### Key Metrics

| Metric | Purpose |
|--------|---------|
| Active Jobs | Current workload |
| Total Revenue | Business health |
| Gross Margin | Profitability |
| Quote Pipeline | Future work |
| Cash Position | Liquidity |

### Drill-Down

```
Dashboard → Click Metric → Detailed Report → Filter/Export
```

---

## Settings Configuration

| Setting | Options |
|---------|---------|
| Folder Template | Add/remove/rename folders |
| Cost Categories | Add/remove/rename |
| Labour Rates | Default hourly rates |
| GST | Rate (10% default) |
| Invoice Numbering | Prefix, sequence |
| Quote Numbering | Prefix, sequence |

---

## Success Metrics

| Metric | Target |
|--------|--------|
| Onboarding time | < 10 minutes |
| User adoption | > 80% DAU |
| System uptime | 99.9% |

---

## Key Decisions

| Decision | Considerations |
|----------|----------------|
| Folder template | Match existing structure |
| User roles | Start minimal, expand |
| Email connection | Depends on email culture |
| Cost categories | Match accounting |
