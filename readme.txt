AWS Role Assumer CLI Tool
Overview
This project is a CLI tool written in Go to streamline AWS role assumption and basic account management tasks. It aims to provide developers and administrators with an intuitive interface for interacting with AWS Organizations, roles, and credentials directly from their local machines.

Name Suggestions
RoleMaster
AWSurfer
AssumeBuddy
CloudPass
KeySwitch
Credible
RoleCaddy
Project Goals
Primary Goal: Develop an installable CLI tool that enables users to assume roles securely and efficiently.

Future Goals:

Add AWS Organizations insights (list accounts, organizational units, etc.).
Manage and validate access keys, credentials, and policies.
Support role chaining and temporary credential handling.
Automate compliance checks for AWS security best practices.
Milestone 1: Basic Role Assumption CLI
Features:
Role Assumption:

Assume an AWS IAM role using the AWS SDK for Go.
Parse local credentials and configuration files for profiles.
Support MFA (Multi-Factor Authentication) if required by the role.
Basic Commands:

assume-role: Assume a specified role and export temporary credentials.
list-roles: List available roles in the AWS account (future feature).
Environment and Configuration Support:

Use environment variables for region, profile, etc.
Handle AWS credentials fallback if no flags are passed.
Error Handling:

Gracefully handle incorrect configurations, invalid roles, or expired sessions.
Project Structure
aws-role-cli/ ├── cmd/ │ ├── root.go # CLI entry point │ ├── assume_role.go # Command: assume-role ├── pkg/ │ ├── awsutils/ │ │ ├── assume_role.go # Core logic for AssumeRole │ │ ├── config.go # Parse AWS credentials/config files │ ├── config/ │ │ ├── profiles.go # Handle AWS profiles and regions ├── internal/ │ ├── utils.go # General helper functions ├── README.md # Documentation ├── go.mod # Go module dependencies

Technical Stack
Language: Go
CLI Framework: Cobra (github.com/spf13/cobra)
AWS SDK: AWS SDK for Go v2 (github.com/aws/aws-sdk-go-v2)
Packaging and Distribution: GoReleaser (github.com/goreleaser/goreleaser)
Implementation Steps
Setup Project:

Initialize a Go module: go mod init github.com/yourusername/aws-role-cli.
Set up a basic Cobra CLI application.
Implement Role Assumption:

Add a function in pkg/awsutils/assume_role.go to call the AWS sts:AssumeRole API.
Parse ~/.aws/credentials and ~/.aws/config to identify available roles and profiles.
Export temporary credentials to the environment for subsequent AWS CLI/API calls.
Build CLI Commands:

Create assume-role and list-roles commands using Cobra.
Provide helpful flags for specifying profiles, regions, and MFA tokens.
Package and Release:

Set up GoReleaser for building binaries.
Provide precompiled binaries for macOS, Linux, and Windows.
Add installation instructions in the README.
Example Usage
Installation
Using Homebrew:

bash
Copy code
brew install yourusername/aws-role-cli
Using Precompiled Binary:

ruby
Copy code
curl -L -o aws-role-cli https://github.com/yourusername/aws-role-cli/releases/latest/download/aws-role-cli
chmod +x aws-role-cli
mv aws-role-cli /usr/local/bin/
Commands
Assume a Role:

scss
Copy code
aws-role-cli assume-role --role-name my-role --profile default --mfa-token 123456
List Available Roles (Future):

Copy code
aws-role-cli list-roles
Future Enhancements
Integrate AWS Organizations API to list accounts and OUs.
Validate policies and trust relationships for roles.
Add an interactive mode for easier role switching.
Support for custom plugins or extensions.
Getting Started
Clone the repository:

bash
Copy code
git clone https://github.com/yourusername/aws-role-cli.git
cd aws-role-cli
Install dependencies:

go
Copy code
go mod tidy
Build the CLI:

go
Copy code
go build -o aws-role-cli .
Test it locally:

bash
Copy code
./aws-role-cli assume-role --role-name my-role
Contributors
Your Name (https://github.com/yourusername)

License
Apache
