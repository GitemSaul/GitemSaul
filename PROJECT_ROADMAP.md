# Troubleshooting Toolkit - Project Roadmap

## Project Overview
**Goal:** Build a production-ready SQL forensics toolkit demonstrating technical support engineering skills
**Timeline:** 4-6 weeks @ 3-4 hours/day
**Tech Stack:** ASP.NET Core Web API + React + SQL Server + Docker
**Primary Focus:** SQL Forensics Module (Duplicates, Orphans, Stored Procedures)

---

## Quick Reference

| Phase | Duration | Daily Hours | Focus |
|-------|----------|-------------|-------|
| Phase 0: Foundation | 3 days | 3-4 hrs | Repo setup, architecture, dependencies |
| Phase 1: Backend Core | 7-10 days | 3-4 hrs | API, services, database connectivity |
| Phase 2: Frontend | 5-7 days | 3-4 hrs | React UI, API integration |
| Phase 3: Integration | 3-5 days | 3-4 hrs | End-to-end testing, refinement |
| Phase 4: Polish & Deploy | 4-6 days | 3-4 hrs | Documentation, Docker, deployment |

**Total: 22-31 days (4-6 weeks)**

---

## Phase 0: Foundation & Setup
**Duration:** 3 days (9-12 hours total)
**Goal:** Repository structure, development environment, core architecture decisions

### Day 1 - Repository & Project Structure (3-4 hours)

#### TODO List:
- [x] Create GitHub repository: `troubleshooting-toolkit`
- [x] Initialize with README.md
- [x] Create comprehensive .gitignore for .NET and React
- [x] Set up repository structure
- [x] Create development branch: `git checkout -b develop`
- [ ] Create initial commit and push

#### Repository Structure:
```
troubleshooting-toolkit/
├── .gitignore
├── README.md
├── PROJECT_ROADMAP.md
├── backend/
│   ├── Toolkit.Api/
│   │   ├── Controllers/
│   │   ├── Services/
│   │   ├── Models/
│   │   │   ├── Requests/
│   │   │   ├── Responses/
│   │   │   └── Schema/
│   │   └── Configuration/
│   ├── tests/
│   │   └── Toolkit.Tests/
│   └── schema_exports/
├── frontend/
│   └── src/
│       ├── components/
│       ├── pages/
│       ├── services/
│       └── utils/
├── docs/
├── learning/
└── .github/
    └── workflows/
```

---

### Day 2 - Backend Project Setup (3-4 hours)

#### TODO List:
- [ ] Install .NET 8 SDK (if not already installed)
- [ ] Create ASP.NET Core Web API project
- [ ] Add required NuGet packages
- [ ] Configure CORS for frontend communication
- [ ] Set up logging with Serilog
- [ ] Create appsettings.TEMPLATE.json
- [ ] Test that API runs successfully
- [ ] Commit: "Backend API project setup with dependencies"

#### Commands to Run:
```powershell
cd backend

# Create Web API project
dotnet new webapi -n Toolkit.Api --framework net8.0

cd Toolkit.Api

# Add required packages
dotnet add package Dapper
dotnet add package Microsoft.Data.SqlClient
dotnet add package Serilog.AspNetCore
dotnet add package Serilog.Sinks.Console
dotnet add package Serilog.Sinks.File

# Test run
dotnet run
```

---

### Day 3 - Frontend Setup (3-4 hours)

#### TODO List:
- [ ] Install Node.js (if not already installed)
- [ ] Create React application
- [ ] Install frontend dependencies
- [ ] Configure environment variables
- [ ] Test frontend runs successfully
- [ ] Commit: "Frontend setup complete"

#### Commands to Run:
```powershell
cd frontend

# Create React app
npx create-react-app . --template typescript

# Install dependencies
npm install axios
npm install @mui/material @emotion/react @emotion/styled
npm install react-router-dom

# Test run
npm start
```

---

## Phase 1: Backend Core Development
**Duration:** 7-10 days (21-40 hours total)
**Goal:** Complete backend API with all SQL forensics features

### Day 4 - Database Connection Infrastructure (3-4 hours)

#### TODO List:
- [ ] Create DatabaseProfile model
- [ ] Create DatabaseConnectionService
- [ ] Create DatabaseController
- [ ] Register services in Program.cs
- [ ] Create appsettings.Development.json (DO NOT COMMIT - it's in .gitignore)
- [ ] Test profile retrieval via Swagger
- [ ] Commit: "Database connection service with profile support"

---

### Day 5 - Schema Configuration System (3-4 hours)

#### TODO List:
- [ ] Create schema models (Table, Column, ForeignKey)
- [ ] Create SchemaService to load and validate schema
- [ ] Create schema.json configuration file
- [ ] Add validation for table/column names (SQL injection prevention)
- [ ] Test schema loading on startup
- [ ] Commit: "Schema configuration and validation system"

---

### Day 6 - Duplicate Detection Service (3-4 hours)

#### TODO List:
- [ ] Create DuplicateCheckRequest/Response models
- [ ] Create SqlForensicsService with DetectDuplicates method
- [ ] Create SqlController with duplicate detection endpoint
- [ ] Add input validation using SchemaService
- [ ] Test with Swagger
- [ ] Commit: "Duplicate detection feature complete"

---

### Day 7 - Orphaned Records Detection (3-4 hours)

#### TODO List:
- [ ] Create OrphanCheckRequest/Response models
- [ ] Add DetectOrphansAsync method to SqlForensicsService
- [ ] Add orphan detection endpoint to SqlController
- [ ] **IMPORTANT:** Validate ReferencedTable against schema (security fix)
- [ ] Test with tables that have foreign keys
- [ ] Commit: "Orphaned records detection feature"

#### Security Note - Orphan Detection Validation:
The OrphanCheckRequest must validate BOTH the child table AND the referenced (parent) table:

```csharp
// In SqlForensicsService.DetectOrphansAsync():
// Validate BOTH tables to prevent SQL injection
if (!_schemaService.ValidateTable(request.SchemaName, request.TableName))
{
    return new OrphanCheckResponse
    {
        Success = false,
        Message = $"Invalid child table: {request.SchemaName}.{request.TableName}"
    };
}

// CRITICAL: Also validate the referenced table!
if (!_schemaService.ValidateTable(request.ReferencedSchema ?? "dbo", request.ReferencedTable))
{
    return new OrphanCheckResponse
    {
        Success = false,
        Message = $"Invalid referenced table: {request.ReferencedTable}"
    };
}
```

---

### Day 8 - Stored Procedures Check (3-4 hours)

#### TODO List:
- [ ] Create StoredProcedureCheckRequest/Response models
- [ ] Add DetectMissingStoredProceduresAsync method
- [ ] Add endpoint to SqlController
- [ ] Test with your database
- [ ] Commit: "Stored procedure validation feature"

---

### Days 9-10 - Testing & Refinement (6-8 hours)

#### TODO List:
- [ ] Create unit tests for all services
- [ ] Test all endpoints with invalid inputs
- [ ] Test error scenarios
- [ ] Add pagination support to API endpoints (performance optimization)
- [ ] Update Swagger documentation
- [ ] Commit: "Unit tests and documentation complete"

#### Pagination Support (Add to responses):
```csharp
public class PaginatedResponse<T>
{
    public List<T> Items { get; set; }
    public int TotalCount { get; set; }
    public int Page { get; set; }
    public int PageSize { get; set; }
    public int TotalPages => (int)Math.Ceiling(TotalCount / (double)PageSize);
}
```

---

## Phase 2: Frontend Development
**Duration:** 5-7 days (15-28 hours total)
**Goal:** Complete React frontend with all features

### Day 11 - Base Components & API Service (3-4 hours)

#### TODO List:
- [ ] Create API service wrapper with axios
- [ ] Create DatabaseSelector component
- [ ] Create LoadingSpinner component
- [ ] Create ErrorAlert component
- [ ] Set up React Router
- [ ] Create basic Dashboard page
- [ ] Test API connectivity
- [ ] Commit: "Frontend base components and API integration"

---

### Day 12 - Duplicate Check Component (3-4 hours)

#### TODO List:
- [ ] Create DuplicateCheckForm component
- [ ] Create DuplicateResultsTable component
- [ ] Integrate with Dashboard
- [ ] Test duplicate detection end-to-end
- [ ] Commit: "Duplicate check UI complete"

---

### Days 13-14 - Remaining Check Components (6-8 hours)

#### TODO List:
- [ ] Create OrphanCheckForm component
- [ ] Create OrphanResultsTable component
- [ ] Create StoredProcedureCheckForm component
- [ ] Create StoredProcedureResults component
- [ ] Integrate all into Dashboard with tabs
- [ ] Commit: "All check components complete"

---

### Day 15 - UI Polish & Export Features (3-4 hours)

#### TODO List:
- [ ] Add export to CSV button for results
- [ ] Add pagination to results tables
- [ ] Improve styling and layout
- [ ] Add help text/tooltips
- [ ] Commit: "UI polish and export features"

---

## Phase 3: Integration & Testing
**Duration:** 3-5 days (9-20 hours total)

### Days 16-17 - End-to-End Testing (6-8 hours)

#### TODO List:
- [ ] Create test scenarios document
- [ ] Test all features with real data
- [ ] Test edge cases
- [ ] Performance testing
- [ ] Create test report
- [ ] Fix all critical bugs
- [ ] Commit: "Integration testing complete"

---

### Day 18 - Bug Fixes & Optimization (3-4 hours)

#### TODO List:
- [ ] Fix all bugs from testing
- [ ] Optimize slow queries
- [ ] Improve error messages
- [ ] Commit: "Bug fixes and optimizations"

---

## Phase 4: Documentation & Deployment
**Duration:** 4-6 days (12-24 hours total)

### Day 19 - Comprehensive README (3-4 hours)

#### TODO List:
- [ ] Write comprehensive README.md
- [ ] Add screenshots
- [ ] Create quick start guide
- [ ] Document all features
- [ ] Commit: "Complete documentation"

---

### Day 20 - Docker Configuration (3-4 hours)

#### TODO List:
- [ ] Create Dockerfile for backend
- [ ] Create Dockerfile for frontend
- [ ] Create docker-compose.yml
- [ ] Test Docker build
- [ ] Commit: "Docker configuration complete"

---

### Day 21 - Case Studies & Examples (3-4 hours)

#### TODO List:
- [ ] Create 3 case study documents
- [ ] Add sample datasets
- [ ] Document lessons learned
- [ ] Commit: "Case studies and examples"

---

### Day 22 - Final Polish & Deployment (3-4 hours)

#### TODO List:
- [ ] Code cleanup
- [ ] Final testing
- [ ] Create GitHub release
- [ ] Optional: Deploy to cloud
- [ ] Commit: "Final release v1.0"

---

## Security Checklist

- [x] Sensitive files in .gitignore (appsettings.Development.json, appsettings.Production.json)
- [ ] Schema validation for ALL user-provided table/column names
- [ ] Schema validation for referenced tables in orphan detection
- [ ] No connection strings in source control
- [ ] Read-only database profiles where appropriate
- [ ] Input validation on all API endpoints
- [ ] CORS configured correctly

---

## Progress Tracking

### Week 1
- [x] Day 1: Repository setup
- [ ] Day 2: Backend setup
- [ ] Day 3: Frontend setup
- [ ] Day 4: Database connection service
- [ ] Day 5: Schema configuration
- [ ] Day 6: Duplicate detection
- [ ] Day 7: Orphan detection

### Week 2
- [ ] Day 8: Stored procedures check
- [ ] Days 9-10: Testing & refinement
- [ ] Day 11: Base frontend components
- [ ] Day 12: Duplicate UI
- [ ] Days 13-14: Remaining UIs

### Week 3
- [ ] Day 15: UI polish
- [ ] Days 16-17: Integration testing
- [ ] Day 18: Bug fixes
- [ ] Day 19: Documentation
- [ ] Day 20: Docker
- [ ] Day 21: Case studies

### Week 4
- [ ] Day 22: Final polish & deploy

---

**Last Updated:** December 2024
**Status:** Day 1 in progress
