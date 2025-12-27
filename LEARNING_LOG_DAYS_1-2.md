# Learning Log: Days 1-2
## SQL Forensics Toolkit Project

**Date:** December 27, 2024
**Environment:** Windows 11, PowerShell, VS Code, .NET 10, Git

---

## Table of Contents
1. [Day 1: Repository & Project Structure](#day-1-repository--project-structure)
2. [Day 2: Backend API Setup](#day-2-backend-api-setup)
3. [Key Learnings](#key-learnings)
4. [Improvement Opportunities](#improvement-opportunities)
5. [Command Reference](#command-reference)

---

## Day 1: Repository & Project Structure

### Overview
Set up the GitHub repository, created the folder structure, configured Git, and made the first commit.

---

### Task 1.1: Creating a GitHub Repository

**What We Did:**
Created a new public repository on GitHub with README, .gitignore, and MIT license.

**How-To:**
1. Go to [github.com](https://github.com) and sign in
2. Click the `+` icon (top-right) → "New repository"
3. Configure:
   - **Repository name:** `troubleshooting-toolkit`
   - **Description:** Brief project summary
   - **Visibility:** Public
   - **Initialize with README:** ✓ Check
   - **Add .gitignore:** Select `VisualStudio`
   - **License:** MIT
4. Click "Create repository"

**Result:** Repository available at `https://github.com/YOUR_USERNAME/troubleshooting-toolkit`

---

### Task 1.2: Cloning the Repository Locally

**What We Did:**
Downloaded the repository to our local machine.

**Commands:**
```powershell
# Navigate to your projects folder
cd C:\Code

# Clone the repository
git clone https://github.com/GitemSaul/troubleshooting-toolkit.git

# Enter the project folder
cd troubleshooting-toolkit
```

**Key Concepts:**
- `git clone` creates a local copy of a remote repository
- The `.git` folder (hidden) contains all version control information

---

### Task 1.3: Creating a Development Branch

**What We Did:**
Created a `develop` branch to keep `main` stable.

**Commands:**
```powershell
# Create and switch to develop branch
git checkout -b develop

# Verify current branch (asterisk shows active branch)
git branch
```

**Output:**
```
  main
* develop
```

**Key Concepts:**
- `main` branch = stable, production-ready code
- `develop` branch = active development
- `-b` flag creates a new branch and switches to it simultaneously
- Never commit directly to `main` without review

**💡 Improvement Opportunity:**
Consider setting up branch protection rules on GitHub to prevent accidental pushes to `main`:
1. Go to Repository → Settings → Branches
2. Add rule for `main`
3. Require pull request reviews before merging

---

### Task 1.4: Creating the Folder Structure

**What We Did:**
Created all project folders for backend, frontend, docs, etc.

**Commands (PowerShell):**
```powershell
# Backend folders
New-Item -ItemType Directory -Force -Path "backend/Toolkit.Api/Controllers"
New-Item -ItemType Directory -Force -Path "backend/Toolkit.Api/Services"
New-Item -ItemType Directory -Force -Path "backend/Toolkit.Api/Models/Requests"
New-Item -ItemType Directory -Force -Path "backend/Toolkit.Api/Models/Responses"
New-Item -ItemType Directory -Force -Path "backend/Toolkit.Api/Models/Schema"
New-Item -ItemType Directory -Force -Path "backend/Toolkit.Api/Configuration"
New-Item -ItemType Directory -Force -Path "backend/tests/Toolkit.Tests"
New-Item -ItemType Directory -Force -Path "backend/schema_exports"

# Frontend folders
New-Item -ItemType Directory -Force -Path "frontend/src/components/common"
New-Item -ItemType Directory -Force -Path "frontend/src/components/database"
New-Item -ItemType Directory -Force -Path "frontend/src/components/checks"
New-Item -ItemType Directory -Force -Path "frontend/src/pages"
New-Item -ItemType Directory -Force -Path "frontend/src/services"
New-Item -ItemType Directory -Force -Path "frontend/src/utils"
New-Item -ItemType Directory -Force -Path "frontend/public"

# Documentation and other folders
New-Item -ItemType Directory -Force -Path "docs"
New-Item -ItemType Directory -Force -Path "learning"
New-Item -ItemType Directory -Force -Path ".github/workflows"
```

**Key Concepts:**
- `New-Item -ItemType Directory` = PowerShell's way to create folders
- `-Force` = creates parent directories if they don't exist (like `mkdir -p` in Unix)
- Git doesn't track empty folders

**💡 Improvement Opportunity:**
Create a PowerShell script (`setup-folders.ps1`) to automate this:
```powershell
# setup-folders.ps1
$folders = @(
    "backend/Toolkit.Api/Controllers",
    "backend/Toolkit.Api/Services",
    # ... etc
)
foreach ($folder in $folders) {
    New-Item -ItemType Directory -Force -Path $folder
}
```

---

### Task 1.5: Creating .gitkeep Files

**What We Did:**
Added placeholder files so Git tracks empty directories.

**Commands:**
```powershell
New-Item -ItemType File -Force -Path "backend/schema_exports/.gitkeep"
New-Item -ItemType File -Force -Path "backend/tests/Toolkit.Tests/.gitkeep"
New-Item -ItemType File -Force -Path "docs/.gitkeep"
New-Item -ItemType File -Force -Path "learning/.gitkeep"
New-Item -ItemType File -Force -Path ".github/workflows/.gitkeep"
```

**Key Concepts:**
- `.gitkeep` is a convention (not a Git feature) to track empty directories
- The file can be named anything, but `.gitkeep` is widely recognized
- Once real files are added, `.gitkeep` can be removed

---

### Task 1.6: Configuring .gitignore

**What We Did:**
Updated `.gitignore` to exclude sensitive files and build artifacts.

**Critical Entries Added:**
```gitignore
# SENSITIVE FILES - NEVER COMMIT
appsettings.Development.json
appsettings.Production.json
appsettings.Local.json
**/secrets.*
**/credentials.*

# Build outputs
[Bb]in/
[Oo]bj/
node_modules/

# IDE files
.vs/
.idea/
```

**Key Concepts:**
- `.gitignore` tells Git which files to never track
- Patterns with `**/` match in any subdirectory
- `[Bb]in/` matches both `bin/` and `Bin/` (case-insensitive)
- Add sensitive files BEFORE creating them to prevent accidental commits

**💡 Improvement Opportunity:**
Use `git status` frequently to verify ignored files aren't being tracked. If you accidentally committed a sensitive file:
```powershell
# Remove from Git but keep local file
git rm --cached appsettings.Development.json
git commit -m "Remove sensitive file from tracking"
```

---

### Task 1.7: First Commit and Push

**What We Did:**
Staged all changes, created a commit, and pushed to GitHub.

**Commands:**
```powershell
# Stage all changes
git add .

# Check what will be committed
git status

# Create commit with descriptive message
git commit -m "Initial project structure with folders and roadmap"

# Push to GitHub (first time with -u to set upstream)
git push -u origin develop
```

**Key Concepts:**
- `git add .` stages all changes in current directory and subdirectories
- `git status` shows staged, unstaged, and untracked files
- `git commit -m "message"` creates a snapshot with a description
- `git push -u origin develop` pushes and sets up tracking for future pushes

**Common Warning:**
```
warning: LF will be replaced by CRLF
```
This is normal on Windows. Git is normalizing line endings.

**💡 Improvement Opportunity:**
Write more descriptive commit messages:
```powershell
# Instead of:
git commit -m "Initial project structure"

# Consider:
git commit -m "Set up project structure for SQL Forensics Toolkit

- Created backend folder structure (Controllers, Services, Models)
- Created frontend folder structure (components, pages, services)
- Added .gitignore for .NET and React
- Added PROJECT_ROADMAP.md with development plan"
```

---

## Day 2: Backend API Setup

### Overview
Created the ASP.NET Core Web API project, added dependencies, configured logging and CORS, and tested the API.

---

### Task 2.1: Verifying Prerequisites

**What We Did:**
Confirmed .NET SDK and Git were installed and we were in the correct directory.

**Commands:**
```powershell
# Check .NET version
dotnet --version
# Output: 10.0.101

# Check current directory
pwd
# Output: C:\code\troubleshooting-toolkit

# Check current branch
git branch
# Output: * develop
```

**Key Concepts:**
- Always verify your environment before starting work
- `pwd` = "print working directory"
- The `*` in `git branch` output indicates the active branch

---

### Task 2.2: Creating the ASP.NET Core Web API Project

**What We Did:**
Used the .NET CLI to scaffold a new Web API project.

**Commands:**
```powershell
# Navigate to backend folder
cd backend

# Create the Web API project
dotnet new webapi -n Toolkit.Api

# Navigate into the project
cd Toolkit.Api
```

**What Was Created:**
```
Toolkit.Api/
├── Controllers/          # (empty - we'll add these)
├── Properties/
│   └── launchSettings.json
├── appsettings.json
├── appsettings.Development.json
├── Program.cs
└── Toolkit.Api.csproj
```

**Key Concepts:**
- `dotnet new webapi` = creates a Web API template
- `-n Toolkit.Api` = names the project
- `.csproj` = project file containing dependencies and settings
- `launchSettings.json` = development server configuration (ports, etc.)

**💡 Improvement Opportunity:**
Specify the framework version explicitly for consistency:
```powershell
dotnet new webapi -n Toolkit.Api --framework net8.0
```
This ensures the same version regardless of what SDK is installed.

---

### Task 2.3: Adding NuGet Packages

**What We Did:**
Added required libraries for database access, logging, and API documentation.

**Commands:**
```powershell
# Database ORM (lightweight, fast SQL queries)
dotnet add package Dapper

# SQL Server connectivity
dotnet add package Microsoft.Data.SqlClient

# Structured logging
dotnet add package Serilog.AspNetCore
dotnet add package Serilog.Sinks.Console
dotnet add package Serilog.Sinks.File

# API documentation (required in .NET 9+)
dotnet add package Swashbuckle.AspNetCore
```

**Verify Installation:**
```powershell
# Restore all packages
dotnet restore

# View installed packages
dotnet list package
```

**Key Concepts:**
- NuGet = .NET's package manager (like npm for Node.js)
- `dotnet add package` downloads and adds reference to `.csproj`
- Packages are stored in a global cache, not in your project folder
- `dotnet restore` ensures all packages are downloaded

**💡 Improvement Opportunity:**
Pin package versions for reproducibility:
```powershell
dotnet add package Dapper --version 2.1.28
```
Or maintain a `Directory.Packages.props` file for centralized version management.

---

### Task 2.4: Configuring Program.cs

**What We Did:**
Replaced the default minimal API setup with controller-based configuration including Serilog and CORS.

**Complete Program.cs:**
```csharp
using Serilog;

var builder = WebApplication.CreateBuilder(args);

// Configure Serilog
Log.Logger = new LoggerConfiguration()
    .ReadFrom.Configuration(builder.Configuration)
    .Enrich.FromLogContext()
    .WriteTo.Console()
    .WriteTo.File("logs/toolkit-.log", rollingInterval: RollingInterval.Day)
    .CreateLogger();

builder.Host.UseSerilog();

// Add services to the container
builder.Services.AddControllers();
builder.Services.AddEndpointsApiExplorer();
builder.Services.AddSwaggerGen();

// Configure CORS
var allowedOrigins = builder.Configuration.GetSection("Cors:AllowedOrigins").Get<string[]>()
    ?? new[] { "http://localhost:3000" };

builder.Services.AddCors(options =>
{
    options.AddPolicy("AllowFrontend", policy =>
    {
        policy.WithOrigins(allowedOrigins)
              .AllowAnyMethod()
              .AllowAnyHeader();
    });
});

var app = builder.Build();

// Configure the HTTP request pipeline
if (app.Environment.IsDevelopment())
{
    app.UseSwagger();
    app.UseSwaggerUI();
}

app.UseCors("AllowFrontend");
app.UseAuthorization();
app.MapControllers();

Log.Information("Toolkit API starting...");
app.Run();
```

**Key Concepts:**
- **Serilog:** Structured logging framework (better than default logging)
- **CORS:** Cross-Origin Resource Sharing (allows frontend on port 3000 to call backend on port 5135)
- **Swagger:** Auto-generates API documentation and testing UI
- **AddControllers():** Enables attribute-based routing with `[ApiController]`
- **MapControllers():** Registers controller routes

**Why "No operations defined in spec!"?**
We haven't created any controllers yet. Swagger shows what's available - currently nothing. Controllers come on Day 4.

**💡 Improvement Opportunity:**
Add global exception handling:
```csharp
app.UseExceptionHandler("/error");

// Add this endpoint
app.Map("/error", (HttpContext context) =>
{
    var exception = context.Features.Get<IExceptionHandlerFeature>()?.Error;
    Log.Error(exception, "Unhandled exception");
    return Results.Problem("An error occurred");
});
```

---

### Task 2.5: Configuring appsettings.json

**What We Did:**
Set up base configuration for logging, CORS, and schema path.

**appsettings.json:**
```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft.AspNetCore": "Warning"
    }
  },
  "AllowedHosts": "*",
  "Cors": {
    "AllowedOrigins": ["http://localhost:3000"]
  },
  "Serilog": {
    "MinimumLevel": {
      "Default": "Information",
      "Override": {
        "Microsoft": "Warning",
        "System": "Warning"
      }
    }
  },
  "SchemaConfiguration": {
    "FilePath": "Configuration/schema.json"
  }
}
```

**Key Concepts:**
- `appsettings.json` = default configuration (committed to Git)
- `appsettings.Development.json` = development overrides (NOT committed)
- Configuration is hierarchical and can be overridden by environment

---

### Task 2.6: Creating appsettings.TEMPLATE.json

**What We Did:**
Created a template showing required settings without real values.

**appsettings.TEMPLATE.json:**
```json
{
  "ConnectionStrings": {
    "DefaultConnection": "Server=YOUR_SERVER;Database=YOUR_DATABASE;User Id=YOUR_USER;Password=YOUR_PASSWORD;TrustServerCertificate=True;"
  },
  "DatabaseProfiles": {
    "Production": {
      "Name": "Your Database Name",
      "ConnectionStringKey": "DefaultConnection",
      "Description": "Main production database",
      "ReadOnly": true
    }
  },
  "Cors": {
    "AllowedOrigins": ["http://localhost:3000"]
  }
}
```

**Key Concepts:**
- Template files show required structure without sensitive data
- Team members copy template to `appsettings.Development.json` and fill in real values
- The actual settings file is in `.gitignore`

**💡 Improvement Opportunity:**
Add instructions as comments (JSON5 or separate README):
```
Instructions:
1. Copy this file to appsettings.Development.json
2. Replace YOUR_SERVER with your SQL Server instance
3. Replace YOUR_DATABASE with target database name
4. Never commit appsettings.Development.json!
```

---

### Task 2.7: Testing the API

**What We Did:**
Ran the application and verified Swagger UI loaded.

**Commands:**
```powershell
# Start the application
dotnet run
```

**Finding the Port:**
```powershell
# Check launchSettings.json for URL
Get-Content Properties/launchSettings.json
```

**Result:**
- API running at: `http://localhost:5135`
- Swagger UI at: `http://localhost:5135/swagger`
- Message "No operations defined in spec!" = expected (no controllers yet)

**Stopping the Server:**
- Press `Ctrl+C` in the terminal

**💡 Improvement Opportunity:**
Configure a consistent port in `launchSettings.json`:
```json
"applicationUrl": "http://localhost:5000"
```
This makes URLs predictable across development environments.

---

### Task 2.8: Committing Day 2 Changes

**What We Did:**
Committed and pushed all backend setup changes.

**Commands:**
```powershell
# Return to project root
cd C:\code\troubleshooting-toolkit

# Stage changes
git add .

# Commit
git commit -m "Add ASP.NET Core Web API with Serilog and Swagger"

# Push
git push origin develop
```

**Alternative: VS Code Source Control UI**
1. Click Source Control icon (left sidebar)
2. Review changes
3. Enter commit message
4. Click ✓ to commit
5. Click ... → Push

**💡 Improvement Opportunity:**
Use conventional commit messages for better history:
```
feat: add ASP.NET Core Web API project

- Configure Serilog for structured logging
- Add Swagger for API documentation
- Set up CORS for frontend communication
- Create appsettings.TEMPLATE.json for team setup
```

---

## Key Learnings

### Git Workflow
1. Always work on a feature/develop branch, not `main`
2. Use `git status` frequently to understand state
3. Commit often with descriptive messages
4. Push regularly to backup your work

### .NET Development
1. Use `dotnet new` to scaffold projects
2. Add packages with `dotnet add package`
3. Configuration flows: appsettings.json → appsettings.{Environment}.json
4. Swagger requires explicit package in .NET 9+

### Security Practices
1. Never commit credentials or connection strings
2. Use `.gitignore` before creating sensitive files
3. Use template files to document required configuration
4. Keep sensitive config in environment-specific files

---

## Improvement Opportunities

| Area | Current State | Suggested Improvement |
|------|---------------|----------------------|
| **Branch Protection** | None | Enable on GitHub to require PR reviews |
| **Commit Messages** | Basic | Use conventional commits format |
| **Folder Setup** | Manual commands | Create setup script |
| **Package Versions** | Floating | Pin specific versions |
| **Error Handling** | Default | Add global exception handler |
| **Port Configuration** | Random | Set consistent port in launchSettings |
| **Documentation** | Template file | Add setup README |

---

## Command Reference

### Git Commands
| Command | Purpose |
|---------|---------|
| `git clone URL` | Download repository |
| `git checkout -b BRANCH` | Create and switch to branch |
| `git branch` | List branches (current marked with *) |
| `git status` | Show changed files |
| `git add .` | Stage all changes |
| `git commit -m "message"` | Create commit |
| `git push origin BRANCH` | Upload to GitHub |
| `git pull origin BRANCH` | Download latest changes |

### .NET Commands
| Command | Purpose |
|---------|---------|
| `dotnet --version` | Check SDK version |
| `dotnet new webapi -n NAME` | Create Web API project |
| `dotnet add package NAME` | Install NuGet package |
| `dotnet restore` | Download all packages |
| `dotnet run` | Start application |
| `dotnet build` | Compile without running |

### PowerShell Commands
| Command | Purpose |
|---------|---------|
| `pwd` | Print working directory |
| `cd PATH` | Change directory |
| `New-Item -ItemType Directory -Path PATH` | Create folder |
| `New-Item -ItemType File -Path PATH` | Create file |
| `Get-Content FILE` | Read file contents |
| `Get-ChildItem` | List directory contents |

---

## Next Steps (Day 3)

- Set up React frontend
- Install Material-UI
- Configure API connection
- Create basic components

---

**Document Created:** December 27, 2024
**Last Updated:** December 27, 2024
