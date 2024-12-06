# AWS Role Assumer CLI Tool

## Overview
This project is a CLI tool written in Go to streamline AWS role assumption and basic account management tasks. It aims to provide developers and administrators with an intuitive interface for interacting with AWS Organizations, roles, and credentials directly from their local machines.

## Name Suggestions
- **RoleMaster**
- **AWSurfer**
- **AssumeBuddy**
- **CloudPass**
- **KeySwitch**
- **Credible**
- **RoleCaddy**

(Choose your favorite or suggest another!)

---

## Project Goals
### Primary Goal:
Develop an installable CLI tool that enables users to assume roles securely and efficiently.

### Future Goals:
- Add AWS Organizations insights (list accounts, organizational units, etc.).
- Manage and validate access keys, credentials, and policies.
- Support role chaining and temporary credential handling.
- Automate compliance checks for AWS security best practices.

---

## Milestone 1: Basic Role Assumption CLI
### Features
1. **Role Assumption:**
   - Assume an AWS IAM role using the AWS SDK for Go.
   - Parse local credentials and configuration files for profiles.
   - Support MFA (Multi-Factor Authentication) if required by the role.

2. **Basic Commands:**
   - `assume-role`: Assume a specified role and export temporary credentials.
   - `list-roles`: List available roles in the AWS account (future feature).

3. **Environment and Configuration Support:**
   - Use environment variables for region, profile, etc.
   - Handle AWS credentials fallback if no flags are passed.

4. **Error Handling:**
   - Gracefully handle incorrect configurations, invalid roles, or expired sessions.

---

## Project Structure
```plaintext
aws-role-cli/
├── cmd/
│   ├── root.go           # CLI entry point
│   ├── assume_role.go    # Command: assume-role
├── pkg/
│   ├── awsutils/
│   │   ├── assume_role.go   # Core logic for AssumeRole
│   │   ├── config.go        # Parse AWS credentials/config files
│   ├── config/
│   │   ├── profiles.go      # Handle AWS profiles and regions
├── internal/
│   ├── utils.go           # General helper functions
├── README.md              # Documentation
├── go.mod                 # Go module dependencies
```
