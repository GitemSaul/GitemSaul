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

## 🤖 Claude Code vs Claude Chat - Usage Guide

**This roadmap works with BOTH tools. Here's when to use each:**

### Use **Claude Code** (Terminal/IDE Integration) For:
- 🔧 **All actual development work** (Days 1-18, 20)
- 📁 Creating files and folder structures
- ⚙️ Running commands (`dotnet`, `npm`, `git`)
- 🧪 Testing and debugging your application
- 💻 Writing backend services and frontend components
- 🐳 Docker builds and deployments
- ✅ Checking off tasks in THIS roadmap as you complete them

### Use **Claude Chat** (This Interface) For:
- 💡 Conceptual questions and learning
- 🏗️ Architecture and design decisions
- 📚 Understanding security principles
- 🤔 "Why does this work this way?"
- 📖 Generating documentation (Days 19, 21)
- 🔍 Code review and feedback
- 🆘 Troubleshooting complex issues

### Recommended Workflow by Phase:

**Phase 0-1 (Days 1-10): Foundation & Backend**
- **Primary:** Claude Code (90% of time)
- **Secondary:** Chat for questions about Dapper, security patterns, architecture

**Phase 2 (Days 11-15): Frontend**
- **Primary:** Claude Code (85% of time)
- **Secondary:** Chat for React patterns, component design questions

**Phase 3 (Days 16-18): Integration & Testing**
- **Primary:** Claude Code (80% of time)
- **Secondary:** Chat for debugging strategies, performance optimization

**Phase 4 (Days 19-22): Documentation & Polish**
- **Primary:** Split 50/50
- **Code:** Docker setup, final testing, commits
- **Chat:** README, case studies, learning documentation

### How to Switch Between Tools:

**Starting in Claude Code (Recommended for Days 1-18):**
```
Prompt: "I'm working on the Troubleshooting Toolkit project. Load PROJECT_ROADMAP.md 
from my project files and let's start Day X. Check off tasks as I complete them."
```

**When You Need Help in Chat:**
```
Prompt: "I'm on Day X of my project roadmap. [Describe your specific question]. 
The roadmap is in my project files."
```

**Returning to Claude Code:**
```
Prompt: "Continue where we left off on Day X. Update the roadmap with completed tasks."
```

### Quick Decision Guide:
- **Need to CREATE files?** → Claude Code
- **Need to RUN commands?** → Claude Code  
- **Need to UNDERSTAND concepts?** → Chat
- **Need to WRITE documentation?** → Chat
- **Need to DEBUG code?** → Claude Code (with Chat for strategy)
- **Need to TEST features?** → Claude Code

**📋 For detailed day-by-day tool usage, see [TOOL_USAGE_GUIDE.md](/mnt/project/TOOL_USAGE_GUIDE.md)**

---

## Phase 0: Foundation & Setup
**Duration:** 3 days (9-12 hours total)  
**Goal:** Repository structure, development environment, core architecture decisions  
**🔧 Tool: Claude Code (100%)** - File creation, Git operations, running all setup commands

### Day 1 - Repository & Project Structure (3-4 hours)
**🔧 Claude Code** | Creating folders, Git init, .gitignore

#### âœ… TODO List:
- [ ] Create GitHub repository: `troubleshooting-toolkit`
- [ ] Initialize with README.md (basic description)
- [ ] Create comprehensive .gitignore for .NET and React
- [ ] Set up repository structure (see below)
- [ ] Create initial commit: "Initial project structure"
- [ ] Create development branch: `git checkout -b develop`

#### ðŸ“ Repository Structure to Create:
```
troubleshooting-toolkit/
â”œâ”€â”€ .gitignore
â”œâ”€â”€ README.md
â”œâ”€â”€ PROJECT_ROADMAP.md (this file)
â”œâ”€â”€ backend/
â”‚   â”œâ”€â”€ Toolkit.Api/
â”‚   â”‚   â”œâ”€â”€ Controllers/
â”‚   â”‚   â”œâ”€â”€ Services/
â”‚   â”‚   â”œâ”€â”€ Models/
â”‚   â”‚   â”œâ”€â”€ Configuration/
â”‚   â”‚   â”œâ”€â”€ Program.cs
â”‚   â”‚   â””â”€â”€ Toolkit.Api.csproj
â”‚   â”œâ”€â”€ tests/
â”‚   â”‚   â””â”€â”€ Toolkit.Tests/
â”‚   â”œâ”€â”€ schema_exports/      # For CSV files from SQL script
â”‚   â”‚   â””â”€â”€ .gitkeep
â”‚   â”œâ”€â”€ appsettings.json
â”‚   â”œâ”€â”€ appsettings.TEMPLATE.json
â”‚   â””â”€â”€ Dockerfile
â”œâ”€â”€ frontend/
â”‚   â”œâ”€â”€ src/
â”‚   â”œâ”€â”€ public/
â”‚   â”œâ”€â”€ package.json
â”‚   â””â”€â”€ Dockerfile
â”œâ”€â”€ docs/
â”‚   â”œâ”€â”€ architecture.md
â”‚   â””â”€â”€ api-documentation.md
â”œâ”€â”€ learning/
â”‚   â””â”€â”€ credential-storage-explained.md
â”œâ”€â”€ docker-compose.yml
â””â”€â”€ .github/
    â””â”€â”€ workflows/
        â””â”€â”€ ci.yml (for later)
```

#### ðŸ”§ Commands to Run:
```bash
# Create repository structure
mkdir -p troubleshooting-toolkit/{backend/Toolkit.Api/{Controllers,Services,Models,Configuration},backend/tests/Toolkit.Tests,backend/schema_exports,frontend/{src,public},docs,learning,.github/workflows}

cd troubleshooting-toolkit

# Initialize Git
git init
git checkout -b main

# Create .gitignore
# (Copy comprehensive .NET + React .gitignore)

# First commit
git add .
git commit -m "Initial project structure"
git checkout -b develop
```

#### ðŸ“ Deliverables:
- Clean repository structure
- Proper .gitignore configured
- Main and develop branches created

---

### Day 2 - Backend Project Setup (3-4 hours)
**🔧 Claude Code** | dotnet commands, NuGet packages, Program.cs configuration

#### âœ… TODO List:
- [ ] Install .NET 8 SDK (if not already installed)
- [ ] Create ASP.NET Core Web API project
- [ ] Add required NuGet packages
- [ ] Configure CORS for frontend communication
- [ ] Set up logging with Serilog
- [ ] Create appsettings.TEMPLATE.json
- [ ] Test that API runs successfully
- [ ] Commit: "Backend API project setup with dependencies"

#### ðŸ”§ Commands to Run:
```bash
cd backend/Toolkit.Api

# Create Web API project
dotnet new webapi -n Toolkit.Api --framework net8.0

# Add required packages
dotnet add package Dapper
dotnet add package Microsoft.Data.SqlClient
dotnet add package Serilog.AspNetCore
dotnet add package Serilog.Sinks.Console
dotnet add package Serilog.Sinks.File

# Restore packages
dotnet restore

# Test run
dotnet run
# Should see: "Now listening on: http://localhost:5000"
```

#### ðŸ“ Files to Create:

**appsettings.json** (base config):
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
  }
}
```

**appsettings.TEMPLATE.json** (for team members):
```json
{
  "ConnectionStrings": {
    "DefaultConnection": "Server=YOUR_SERVER_HERE;Database=YOUR_DATABASE;User Id=YOUR_USER;Password=YOUR_PASSWORD;TrustServerCertificate=True;"
  },
  "DatabaseProfiles": {
    "Production": {
      "Name": "Your Database Name",
      "ConnectionStringKey": "DefaultConnection",
      "Description": "Main production database",
      "ReadOnly": true
    }
  }
}
```

**Program.cs** (updated with CORS and Serilog):
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

// Add services
builder.Services.AddControllers();
builder.Services.AddEndpointsApiExplorer();
builder.Services.AddSwaggerGen();

// Configure CORS
var allowedOrigins = builder.Configuration.GetSection("Cors:AllowedOrigins").Get<string[]>();
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

if (app.Environment.IsDevelopment())
{
    app.UseSwagger();
    app.UseSwaggerUI();
}

app.UseCors("AllowFrontend");
app.UseAuthorization();
app.MapControllers();

Log.Information("Application starting...");
app.Run();
```

#### ðŸ“ Deliverables:
- Working ASP.NET Core API
- All dependencies installed
- CORS configured
- Logging configured
- Template files for configuration

---

### Day 3 - Frontend Setup & Schema Preparation (3-4 hours)
**🔧 Claude Code** | npm commands, React setup | **Manual:** SSMS for schema extraction

#### âœ… TODO List:
- [ ] Install Node.js (if not already installed)
- [ ] Create React application
- [ ] Install frontend dependencies
- [ ] Configure environment variables
- [ ] Create basic folder structure
- [ ] Test frontend runs successfully
- [ ] Run schema extraction SQL script
- [ ] Export schema CSVs to backend/schema_exports/
- [ ] Commit: "Frontend setup and schema extraction complete"

#### ðŸ”§ Commands to Run:
```bash
cd frontend

# Create React app with TypeScript (optional, or use regular JS)
npx create-react-app . --template typescript
# OR for regular JavaScript:
npx create-react-app .

# Install dependencies
npm install axios
npm install @mui/material @emotion/react @emotion/styled
npm install react-router-dom

# Test run
npm start
# Should open browser at http://localhost:3000
```

#### ðŸ“ Frontend Folder Structure to Create:
```
frontend/src/
â”œâ”€â”€ components/
â”‚   â”œâ”€â”€ common/           # Reusable components
â”‚   â”œâ”€â”€ database/         # Database-related components
â”‚   â””â”€â”€ checks/           # Check-specific components
â”œâ”€â”€ pages/
â”‚   â”œâ”€â”€ Dashboard.js
â”‚   â””â”€â”€ CheckResults.js
â”œâ”€â”€ services/
â”‚   â”œâ”€â”€ api.js           # Axios configuration
â”‚   â””â”€â”€ databaseService.js
â”œâ”€â”€ utils/
â”‚   â””â”€â”€ helpers.js
â”œâ”€â”€ App.js
â””â”€â”€ index.js
```

#### ðŸ“ Create Environment File:

**.env.development**:
```
REACT_APP_API_URL=http://localhost:5000
```

**.env.production**:
```
REACT_APP_API_URL=https://your-deployed-api.com
```

#### ðŸ—„ï¸ Schema Extraction Tasks:
- [ ] Open SQL Server Management Studio (SSMS)
- [ ] Connect to Revention database
- [ ] Run `master_schema_extraction.sql` script
- [ ] Export each result set as CSV:
  - Right-click results â†’ Save Results As...
  - Save to `backend/schema_exports/`
  - Name files: 01_tables.csv, 02_columns.csv, etc.
- [ ] Verify all 14 CSV files are exported
- [ ] Add CSVs to Git: `git add backend/schema_exports/*.csv`

#### ðŸ“ Deliverables:
- Working React application
- Frontend dependencies installed
- Environment configuration ready
- All 14 schema CSV files exported and stored
- Both frontend and backend running successfully

---

## Phase 1: Backend Core Development
**Duration:** 7-10 days (21-40 hours total)  
**Goal:** Complete backend API with all SQL forensics features  
**🔧 Tool: Claude Code (90%)** | 💬 Chat (10%) for Dapper/security questions

### Day 4 - Database Connection Infrastructure (3-4 hours)
**🔧 Claude Code** | Models, services, controllers, dependency injection

#### âœ… TODO List:
- [ ] Create DatabaseProfile model
- [ ] Create DatabaseConnectionService
- [ ] Create DatabaseController for profile endpoints
- [ ] Register services in Program.cs
- [ ] Create your personal appsettings.Development.json
- [ ] Test profile retrieval via Swagger
- [ ] Commit: "Database connection service with profile support"

#### ðŸ“ Files to Create:

**Models/DatabaseProfile.cs**:
```csharp
namespace Toolkit.Api.Models
{
    public class DatabaseProfile
    {
        public string Name { get; set; }
        public string ConnectionStringKey { get; set; }
        public string Description { get; set; }
        public bool ReadOnly { get; set; } = true;
    }

    public class DatabaseProfileInfo
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public string Description { get; set; }
        public bool ReadOnly { get; set; }
    }
}
```

**Services/IDatabaseConnectionService.cs**:
```csharp
using Toolkit.Api.Models;

namespace Toolkit.Api.Services
{
    public interface IDatabaseConnectionService
    {
        string GetConnectionString(string profileId);
        List<DatabaseProfileInfo> GetAvailableProfiles();
        bool ValidateProfile(string profileId);
    }
}
```

**Services/DatabaseConnectionService.cs**:
```csharp
using Microsoft.Extensions.Configuration;
using Microsoft.Extensions.Logging;
using Toolkit.Api.Models;

namespace Toolkit.Api.Services
{
    public class DatabaseConnectionService : IDatabaseConnectionService
    {
        private readonly IConfiguration _configuration;
        private readonly ILogger<DatabaseConnectionService> _logger;
        private readonly Dictionary<string, DatabaseProfile> _profiles;

        public DatabaseConnectionService(
            IConfiguration configuration,
            ILogger<DatabaseConnectionService> logger)
        {
            _configuration = configuration;
            _logger = logger;
            
            _profiles = _configuration
                .GetSection("DatabaseProfiles")
                .Get<Dictionary<string, DatabaseProfile>>() 
                ?? new Dictionary<string, DatabaseProfile>();

            _logger.LogInformation($"Loaded {_profiles.Count} database profiles");
        }

        public string GetConnectionString(string profileId)
        {
            if (!_profiles.ContainsKey(profileId))
            {
                _logger.LogWarning($"Invalid profile requested: {profileId}");
                throw new ArgumentException($"Database profile '{profileId}' not found");
            }

            var profile = _profiles[profileId];
            var connectionString = _configuration.GetConnectionString(profile.ConnectionStringKey);

            if (string.IsNullOrEmpty(connectionString))
            {
                _logger.LogError($"Connection string not found for profile: {profileId}");
                throw new InvalidOperationException($"Connection string not configured");
            }

            return connectionString;
        }

        public List<DatabaseProfileInfo> GetAvailableProfiles()
        {
            return _profiles.Select(kvp => new DatabaseProfileInfo
            {
                Id = kvp.Key,
                Name = kvp.Value.Name,
                Description = kvp.Value.Description,
                ReadOnly = kvp.Value.ReadOnly
            }).ToList();
        }

        public bool ValidateProfile(string profileId)
        {
            return _profiles.ContainsKey(profileId);
        }
    }
}
```

**Controllers/DatabaseController.cs**:
```csharp
using Microsoft.AspNetCore.Mvc;
using Toolkit.Api.Services;

namespace Toolkit.Api.Controllers
{
    [ApiController]
    [Route("api/[controller]")]
    public class DatabaseController : ControllerBase
    {
        private readonly IDatabaseConnectionService _connectionService;
        private readonly ILogger<DatabaseController> _logger;

        public DatabaseController(
            IDatabaseConnectionService connectionService,
            ILogger<DatabaseController> logger)
        {
            _connectionService = connectionService;
            _logger = logger;
        }

        [HttpGet("profiles")]
        public IActionResult GetProfiles()
        {
            try
            {
                var profiles = _connectionService.GetAvailableProfiles();
                return Ok(profiles);
            }
            catch (Exception ex)
            {
                _logger.LogError(ex, "Error retrieving database profiles");
                return StatusCode(500, "Failed to retrieve profiles");
            }
        }

        [HttpGet("test-connection/{profileId}")]
        public async Task<IActionResult> TestConnection(string profileId)
        {
            try
            {
                var connectionString = _connectionService.GetConnectionString(profileId);
                
                using var connection = new Microsoft.Data.SqlClient.SqlConnection(connectionString);
                await connection.OpenAsync();
                
                return Ok(new { success = true, message = "Connection successful" });
            }
            catch (Exception ex)
            {
                _logger.LogError(ex, $"Connection test failed for profile: {profileId}");
                return BadRequest(new { success = false, message = ex.Message });
            }
        }
    }
}
```

**Update Program.cs** (add this line):
```csharp
builder.Services.AddSingleton<IDatabaseConnectionService, DatabaseConnectionService>();
```

#### ðŸ§ª Testing Tasks:
- [ ] Run backend: `dotnet run`
- [ ] Open Swagger: http://localhost:5000/swagger
- [ ] Test GET /api/database/profiles
- [ ] Test GET /api/database/test-connection/{profileId}
- [ ] Verify connection works with your database

#### ðŸ“ Deliverables:
- Database connection service working
- Profile system functional
- Connection testing endpoint working
- All endpoints documented in Swagger

---

### Day 5 - Schema Configuration System (3-4 hours)
**🔧 Claude Code** | Schema models, JSON parsing, validation logic

#### âœ… TODO List:
- [ ] Create schema models (Table, Column, ForeignKey, etc.)
- [ ] Create SchemaLoader service to parse CSV files
- [ ] Create schema.json configuration file from exported CSVs
- [ ] Add validation for table/column names (SQL injection prevention)
- [ ] Test schema loading on startup
- [ ] Commit: "Schema configuration and validation system"

#### ðŸ“ Files to Create:

**Models/Schema.cs**:
```csharp
namespace Toolkit.Api.Models.Schema
{
    public class TableSchema
    {
        public string SchemaName { get; set; }
        public string TableName { get; set; }
        public string FullName => $"{SchemaName}.{TableName}";
        public List<ColumnSchema> Columns { get; set; } = new();
        public List<string> PrimaryKeyColumns { get; set; } = new();
        public List<ForeignKeySchema> ForeignKeys { get; set; } = new();
        public List<UniqueConstraintSchema> UniqueConstraints { get; set; } = new();
    }

    public class ColumnSchema
    {
        public string ColumnName { get; set; }
        public string DataType { get; set; }
        public bool IsNullable { get; set; }
        public bool IsIdentity { get; set; }
        public bool IsComputed { get; set; }
    }

    public class ForeignKeySchema
    {
        public string ConstraintName { get; set; }
        public string ColumnName { get; set; }
        public string ReferencedTable { get; set; }
        public string ReferencedColumn { get; set; }
        public string DeleteRule { get; set; }
    }

    public class UniqueConstraintSchema
    {
        public string ConstraintName { get; set; }
        public List<string> Columns { get; set; } = new();
    }

    public class DatabaseSchema
    {
        public Dictionary<string, TableSchema> Tables { get; set; } = new();
        
        public TableSchema GetTable(string schemaName, string tableName)
        {
            var fullName = $"{schemaName}.{tableName}";
            return Tables.GetValueOrDefault(fullName);
        }

        public bool IsValidTable(string schemaName, string tableName)
        {
            var fullName = $"{schemaName}.{tableName}";
            return Tables.ContainsKey(fullName);
        }

        public bool IsValidColumn(string schemaName, string tableName, string columnName)
        {
            var table = GetTable(schemaName, tableName);
            return table?.Columns.Any(c => c.ColumnName == columnName) ?? false;
        }
    }
}
```

**Services/ISchemaService.cs**:
```csharp
using Toolkit.Api.Models.Schema;

namespace Toolkit.Api.Services
{
    public interface ISchemaService
    {
        DatabaseSchema GetSchema();
        bool ValidateTable(string schemaName, string tableName);
        bool ValidateColumns(string schemaName, string tableName, params string[] columns);
        TableSchema GetTableSchema(string schemaName, string tableName);
    }
}
```

**Services/SchemaService.cs**:
```csharp
using System.Text.Json;
using Toolkit.Api.Models.Schema;

namespace Toolkit.Api.Services
{
    public class SchemaService : ISchemaService
    {
        private readonly DatabaseSchema _schema;
        private readonly ILogger<SchemaService> _logger;

        public SchemaService(IConfiguration configuration, ILogger<SchemaService> logger)
        {
            _logger = logger;
            _schema = LoadSchemaFromConfiguration(configuration);
            _logger.LogInformation($"Loaded schema with {_schema.Tables.Count} tables");
        }

        private DatabaseSchema LoadSchemaFromConfiguration(IConfiguration configuration)
        {
            // For now, we'll load from a JSON file
            // Later we can add CSV parsing if needed
            var schemaPath = configuration["SchemaConfiguration:FilePath"] 
                ?? "Configuration/schema.json";

            if (!File.Exists(schemaPath))
            {
                _logger.LogWarning($"Schema file not found at {schemaPath}, returning empty schema");
                return new DatabaseSchema();
            }

            var json = File.ReadAllText(schemaPath);
            return JsonSerializer.Deserialize<DatabaseSchema>(json) 
                ?? new DatabaseSchema();
        }

        public DatabaseSchema GetSchema() => _schema;

        public bool ValidateTable(string schemaName, string tableName)
        {
            return _schema.IsValidTable(schemaName, tableName);
        }

        public bool ValidateColumns(string schemaName, string tableName, params string[] columns)
        {
            if (!ValidateTable(schemaName, tableName))
                return false;

            return columns.All(col => _schema.IsValidColumn(schemaName, tableName, col));
        }

        public TableSchema GetTableSchema(string schemaName, string tableName)
        {
            return _schema.GetTable(schemaName, tableName);
        }
    }
}
```

**Configuration/schema.json** (example structure - you'll populate from CSV):
```json
{
  "Tables": {
    "dbo.YourTableName": {
      "SchemaName": "dbo",
      "TableName": "YourTableName",
      "Columns": [
        {
          "ColumnName": "Id",
          "DataType": "int",
          "IsNullable": false,
          "IsIdentity": true,
          "IsComputed": false
        }
      ],
      "PrimaryKeyColumns": ["Id"],
      "ForeignKeys": [],
      "UniqueConstraints": []
    }
  }
}
```

**Update Program.cs**:
```csharp
builder.Services.AddSingleton<ISchemaService, SchemaService>();
```

**Update appsettings.json**:
```json
{
  "SchemaConfiguration": {
    "FilePath": "Configuration/schema.json"
  }
}
```

#### ðŸ”§ Manual Task (Do this today):
- [ ] Convert your exported CSVs into schema.json format
- [ ] Start with 2-3 tables as proof of concept
- [ ] Add more tables as you need them for testing

#### ðŸ“ Deliverables:
- Schema models created
- Schema service loads configuration
- Validation methods working
- At least 2-3 tables configured in schema.json

---

### Day 6 - Duplicate Detection Service (3-4 hours)
**🔧 Claude Code** | Dapper queries, SQL forensics service | 💬 Chat for SQL injection prevention questions

#### âœ… TODO List:
- [ ] Create DuplicateCheckRequest/Response models
- [ ] Create SqlForensicsService with DetectDuplicates method
- [ ] Create SqlController with duplicate detection endpoint
- [ ] Add input validation using SchemaService
- [ ] Write unit tests for duplicate detection
- [ ] Test with Swagger using real database
- [ ] Commit: "Duplicate detection feature complete"

#### ðŸ“ Files to Create:

**Models/Requests/DuplicateCheckRequest.cs**:
```csharp
namespace Toolkit.Api.Models.Requests
{
    public class DuplicateCheckRequest
    {
        public string ProfileId { get; set; }
        public string SchemaName { get; set; } = "dbo";
        public string TableName { get; set; }
        public List<string> UniqueColumns { get; set; } = new();
    }
}
```

**Models/Responses/DuplicateCheckResponse.cs**:
```csharp
namespace Toolkit.Api.Models.Responses
{
    public class DuplicateCheckResponse
    {
        public bool Success { get; set; }
        public string Message { get; set; }
        public int DuplicateGroupCount { get; set; }
        public int TotalDuplicateRows { get; set; }
        public List<DuplicateGroup> Duplicates { get; set; } = new();
    }

    public class DuplicateGroup
    {
        public Dictionary<string, object> KeyValues { get; set; } = new();
        public int OccurrenceCount { get; set; }
    }
}
```

**Services/ISqlForensicsService.cs**:
```csharp
using Toolkit.Api.Models.Requests;
using Toolkit.Api.Models.Responses;

namespace Toolkit.Api.Services
{
    public interface ISqlForensicsService
    {
        Task<DuplicateCheckResponse> DetectDuplicatesAsync(DuplicateCheckRequest request);
    }
}
```

**Services/SqlForensicsService.cs**:
```csharp
using Dapper;
using Microsoft.Data.SqlClient;
using Toolkit.Api.Models.Requests;
using Toolkit.Api.Models.Responses;

namespace Toolkit.Api.Services
{
    public class SqlForensicsService : ISqlForensicsService
    {
        private readonly IDatabaseConnectionService _connectionService;
        private readonly ISchemaService _schemaService;
        private readonly ILogger<SqlForensicsService> _logger;

        public SqlForensicsService(
            IDatabaseConnectionService connectionService,
            ISchemaService schemaService,
            ILogger<SqlForensicsService> logger)
        {
            _connectionService = connectionService;
            _schemaService = schemaService;
            _logger = logger;
        }

        public async Task<DuplicateCheckResponse> DetectDuplicatesAsync(DuplicateCheckRequest request)
        {
            try
            {
                // Validate inputs
                if (!_schemaService.ValidateTable(request.SchemaName, request.TableName))
                {
                    return new DuplicateCheckResponse
                    {
                        Success = false,
                        Message = $"Invalid table: {request.SchemaName}.{request.TableName}"
                    };
                }

                if (!_schemaService.ValidateColumns(request.SchemaName, request.TableName, 
                    request.UniqueColumns.ToArray()))
                {
                    return new DuplicateCheckResponse
                    {
                        Success = false,
                        Message = "One or more invalid columns specified"
                    };
                }

                // Get connection string
                var connectionString = _connectionService.GetConnectionString(request.ProfileId);

                // Build safe SQL query
                var tableName = $"[{request.SchemaName}].[{request.TableName}]";
                var columns = string.Join(", ", request.UniqueColumns.Select(c => $"[{c}]"));
                
                var query = $@"
                    SELECT {columns}, COUNT(*) as OccurrenceCount
                    FROM {tableName}
                    GROUP BY {columns}
                    HAVING COUNT(*) > 1
                    ORDER BY COUNT(*) DESC";

                _logger.LogInformation($"Executing duplicate check on {tableName}");

                using var connection = new SqlConnection(connectionString);
                var results = await connection.QueryAsync<dynamic>(query);

                var duplicates = results.Select(row =>
                {
                    var dict = (IDictionary<string, object>)row;
                    var keyValues = new Dictionary<string, object>();
                    
                    foreach (var col in request.UniqueColumns)
                    {
                        if (dict.ContainsKey(col))
                            keyValues[col] = dict[col];
                    }

                    return new DuplicateGroup
                    {
                        KeyValues = keyValues,
                        OccurrenceCount = Convert.ToInt32(dict["OccurrenceCount"])
                    };
                }).ToList();

                var totalDuplicates = duplicates.Sum(d => d.OccurrenceCount);

                return new DuplicateCheckResponse
                {
                    Success = true,
                    Message = $"Found {duplicates.Count} duplicate groups",
                    DuplicateGroupCount = duplicates.Count,
                    TotalDuplicateRows = totalDuplicates,
                    Duplicates = duplicates
                };
            }
            catch (Exception ex)
            {
                _logger.LogError(ex, "Error during duplicate detection");
                return new DuplicateCheckResponse
                {
                    Success = false,
                    Message = $"Error: {ex.Message}"
                };
            }
        }
    }
}
```

**Controllers/SqlController.cs**:
```csharp
using Microsoft.AspNetCore.Mvc;
using Toolkit.Api.Models.Requests;
using Toolkit.Api.Services;

namespace Toolkit.Api.Controllers
{
    [ApiController]
    [Route("api/[controller]")]
    public class SqlController : ControllerBase
    {
        private readonly ISqlForensicsService _forensicsService;
        private readonly ILogger<SqlController> _logger;

        public SqlController(
            ISqlForensicsService forensicsService,
            ILogger<SqlController> logger)
        {
            _forensicsService = forensicsService;
            _logger = logger;
        }

        [HttpPost("check-duplicates")]
        public async Task<IActionResult> CheckDuplicates([FromBody] DuplicateCheckRequest request)
        {
            if (request == null)
                return BadRequest("Request body is required");

            if (string.IsNullOrEmpty(request.ProfileId))
                return BadRequest("ProfileId is required");

            if (string.IsNullOrEmpty(request.TableName))
                return BadRequest("TableName is required");

            if (request.UniqueColumns == null || !request.UniqueColumns.Any())
                return BadRequest("At least one unique column is required");

            var result = await _forensicsService.DetectDuplicatesAsync(request);

            if (!result.Success)
                return BadRequest(result);

            return Ok(result);
        }
    }
}
```

**Update Program.cs**:
```csharp
builder.Services.AddScoped<ISqlForensicsService, SqlForensicsService>();
```

#### ðŸ§ª Testing Tasks:
- [ ] Run backend
- [ ] Open Swagger
- [ ] Test POST /api/sql/check-duplicates with valid data
- [ ] Verify it finds actual duplicates in your database
- [ ] Test with invalid table name (should return error)
- [ ] Test with invalid column name (should return error)

#### ðŸ“ Deliverables:
- Duplicate detection working end-to-end
- Input validation preventing SQL injection
- Proper error handling
- Swagger documentation for endpoint

---

### Day 7 - Orphaned Records Detection (3-4 hours)

#### âœ… TODO List:
- [ ] Create OrphanCheckRequest/Response models
- [ ] Add DetectOrphansAsync method to SqlForensicsService
- [ ] Add orphan detection endpoint to SqlController
- [ ] Test with tables that have foreign keys
- [ ] Commit: "Orphaned records detection feature"

#### ðŸ“ Files to Create:

**Models/Requests/OrphanCheckRequest.cs**:
```csharp
namespace Toolkit.Api.Models.Requests
{
    public class OrphanCheckRequest
    {
        public string ProfileId { get; set; }
        public string SchemaName { get; set; } = "dbo";
        public string TableName { get; set; }
        public string ForeignKeyColumn { get; set; }
        public string ReferencedTable { get; set; }
        public string ReferencedColumn { get; set; }
    }
}
```

**Models/Responses/OrphanCheckResponse.cs**:
```csharp
namespace Toolkit.Api.Models.Responses
{
    public class OrphanCheckResponse
    {
        public bool Success { get; set; }
        public string Message { get; set; }
        public int OrphanCount { get; set; }
        public List<OrphanRecord> Orphans { get; set; } = new();
    }

    public class OrphanRecord
    {
        public Dictionary<string, object> RecordData { get; set; } = new();
    }
}
```

**Add to SqlForensicsService.cs**:
```csharp
public async Task<OrphanCheckResponse> DetectOrphansAsync(OrphanCheckRequest request)
{
    try
    {
        // Validate inputs
        if (!_schemaService.ValidateTable(request.SchemaName, request.TableName))
        {
            return new OrphanCheckResponse
            {
                Success = false,
                Message = $"Invalid table: {request.SchemaName}.{request.TableName}"
            };
        }

        var connectionString = _connectionService.GetConnectionString(request.ProfileId);

        // Build safe SQL query using LEFT JOIN
        var childTable = $"[{request.SchemaName}].[{request.TableName}]";
        var parentTable = $"[{request.ReferencedTable}]";
        
        var query = $@"
            SELECT c.*
            FROM {childTable} c
            LEFT JOIN {parentTable} p ON c.[{request.ForeignKeyColumn}] = p.[{request.ReferencedColumn}]
            WHERE p.[{request.ReferencedColumn}] IS NULL
                AND c.[{request.ForeignKeyColumn}] IS NOT NULL";

        _logger.LogInformation($"Checking for orphaned records in {childTable}");

        using var connection = new SqlConnection(connectionString);
        var results = await connection.QueryAsync<dynamic>(query);

        var orphans = results.Select(row =>
        {
            var dict = (IDictionary<string, object>)row;
            return new OrphanRecord
            {
                RecordData = new Dictionary<string, object>(dict)
            };
        }).ToList();

        return new OrphanCheckResponse
        {
            Success = true,
            Message = $"Found {orphans.Count} orphaned records",
            OrphanCount = orphans.Count,
            Orphans = orphans
        };
    }
    catch (Exception ex)
    {
        _logger.LogError(ex, "Error during orphan detection");
        return new OrphanCheckResponse
        {
            Success = false,
            Message = $"Error: {ex.Message}"
        };
    }
}
```

**Add to ISqlForensicsService.cs**:
```csharp
Task<OrphanCheckResponse> DetectOrphansAsync(OrphanCheckRequest request);
```

**Add to SqlController.cs**:
```csharp
[HttpPost("check-orphans")]
public async Task<IActionResult> CheckOrphans([FromBody] OrphanCheckRequest request)
{
    if (request == null)
        return BadRequest("Request body is required");

    if (string.IsNullOrEmpty(request.ProfileId))
        return BadRequest("ProfileId is required");

    if (string.IsNullOrEmpty(request.TableName))
        return BadRequest("TableName is required");

    if (string.IsNullOrEmpty(request.ForeignKeyColumn))
        return BadRequest("ForeignKeyColumn is required");

    var result = await _forensicsService.DetectOrphansAsync(request);

    if (!result.Success)
        return BadRequest(result);

    return Ok(result);
}
```

#### ðŸ§ª Testing Tasks:
- [ ] Test with tables that have foreign keys
- [ ] Verify orphaned records are detected correctly
- [ ] Test error handling

#### ðŸ“ Deliverables:
- Orphan detection working
- Endpoint tested and documented

---

### Day 8 - Stored Procedures Check (3-4 hours)

#### âœ… TODO List:
- [ ] Create StoredProcedureCheckRequest/Response models
- [ ] Add DetectMissingStoredProceduresAsync method
- [ ] Add endpoint to SqlController
- [ ] Test with your database's expected stored procedures
- [ ] Commit: "Stored procedure validation feature"

#### ðŸ“ Files to Create:

**Models/Requests/StoredProcedureCheckRequest.cs**:
```csharp
namespace Toolkit.Api.Models.Requests
{
    public class StoredProcedureCheckRequest
    {
        public string ProfileId { get; set; }
        public List<string> ExpectedProcedures { get; set; } = new();
    }
}
```

**Models/Responses/StoredProcedureCheckResponse.cs**:
```csharp
namespace Toolkit.Api.Models.Responses
{
    public class StoredProcedureCheckResponse
    {
        public bool Success { get; set; }
        public string Message { get; set; }
        public List<string> MissingProcedures { get; set; } = new();
        public List<string> ExistingProcedures { get; set; } = new();
        public List<StoredProcedureInfo> AllProcedures { get; set; } = new();
    }

    public class StoredProcedureInfo
    {
        public string SchemaName { get; set; }
        public string ProcedureName { get; set; }
        public string FullName => $"{SchemaName}.{ProcedureName}";
        public DateTime? CreatedDate { get; set; }
        public DateTime? ModifiedDate { get; set; }
    }
}
```

**Add to SqlForensicsService.cs**:
```csharp
public async Task<StoredProcedureCheckResponse> DetectMissingStoredProceduresAsync(
    StoredProcedureCheckRequest request)
{
    try
    {
        var connectionString = _connectionService.GetConnectionString(request.ProfileId);

        var query = @"
            SELECT 
                SCHEMA_NAME(schema_id) as SchemaName,
                name as ProcedureName,
                create_date as CreatedDate,
                modify_date as ModifiedDate
            FROM sys.procedures
            WHERE is_ms_shipped = 0
            ORDER BY SchemaName, ProcedureName";

        using var connection = new SqlConnection(connectionString);
        var results = await connection.QueryAsync<StoredProcedureInfo>(query);
        
        var allProcedures = results.ToList();
        var existingNames = allProcedures.Select(p => p.FullName).ToHashSet();
        
        var missing = request.ExpectedProcedures
            .Where(expected => !existingNames.Contains(expected))
            .ToList();

        var existing = request.ExpectedProcedures
            .Where(expected => existingNames.Contains(expected))
            .ToList();

        return new StoredProcedureCheckResponse
        {
            Success = true,
            Message = missing.Any() 
                ? $"Found {missing.Count} missing procedures" 
                : "All expected procedures exist",
            MissingProcedures = missing,
            ExistingProcedures = existing,
            AllProcedures = allProcedures
        };
    }
    catch (Exception ex)
    {
        _logger.LogError(ex, "Error checking stored procedures");
        return new StoredProcedureCheckResponse
        {
            Success = false,
            Message = $"Error: {ex.Message}"
        };
    }
}
```

**Add to ISqlForensicsService.cs**:
```csharp
Task<StoredProcedureCheckResponse> DetectMissingStoredProceduresAsync(
    StoredProcedureCheckRequest request);
```

**Add to SqlController.cs**:
```csharp
[HttpPost("check-stored-procedures")]
public async Task<IActionResult> CheckStoredProcedures(
    [FromBody] StoredProcedureCheckRequest request)
{
    if (request == null)
        return BadRequest("Request body is required");

    if (string.IsNullOrEmpty(request.ProfileId))
        return BadRequest("ProfileId is required");

    var result = await _forensicsService.DetectMissingStoredProceduresAsync(request);

    if (!result.Success)
        return BadRequest(result);

    return Ok(result);
}
```

#### ðŸ“ Deliverables:
- Stored procedure checking complete
- Can detect missing procedures
- Lists all procedures in database

---

### Days 9-10 - Testing & Refinement (6-8 hours)

#### âœ… TODO List:
- [ ] Create unit tests for DatabaseConnectionService
- [ ] Create unit tests for SchemaService
- [ ] Create unit tests for SqlForensicsService
- [ ] Test all endpoints with invalid inputs
- [ ] Test error scenarios (database offline, wrong credentials, etc.)
- [ ] Add XML documentation comments to all public methods
- [ ] Update Swagger with better descriptions
- [ ] Performance test with large datasets
- [ ] Commit: "Unit tests and documentation complete"

#### ðŸ“ Testing Project Setup:

**Create tests/Toolkit.Tests/Toolkit.Tests.csproj**:
```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net8.0</TargetFramework>
    <IsPackable>false</IsPackable>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.NET.Test.Sdk" Version="17.8.0" />
    <PackageReference Include="xUnit" Version="2.6.2" />
    <PackageReference Include="xunit.runner.visualstudio" Version="2.5.4" />
    <PackageReference Include="Moq" Version="4.20.70" />
  </ItemGroup>

  <ItemGroup>
    <ProjectReference Include="..\..\Toolkit.Api\Toolkit.Api.csproj" />
  </ItemGroup>
</Project>
```

**Example Test: DatabaseConnectionServiceTests.cs**:
```csharp
using Xunit;
using Moq;
using Microsoft.Extensions.Configuration;
using Microsoft.Extensions.Logging;
using Toolkit.Api.Services;

namespace Toolkit.Tests.Services
{
    public class DatabaseConnectionServiceTests
    {
        [Fact]
        public void GetAvailableProfiles_ReturnsConfiguredProfiles()
        {
            // Arrange
            var configuration = new ConfigurationBuilder()
                .AddInMemoryCollection(new Dictionary<string, string>
                {
                    {"DatabaseProfiles:Test:Name", "Test Database"},
                    {"DatabaseProfiles:Test:ConnectionStringKey", "TestConnection"},
                    {"DatabaseProfiles:Test:ReadOnly", "true"}
                })
                .Build();

            var logger = new Mock<ILogger<DatabaseConnectionService>>();
            var service = new DatabaseConnectionService(configuration, logger.Object);

            // Act
            var profiles = service.GetAvailableProfiles();

            // Assert
            Assert.Single(profiles);
            Assert.Equal("Test", profiles[0].Id);
            Assert.True(profiles[0].ReadOnly);
        }

        [Fact]
        public void ValidateProfile_ValidProfile_ReturnsTrue()
        {
            // Similar setup as above
            // Test validation logic
        }

        [Fact]
        public void GetConnectionString_InvalidProfile_ThrowsException()
        {
            // Test error handling
        }
    }
}
```

#### ðŸ§ª Manual Testing Checklist:
- [ ] Test duplicate detection with actual duplicates
- [ ] Test duplicate detection with no duplicates
- [ ] Test orphan detection with orphaned records
- [ ] Test orphan detection with no orphans
- [ ] Test SP check with missing procedures
- [ ] Test all endpoints with invalid profile IDs
- [ ] Test all endpoints with invalid table names
- [ ] Test connection with wrong credentials
- [ ] Test with SQL injection attempts

#### ðŸ“ Deliverables:
- At least 10 unit tests written
- All endpoints manually tested
- Documentation complete
- Backend fully functional and tested

---

## Phase 2: Frontend Development
**Duration:** 5-7 days (15-28 hours total)  
**Goal:** Complete React frontend with all features

### Day 11 - Base Components & API Service (3-4 hours)

#### âœ… TODO List:
- [ ] Create API service wrapper with axios
- [ ] Create DatabaseSelector component
- [ ] Create LoadingSpinner component
- [ ] Create ErrorAlert component
- [ ] Set up React Router
- [ ] Create basic Dashboard page
- [ ] Test API connectivity
- [ ] Commit: "Frontend base components and API integration"

#### ðŸ“ Files to Create:

**src/services/api.js**:
```javascript
import axios from 'axios';

const API_BASE_URL = process.env.REACT_APP_API_URL || 'http://localhost:5000';

const api = axios.create({
  baseURL: `${API_BASE_URL}/api`,
  headers: {
    'Content-Type': 'application/json',
  },
});

// Request interceptor for logging
api.interceptors.request.use(
  (config) => {
    console.log('API Request:', config.method.toUpperCase(), config.url);
    return config;
  },
  (error) => {
    return Promise.reject(error);
  }
);

// Response interceptor for error handling
api.interceptors.response.use(
  (response) => response,
  (error) => {
    console.error('API Error:', error.response?.data || error.message);
    return Promise.reject(error);
  }
);

export default api;
```

**src/services/databaseService.js**:
```javascript
import api from './api';

export const databaseService = {
  // Get available database profiles
  getProfiles: async () => {
    const response = await api.get('/database/profiles');
    return response.data;
  },

  // Test database connection
  testConnection: async (profileId) => {
    const response = await api.get(`/database/test-connection/${profileId}`);
    return response.data;
  },
};
```

**src/services/sqlService.js**:
```javascript
import api from './api';

export const sqlService = {
  // Check for duplicates
  checkDuplicates: async (request) => {
    const response = await api.post('/sql/check-duplicates', request);
    return response.data;
  },

  // Check for orphaned records
  checkOrphans: async (request) => {
    const response = await api.post('/sql/check-orphans', request);
    return response.data;
  },

  // Check stored procedures
  checkStoredProcedures: async (request) => {
    const response = await api.post('/sql/check-stored-procedures', request);
    return response.data;
  },
};
```

**src/components/common/LoadingSpinner.js**:
```javascript
import React from 'react';
import { CircularProgress, Box, Typography } from '@mui/material';

function LoadingSpinner({ message = 'Loading...' }) {
  return (
    <Box 
      display="flex" 
      flexDirection="column" 
      alignItems="center" 
      justifyContent="center" 
      minHeight="200px"
    >
      <CircularProgress />
      <Typography variant="body2" color="textSecondary" sx={{ mt: 2 }}>
        {message}
      </Typography>
    </Box>
  );
}

export default LoadingSpinner;
```

**src/components/common/ErrorAlert.js**:
```javascript
import React from 'react';
import { Alert, AlertTitle } from '@mui/material';

function ErrorAlert({ error, onClose }) {
  if (!error) return null;

  return (
    <Alert severity="error" onClose={onClose} sx={{ mb: 2 }}>
      <AlertTitle>Error</AlertTitle>
      {error.message || error.toString()}
    </Alert>
  );
}

export default ErrorAlert;
```

**src/components/database/DatabaseSelector.js**:
```javascript
import React, { useState, useEffect } from 'react';
import {
  FormControl,
  InputLabel,
  Select,
  MenuItem,
  Box,
  Typography,
  Chip,
} from '@mui/material';
import { databaseService } from '../../services/databaseService';
import LoadingSpinner from '../common/LoadingSpinner';
import ErrorAlert from '../common/ErrorAlert';

function DatabaseSelector({ value, onChange }) {
  const [profiles, setProfiles] = useState([]);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    loadProfiles();
  }, []);

  const loadProfiles = async () => {
    try {
      setLoading(true);
      setError(null);
      const data = await databaseService.getProfiles();
      setProfiles(data);
    } catch (err) {
      setError(err);
    } finally {
      setLoading(false);
    }
  };

  if (loading) return <LoadingSpinner message="Loading database profiles..." />;
  if (error) return <ErrorAlert error={error} onClose={() => setError(null)} />;

  const selectedProfile = profiles.find(p => p.id === value);

  return (
    <Box>
      <FormControl fullWidth>
        <InputLabel>Select Database</InputLabel>
        <Select
          value={value}
          onChange={(e) => onChange(e.target.value)}
          label="Select Database"
        >
          <MenuItem value="">
            <em>-- Select Database --</em>
          </MenuItem>
          {profiles.map((profile) => (
            <MenuItem key={profile.id} value={profile.id}>
              {profile.name}
              {profile.readOnly && (
                <Chip 
                  label="Read-Only" 
                  size="small" 
                  color="info" 
                  sx={{ ml: 1 }} 
                />
              )}
            </MenuItem>
          ))}
        </Select>
      </FormControl>

      {selectedProfile && (
        <Typography 
          variant="caption" 
          color="textSecondary" 
          sx={{ mt: 1, display: 'block' }}
        >
          {selectedProfile.description}
        </Typography>
      )}
    </Box>
  );
}

export default DatabaseSelector;
```

**src/App.js**:
```javascript
import React from 'react';
import { BrowserRouter as Router, Routes, Route } from 'react-router-dom';
import { Container, AppBar, Toolbar, Typography } from '@mui/material';
import Dashboard from './pages/Dashboard';

function App() {
  return (
    <Router>
      <AppBar position="static">
        <Toolbar>
          <Typography variant="h6">
            SQL Forensics Toolkit
          </Typography>
        </Toolbar>
      </AppBar>

      <Container maxWidth="lg" sx={{ mt: 4 }}>
        <Routes>
          <Route path="/" element={<Dashboard />} />
        </Routes>
      </Container>
    </Router>
  );
}

export default App;
```

**src/pages/Dashboard.js** (basic):
```javascript
import React, { useState } from 'react';
import { Box, Typography, Paper } from '@mui/material';
import DatabaseSelector from '../components/database/DatabaseSelector';

function Dashboard() {
  const [selectedProfile, setSelectedProfile] = useState('');

  return (
    <Box>
      <Typography variant="h4" gutterBottom>
        Dashboard
      </Typography>

      <Paper sx={{ p: 3, mb: 3 }}>
        <Typography variant="h6" gutterBottom>
          Database Connection
        </Typography>
        <DatabaseSelector 
          value={selectedProfile}
          onChange={setSelectedProfile}
        />
      </Paper>

      {selectedProfile && (
        <Paper sx={{ p: 3 }}>
          <Typography variant="body1">
            Selected Profile: {selectedProfile}
          </Typography>
          {/* Check components will go here */}
        </Paper>
      )}
    </Box>
  );
}

export default Dashboard;
```

#### ðŸ§ª Testing Tasks:
- [ ] Run frontend: `npm start`
- [ ] Verify database selector loads profiles
- [ ] Select a profile and verify it displays correctly
- [ ] Check browser console for API calls
- [ ] Test error states (stop backend and try to load)

#### ðŸ“ Deliverables:
- Base components created
- API services working
- Database selector functional
- Basic dashboard structure

---

### Day 12 - Duplicate Check Component (3-4 hours)

#### âœ… TODO List:
- [ ] Create DuplicateCheckForm component
- [ ] Create DuplicateResultsTable component
- [ ] Integrate with Dashboard
- [ ] Test duplicate detection end-to-end
- [ ] Commit: "Duplicate check UI complete"

#### ðŸ“ Files to Create:

**src/components/checks/DuplicateCheckForm.js**:
```javascript
import React, { useState } from 'react';
import {
  Box,
  TextField,
  Button,
  Typography,
  Chip,
  Stack,
} from '@mui/material';
import { sqlService } from '../../services/sqlService';
import LoadingSpinner from '../common/LoadingSpinner';
import ErrorAlert from '../common/ErrorAlert';

function DuplicateCheckForm({ profileId, onResults }) {
  const [tableName, setTableName] = useState('');
  const [schemaName, setSchemaName] = useState('dbo');
  const [columnInput, setColumnInput] = useState('');
  const [columns, setColumns] = useState([]);
  const [loading, setLoading] = useState(false);
  const [error, setError] = useState(null);

  const handleAddColumn = () => {
    if (columnInput.trim() && !columns.includes(columnInput.trim())) {
      setColumns([...columns, columnInput.trim()]);
      setColumnInput('');
    }
  };

  const handleRemoveColumn = (columnToRemove) => {
    setColumns(columns.filter(col => col !== columnToRemove));
  };

  const handleSubmit = async (e) => {
    e.preventDefault();
    
    if (!tableName || columns.length === 0) {
      setError({ message: 'Please provide table name and at least one column' });
      return;
    }

    try {
      setLoading(true);
      setError(null);

      const request = {
        profileId,
        schemaName,
        tableName,
        uniqueColumns: columns,
      };

      const result = await sqlService.checkDuplicates(request);
      onResults(result);
    } catch (err) {
      setError(err);
    } finally {
      setLoading(false);
    }
  };

  if (loading) return <LoadingSpinner message="Checking for duplicates..." />;

  return (
    <Box component="form" onSubmit={handleSubmit}>
      <Typography variant="h6" gutterBottom>
        Duplicate Detection
      </Typography>

      {error && <ErrorAlert error={error} onClose={() => setError(null)} />}

      <Stack spacing={2}>
        <TextField
          label="Schema Name"
          value={schemaName}
          onChange={(e) => setSchemaName(e.target.value)}
          size="small"
          fullWidth
        />

        <TextField
          label="Table Name"
          value={tableName}
          onChange={(e) => setTableName(e.target.value)}
          size="small"
          required
          fullWidth
        />

        <Box>
          <Box display="flex" gap={1}>
            <TextField
              label="Column Name"
              value={columnInput}
              onChange={(e) => setColumnInput(e.target.value)}
              onKeyPress={(e) => {
                if (e.key === 'Enter') {
                  e.preventDefault();
                  handleAddColumn();
                }
              }}
              size="small"
              fullWidth
            />
            <Button 
              variant="outlined" 
              onClick={handleAddColumn}
              disabled={!columnInput.trim()}
            >
              Add
            </Button>
          </Box>

          <Box mt={1} display="flex" flexWrap="wrap" gap={1}>
            {columns.map((col) => (
              <Chip
                key={col}
                label={col}
                onDelete={() => handleRemoveColumn(col)}
                color="primary"
              />
            ))}
          </Box>
        </Box>

        <Button 
          type="submit" 
          variant="contained" 
          disabled={!tableName || columns.length === 0}
        >
          Check for Duplicates
        </Button>
      </Stack>
    </Box>
  );
}

export default DuplicateCheckForm;
```

**src/components/checks/DuplicateResultsTable.js**:
```javascript
import React from 'react';
import {
  Box,
  Typography,
  Table,
  TableBody,
  TableCell,
  TableContainer,
  TableHead,
  TableRow,
  Paper,
  Alert,
  Chip,
} from '@mui/material';

function DuplicateResultsTable({ results }) {
  if (!results) return null;

  if (!results.success) {
    return (
      <Alert severity="error">
        {results.message}
      </Alert>
    );
  }

  if (results.duplicateGroupCount === 0) {
    return (
      <Alert severity="success">
        No duplicates found!
      </Alert>
    );
  }

  return (
    <Box>
      <Box display="flex" justifyContent="space-between" alignItems="center" mb={2}>
        <Typography variant="h6">
          Duplicate Results
        </Typography>
        <Box>
          <Chip 
            label={`${results.duplicateGroupCount} Groups`} 
            color="warning" 
            sx={{ mr: 1 }}
          />
          <Chip 
            label={`${results.totalDuplicateRows} Total Rows`} 
            color="error" 
          />
        </Box>
      </Box>

      <TableContainer component={Paper}>
        <Table size="small">
          <TableHead>
            <TableRow>
              {Object.keys(results.duplicates[0]?.keyValues || {}).map((key) => (
                <TableCell key={key}><strong>{key}</strong></TableCell>
              ))}
              <TableCell><strong>Count</strong></TableCell>
            </TableRow>
          </TableHead>
          <TableBody>
            {results.duplicates.map((dup, index) => (
              <TableRow key={index}>
                {Object.values(dup.keyValues).map((value, i) => (
                  <TableCell key={i}>{String(value)}</TableCell>
                ))}
                <TableCell>
                  <Chip 
                    label={dup.occurrenceCount} 
                    color="error" 
                    size="small" 
                  />
                </TableCell>
              </TableRow>
            ))}
          </TableBody>
        </Table>
      </TableContainer>
    </Box>
  );
}

export default DuplicateResultsTable;
```

**Update src/pages/Dashboard.js**:
```javascript
import React, { useState } from 'react';
import { Box, Typography, Paper, Tabs, Tab } from '@mui/material';
import DatabaseSelector from '../components/database/DatabaseSelector';
import DuplicateCheckForm from '../components/checks/DuplicateCheckForm';
import DuplicateResultsTable from '../components/checks/DuplicateResultsTable';

function Dashboard() {
  const [selectedProfile, setSelectedProfile] = useState('');
  const [duplicateResults, setDuplicateResults] = useState(null);
  const [activeTab, setActiveTab] = useState(0);

  return (
    <Box>
      <Typography variant="h4" gutterBottom>
        SQL Forensics Toolkit
      </Typography>

      <Paper sx={{ p: 3, mb: 3 }}>
        <DatabaseSelector 
          value={selectedProfile}
          onChange={setSelectedProfile}
        />
      </Paper>

      {selectedProfile && (
        <>
          <Paper sx={{ mb: 2 }}>
            <Tabs 
              value={activeTab} 
              onChange={(e, newValue) => setActiveTab(newValue)}
            >
              <Tab label="Duplicate Detection" />
              <Tab label="Orphaned Records" disabled />
              <Tab label="Stored Procedures" disabled />
            </Tabs>
          </Paper>

          <Paper sx={{ p: 3, mb: 3 }}>
            {activeTab === 0 && (
              <DuplicateCheckForm
                profileId={selectedProfile}
                onResults={setDuplicateResults}
              />
            )}
          </Paper>

          {duplicateResults && (
            <Paper sx={{ p: 3 }}>
              <DuplicateResultsTable results={duplicateResults} />
            </Paper>
          )}
        </>
      )}
    </Box>
  );
}

export default Dashboard;
```

#### ðŸ“ Deliverables:
- Duplicate check form working
- Results display correctly
- Full end-to-end duplicate detection

---

### Days 13-14 - Remaining Check Components (6-8 hours)

#### âœ… TODO List:
- [ ] Create OrphanCheckForm component
- [ ] Create OrphanResultsTable component
- [ ] Create StoredProcedureCheckForm component
- [ ] Create StoredProcedureResults component
- [ ] Integrate all into Dashboard with tabs
- [ ] Test all features end-to-end
- [ ] Commit: "All check components complete"

#### ðŸ“ Files to Create:

**src/components/checks/OrphanCheckForm.js**:
```javascript
// Similar structure to DuplicateCheckForm
// Include fields for:
// - Table Name
// - Foreign Key Column
// - Referenced Table
// - Referenced Column
```

**src/components/checks/OrphanResultsTable.js**:
```javascript
// Display orphaned records in table format
```

**src/components/checks/StoredProcedureCheckForm.js**:
```javascript
// Form with:
// - Text area for expected procedures (one per line)
// - Submit button
```

**src/components/checks/StoredProcedureResults.js**:
```javascript
// Display:
// - Missing procedures (red)
// - Existing procedures (green)
// - All procedures in database
```

#### ðŸ§ª Testing Checklist:
- [ ] Test duplicate check with various tables
- [ ] Test orphan check with FK relationships
- [ ] Test SP check with missing procedures
- [ ] Test error handling for all checks
- [ ] Test UI responsiveness

#### ðŸ“ Deliverables:
- All check types working
- Complete UI for all features
- Tabs navigation functional

---

### Day 15 - UI Polish & Export Features (3-4 hours)

#### âœ… TODO List:
- [ ] Add export to CSV button for results
- [ ] Add print functionality
- [ ] Improve styling and layout
- [ ] Add help text/tooltips
- [ ] Make UI responsive for mobile
- [ ] Add dark mode support (optional)
- [ ] Commit: "UI polish and export features"

#### ðŸ“ Features to Add:

**Export to CSV functionality**:
```javascript
const exportToCSV = (data, filename) => {
  const csv = convertToCSV(data);
  const blob = new Blob([csv], { type: 'text/csv' });
  const url = window.URL.createObjectURL(blob);
  const link = document.createElement('a');
  link.href = url;
  link.download = filename;
  link.click();
};
```

**Add to results components**:
- Export button
- Print button
- Copy to clipboard

#### ðŸ“ Deliverables:
- Export functionality working
- Polished UI
- Responsive design

---

## Phase 3: Integration & Testing
**Duration:** 3-5 days (9-20 hours total)  
**Goal:** End-to-end testing, bug fixes, performance optimization

### Day 16-17 - End-to-End Testing (6-8 hours)

#### âœ… TODO List:
- [ ] Create test scenarios document
- [ ] Test with real production data
- [ ] Test with edge cases (empty tables, huge datasets)
- [ ] Test error scenarios
- [ ] Performance testing
- [ ] Browser compatibility testing
- [ ] Create test report
- [ ] Fix all critical bugs
- [ ] Commit: "Integration testing complete"

#### ðŸ§ª Test Scenarios to Create:

**Test Scenario 1: Duplicate Detection**
- Table with no duplicates â†’ Should return 0
- Table with 1 duplicate group â†’ Should find it
- Table with multiple duplicate groups â†’ Should find all
- Large table (10k+ rows) â†’ Should complete in <5 seconds
- Invalid table name â†’ Should show error
- Invalid column name â†’ Should show error

**Test Scenario 2: Orphan Detection**
- Table with orphans â†’ Should find them
- Table with no orphans â†’ Should return 0
- Table with NULL FKs â†’ Should handle correctly
- Invalid FK relationship â†’ Should show error

**Test Scenario 3: Stored Procedures**
- Missing procedures â†’ Should identify them
- All procedures exist â†’ Should confirm
- Empty database â†’ Should handle gracefully

**Test Scenario 4: Security**
- SQL injection attempts â†’ Should be blocked
- Invalid profile access â†’ Should be denied
- Wrong credentials â†’ Should error appropriately

#### ðŸ“ Create Test Report:
```markdown
# Test Report

## Test Environment
- Backend: .NET 8
- Frontend: React 18
- Database: SQL Server 2019
- Browser: Chrome 120

## Test Results

### Duplicate Detection
- âœ… Finds duplicates correctly
- âœ… Handles no duplicates
- âœ… Performance acceptable (<3s for 10k rows)
- âš ï¸  Large result sets (1000+) slow to render
- âŒ Export CSV fails for >500 rows

### Bug Log
1. CSV export memory issue - FIX: Stream large datasets
2. UI freezes on large results - FIX: Implement pagination
...
```

#### ðŸ“ Deliverables:
- All features tested thoroughly
- Test report created
- Critical bugs fixed
- Performance acceptable

---

### Day 18 - Bug Fixes & Optimization (3-4 hours)

#### âœ… TODO List:
- [ ] Fix all bugs from testing
- [ ] Optimize slow queries
- [ ] Add result pagination for large datasets
- [ ] Improve error messages
- [ ] Add loading indicators where missing
- [ ] Commit: "Bug fixes and optimizations"

#### ðŸ”§ Common Optimizations:

**Add pagination to results**:
```javascript
const [page, setPage] = useState(0);
const [rowsPerPage, setRowsPerPage] = useState(25);

// Display only current page of results
const displayedRows = results.slice(
  page * rowsPerPage,
  page * rowsPerPage + rowsPerPage
);
```

**Optimize large queries**:
```sql
-- Add TOP clause for preview
SELECT TOP 1000 ...
```

**Add caching**:
```csharp
// Cache schema to avoid reloading
private static DatabaseSchema _cachedSchema;
```

#### ðŸ“ Deliverables:
- All bugs fixed
- Performance optimized
- UX improvements implemented

---

## Phase 4: Documentation & Deployment
**Duration:** 4-6 days (12-24 hours total)  
**Goal:** Complete documentation, Docker setup, deployment

### Day 19 - Comprehensive README (3-4 hours)

#### âœ… TODO List:
- [ ] Write comprehensive README.md
- [ ] Add screenshots
- [ ] Create quick start guide
- [ ] Document all features
- [ ] Add troubleshooting section
- [ ] Create API documentation
- [ ] Commit: "Complete documentation"

#### ðŸ“ README.md Structure:

```markdown
# SQL Forensics Toolkit

## Overview
[Description, purpose, key features]

## Screenshots
![Dashboard](docs/screenshots/dashboard.png)
![Duplicate Check](docs/screenshots/duplicates.png)

## Features
- âœ… Duplicate Detection
- âœ… Orphaned Records Detection
- âœ… Stored Procedure Validation
- âœ… Export to CSV
- âœ… Multi-database support

## Tech Stack
- **Backend:** ASP.NET Core 8, Dapper, SQL Server
- **Frontend:** React 18, Material-UI
- **Deployment:** Docker

## Quick Start

### Prerequisites
- .NET 8 SDK
- Node.js 18+
- SQL Server 2016+

### Setup
1. Clone repository
2. Copy `appsettings.TEMPLATE.json` to `appsettings.Development.json`
3. Update connection strings
4. Run backend: `cd backend && dotnet run`
5. Run frontend: `cd frontend && npm start`

## Usage Guide

### Duplicate Detection
[Step-by-step instructions]

### Orphan Detection
[Step-by-step instructions]

## Configuration

### Database Profiles
[Explain profile system]

### Schema Configuration
[Explain schema.json]

## Security

### Credential Storage
[Link to learning document]

### SQL Injection Prevention
[Explain validation approach]

## Troubleshooting

### Connection Fails
[Solutions]

### Slow Performance
[Optimization tips]

## Contributing
[Guidelines]

## License
MIT
```

#### ðŸ“¸ Screenshots to Capture:
- [ ] Dashboard with database selector
- [ ] Duplicate check form
- [ ] Duplicate results
- [ ] Orphan check results
- [ ] SP check results
- [ ] Export functionality

#### ðŸ“ Deliverables:
- Complete README
- All screenshots added
- Clear documentation

---

### Day 20 - Docker Configuration (3-4 hours)

#### âœ… TODO List:
- [ ] Create Dockerfile for backend
- [ ] Create Dockerfile for frontend
- [ ] Create docker-compose.yml
- [ ] Test Docker build
- [ ] Document Docker deployment
- [ ] Commit: "Docker configuration complete"

#### ðŸ“ Files to Create:

**backend/Dockerfile**:
```dockerfile
FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS base
WORKDIR /app
EXPOSE 5000

FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /src
COPY ["Toolkit.Api/Toolkit.Api.csproj", "Toolkit.Api/"]
RUN dotnet restore "Toolkit.Api/Toolkit.Api.csproj"
COPY . .
WORKDIR "/src/Toolkit.Api"
RUN dotnet build "Toolkit.Api.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "Toolkit.Api.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "Toolkit.Api.dll"]
```

**frontend/Dockerfile**:
```dockerfile
FROM node:18-alpine AS build
WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .
RUN npm run build

FROM nginx:alpine
COPY --from=build /app/build /usr/share/nginx/html
COPY nginx.conf /etc/nginx/conf.d/default.conf
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
```

**frontend/nginx.conf**:
```nginx
server {
    listen 80;
    location / {
        root /usr/share/nginx/html;
        index index.html;
        try_files $uri $uri/ /index.html;
    }
}
```

**docker-compose.yml** (root):
```yaml
version: '3.8'

services:
  backend:
    build:
      context: ./backend
      dockerfile: Dockerfile
    ports:
      - "5000:5000"
    environment:
      - ASPNETCORE_ENVIRONMENT=Production
      - ASPNETCORE_URLS=http://+:5000
    volumes:
      - ./backend/appsettings.Production.json:/app/appsettings.Production.json:ro
      - ./backend/Configuration:/app/Configuration:ro

  frontend:
    build:
      context: ./frontend
      dockerfile: Dockerfile
    ports:
      - "3000:80"
    depends_on:
      - backend
    environment:
      - REACT_APP_API_URL=http://localhost:5000
```

#### ðŸ§ª Testing Commands:
```bash
# Build images
docker-compose build

# Run containers
docker-compose up

# Test
curl http://localhost:5000/api/database/profiles
curl http://localhost:3000
```

#### ðŸ“ Deliverables:
- Docker files created
- Docker build successful
- docker-compose working

---

### Day 21 - Case Studies & Examples (3-4 hours)

#### âœ… TODO List:
- [ ] Create 3 case study documents
- [ ] Anonymize real-world examples
- [ ] Add before/after screenshots
- [ ] Create sample datasets
- [ ] Document lessons learned
- [ ] Commit: "Case studies and examples"

#### ðŸ“ Case Studies to Create:

**Case Study 1: Duplicate Orders Investigation**
```markdown
# Case Study: Duplicate Order Detection

## Problem
Production database had duplicate orders causing billing issues.

## Investigation
- Used duplicate detection on Orders table
- Checked columns: [CustomerId, OrderDate, TotalAmount]
- Found 47 duplicate groups affecting 156 orders

## Resolution
- Identified root cause: Race condition in checkout process
- Cleaned up duplicates
- Added unique constraint

## Tools Used
- Duplicate Detection feature
- Export to CSV for analysis

## Outcome
- Prevented $12,000 in duplicate charges
- Fixed underlying bug
```

**Case Study 2: Orphaned Records Cleanup**
**Case Study 3: Missing Stored Procedures Alert**

#### ðŸ“ Deliverables:
- 3 case studies written
- Examples anonymized
- Lessons documented

---

### Day 22 - Final Polish & Deployment (3-4 hours)

#### âœ… TODO List:
- [ ] Code cleanup (remove console.logs, etc.)
- [ ] Final testing
- [ ] Update all documentation
- [ ] Create GitHub release
- [ ] Deploy to Azure/Render (optional)
- [ ] Record demo video
- [ ] Commit: "Final release v1.0"

#### ðŸ“ Cleanup Tasks:
- [ ] Remove all debug code
- [ ] Clean up commented code
- [ ] Format all code consistently
- [ ] Update version numbers
- [ ] Check all dependencies are latest stable

#### ðŸ“ Deployment Options:

**Option 1: Azure (Free Tier)**
- Azure App Service for backend
- Azure Static Web Apps for frontend
- Estimated cost: $0/month

**Option 2: Render (Free Tier)**
- Web Service for backend
- Static Site for frontend
- Estimated cost: $0/month

#### ðŸŽ¥ Demo Video Script:
1. Introduction (30 sec)
2. Database connection (30 sec)
3. Duplicate detection (60 sec)
4. Orphan detection (60 sec)
5. SP check (30 sec)
6. Export feature (30 sec)
7. Conclusion (30 sec)

Total: 4-5 minutes

#### ðŸ“ Deliverables:
- Clean codebase
- All documentation updated
- GitHub release created
- Optional: Live deployment
- Optional: Demo video

---

## Progress Tracking

### Week 1
- [x] Day 1: Repository setup
- [ ] Day 2: Backend setup
- [ ] Day 3: Frontend setup & schema
- [ ] Day 4: Database connection service
- [ ] Day 5: Schema configuration
- [ ] Day 6: Duplicate detection
- [ ] Day 7: Orphan detection

### Week 2
- [ ] Day 8: Stored procedures check
- [ ] Day 9-10: Testing & refinement
- [ ] Day 11: Base frontend components
- [ ] Day 12: Duplicate UI
- [ ] Day 13-14: Remaining UIs

### Week 3
- [ ] Day 15: UI polish
- [ ] Day 16-17: Integration testing
- [ ] Day 18: Bug fixes
- [ ] Day 19: Documentation
- [ ] Day 20: Docker
- [ ] Day 21: Case studies

### Week 4
- [ ] Day 22: Final polish & deploy

---

## Daily Workflow Template

### Start of Day
- [ ] Review yesterday's commits
- [ ] Pull latest changes (if team)
- [ ] Review today's TODO list
- [ ] Start backend server (if needed)
- [ ] Start frontend server (if needed)

### During Work
- [ ] Commit frequently (every feature/fix)
- [ ] Test as you go
- [ ] Document complex logic

### End of Day
- [ ] Commit all changes
- [ ] Push to GitHub
- [ ] Update roadmap checkboxes
- [ ] Plan tomorrow's tasks

---

## Success Metrics

### Code Quality
- [ ] All features working
- [ ] No critical bugs
- [ ] Test coverage >60%
- [ ] Clean code (no linting errors)

### Documentation
- [ ] README complete
- [ ] API documented
- [ ] Code commented
- [ ] Case studies written

### Deployment
- [ ] Docker working
- [ ] Locally deployable
- [ ] Optionally cloud-deployed

---

## Next Steps After Completion

### Portfolio Enhancement
1. Add to resume
2. Create LinkedIn post
3. Prepare for interview questions
4. Practice demo

### Future Enhancements (v2.0)
- [ ] Add schema comparison feature
- [ ] Add data quality checks
- [ ] Implement Azure Key Vault
- [ ] Add scheduled checks
- [ ] Email notifications
- [ ] Multi-database comparison

---

## Notes & Reminders

- **Commit often:** Every feature, every fix
- **Test continuously:** Don't wait for end
- **Document as you go:** Easier than retroactive
- **Ask for help:** Use this roadmap, Claude, or community
- **Celebrate wins:** Mark checkboxes with pride!

---

**Last Updated:** December 2024  
**Estimated Completion:** 4-6 weeks @ 3-4 hours/day  
**Status:** Ready to start!
