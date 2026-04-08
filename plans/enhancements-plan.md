# Bicep 101 Tutorial — Enhancements Plan

## Strong Fits for the Curriculum

### 1. Loops (`for` expressions)
Deploy N resources from an array or range. Currently not covered at all — this is a fundamental Bicep concept.
- **PowerShell bridge:** `foreach` / `ForEach-Object`
- **Suggested placement:** Between current Modules 2 (Params & Variables) and 3 (Modules & Outputs)
- **Exercise idea:** Create multiple storage accounts from an array of names/configs

### 2. User-Defined Types (`type` keyword)
Define reusable schemas for params, variables, and outputs. Brings compile-time validation.
- **PowerShell bridge:** `[PSCustomObject]` type definitions, class definitions
- **Suggested placement:** Alongside or right after loops
- **Exercise idea:** Define a `StorageConfig` type with constrained properties, use it as a parameter

### 3. User-Defined Functions
Reusable expressions within Bicep files for common logic.
- **PowerShell bridge:** `function Get-Something { ... }`
- **Suggested placement:** Pairs well with the existing modules concept (Module 3)
- **Exercise idea:** Create a naming convention function used across multiple resources

### 4. Deployment (Module 1.5)
The `learn-bicep` skill already defines a Module 1.5 for deploying to Azure, but it hasn't been exercised in the tutorial flow. Actually seeing a resource appear in Azure is a powerful learning moment.
- **Suggested placement:** After Module 1 (already designed for this spot)
- **Covers:** `az deployment group create` or `New-AzResourceGroupDeployment`, resource verification, cleanup

## Intermediate / Stretch Topics

### 5. Bicep Test Framework (experimental)
Write `assert` statements to validate templates before deploying.
- **PowerShell bridge:** Pester tests for infrastructure
- **Suggested placement:** Bonus module at the end — forward-looking, shows where Bicep is headed
- **Exercise idea:** Add assertions to validate naming conventions and SKU constraints

### 6. `@secure()` Decorator
Handling secrets (passwords, connection strings) safely in templates.
- **Practical importance:** High — every real-world deployment needs this
- **Exercise idea:** Add a secure param for a storage account access key or Key Vault secret

### 7. `@nullIfNotFound`
Graceful handling of optional or dependent resources. Introduced in Bicep v0.41.2 (Feb 2024) but **still experimental** as of April 2026 — requires `existingNullIfNotFound` flag in `bicepconfig.json`. No announced GA timeline.
- **Status:** ⏳ Watch this space — not recommended for a 101 tutorial until it reaches GA
- **Exercise idea:** Conditionally reference an existing Log Analytics workspace

### 8. Deployer Function (`deployer()`)
Discover who's running the deployment for tagging and RBAC automation.
- **Quick win** — small concept, practical for real-world tagging patterns
- **Exercise idea:** Auto-tag resources with the deployer's identity

## Suggested Revised Module Order

1. Hello Storage Account (existing)
2. Deploy It (existing Module 1.5, not yet exercised)
3. Parameters, Variables & Conditions (existing)
4. **Loops** (new)
5. **User-Defined Types** (new)
6. Modules & Outputs (existing)
7. ARM → Bicep Migration (existing)
8. **Bicep Test Framework** (new, bonus)
