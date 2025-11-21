# Contract Monthly Claims System (CMCS)

**Developed by:** Sivikelwe Nxumalo  
**Student ID:** ST10448374  
**Course:** Programming 2B  

## 1. System Overview
The Contract Monthly Claims System (CMCS) is a web-based ASP.NET Core MVC application designed to manage part-time lecturer monthly claims for universities or training institutions. The system automates claim submissions, approvals, HR processing, and secure document uploads. It was developed using .NET 9 MVC, SQL Server, Entity Framework Core, and ASP.NET Identity.

## 2. System Features
Key functional modules include:
- **Lecturer claim submissions** with auto-calculated totals (Hours × Hourly Rate).
- **File uploads** (PDF, DOCX, etc.) stored securely in the server’s `wwwroot/uploads` directory.
- **Program Coordinator approval workflow.**
- **Academic Manager review and approval.**
- **HR module** for payment processing and invoice/report generation.
- **User authentication & role-based authorization** via ASP.NET Identity.
- **Validation, error handling,** and secure database access.

## 3. Fixes Applied Based on Feedback
- Resolved Entity Framework errors related to `DbContext` inheritance.
- Replaced `IdentityDbContext` constructor error with the correct base constructor.
- Fixed `OnModelCreating` overrides by using proper EF Core signatures.
- Ensured `ClaimManagementContext` inherits from `IdentityDbContext<ApplicationUser>`.
- Corrected missing Database property errors by adding EF references.
- Added nullable collections or initialized them to fix constructor exit warnings.
- Fixed incompatible package versions (removed Identity 10.0, installed Identity 8.0).
- Addressed async warnings and null reference checks.
- Resolved namespace typos (DbContext spelled incorrectly, removed `DataContext` reference).
- After fixes, the system now runs without crashing after launch.

## 4. Technologies Used
- **ASP.NET Core MVC** (.NET 9)
- **Entity Framework Core** (SQL Server provider)
- **ASP.NET Identity** for authentication
- **Bootstrap 5** for UI styling
- **jQuery** for client-side enhancements
- **xUnit + Moq** for automated testing
- **SQL Server Management Studio (SSMS)**

## 5. Database Structure Summary
The SQL database named `CMCS` contains the following tables:
- **Users** – Optional simple user lookup table.
- **Lecturers** – Lecturer profiles, hourly rate, and Identity link.
- **Claims** – Monthly claim submissions with computed `TotalAmount`.
- **ClaimApprovals** – Coordinator/Manager approval history.
- **HRProcessing** – HR payment processing actions.
- **ClaimDocuments** – Uploaded file metadata.

## 6. Project Structure ClaimManagementSystem/
├─ src/
│ ├─ wwwroot/
│ │ ├─ bootstrap.css
│ │ ├─ bootstrap-grid.css
│ │ ├─ bootstrapReboot.css
│ │ ├─ bootstrapUtilities.css
│ │ ├─ site.css
│ │ ├─ js/
│ │ │ ├─ bootstrap.js
│ │ │ └─ site.js
│ ├─ ClaimManagementSystem/
│ │ ├─ ClaimManagementSystem.csproj
│ │ ├─ Program.cs
│ │ ├─ appsettings.json
│ │ ├─ /DataContext/
│ │ │ ├─ ClaimManagementContext.cs
│ │ │ └─ DbInitializer.cs
│ │ ├─ /Models/
│ │ │ ├─ Lecturer.cs
│ │ │ ├─ Claim.cs
│ │ │ ├─ ClaimApproval.cs
│ │ │ ├─ HRProcessing.cs
│ │ │ └─ ClaimDocument.cs
│ │ ├─ /ViewModels/
│ │ │ ├─ LoginViewModel.cs
│ │ │ └─ RegisterViewModel.cs
│ │ ├─ /Services/
│ │ │ ├─ FileService.cs
│ │ │ └─ RoleSeeder.cs
│ │ ├─ /Controllers/
│ │ │ ├─ HomeController.cs
│ │ │ ├─ AccountController.cs
│ │ │ ├─ ClaimsController.cs
│ │ │ ├─ AdminController.cs
│ │ │ └─ HRController.cs
│ │ ├─ /Views/
│ │ │ ├─ /Shared/_Layout.cshtml
│ │ │ ├─ /Home/Index.cshtml
│ │ │ ├─ /Claims/Create.cshtml
│ │ │ ├─ /Claims/MyClaims.cshtml
│ │ │ ├─ /Admin/Pending.cshtml
│ │ │ └─ /HR/Approved.cshtml

## 7. Presentation Guide (5 Minutes)
Recommended structure for your PowerPoint:
- **Slide 1:** System Title + Your Name
- **Slide 2:** Problem Statement (manual claim processing issues)
- **Slide 3:** System Architecture Diagram
- **Slide 4:** Key Features (auto-calculation, approvals, HR module)
- **Slide 5:** Database Schema Diagram
- **Slide 6:** Code Snippets (DbContext, Claim model, File upload code)
- **Slide 7:** Demo Screenshots
- **Slide 8:** Benefits and Final Notes

## 8. Recommended Code Snippets for Presentation
- `DbContext` configuration (ClaimManagementContext).
- Claim model showing computed `TotalAmount`.
- File upload action in controller.
- Identity role seeding.
- Simple EF query in a controller (e.g., list claims).

## 9. Final Notes
The system is now stable, tested, and runs correctly after resolving all startup crashes. This report summarizes the technical and functional aspects and can be used as supporting documentation for academic or project submission.
