# GitHub Copilot CLI (Public Preview)

The power of GitHub Copilot, now in your terminal.

GitHub Copilot CLI brings AI-powered coding assistance directly to your command line, enabling you to build, debug, and understand code through natural language conversations. Powered by the same agentic harness as GitHub's Copilot coding agent, it provides intelligent assistance while staying deeply integrated with your GitHub workflow.

See [our official documentation](https://docs.github.com/copilot/concepts/agents/about-copilot-cli) for more information.

![Image of the splash screen for the Copilot CLI](https://github.com/user-attachments/assets/f40aa23d-09dd-499e-9457-1d57d3368887)


## 🚀 Introduction and Overview

We're bringing the power of GitHub Copilot coding agent directly to your terminal. With GitHub Copilot CLI, you can work locally and synchronously with an AI agent that understands your code and GitHub context.

- **Terminal-native development:** Work with Copilot coding agent directly in your command line — no context switching required.
- **GitHub integration out of the box:** Access your repositories, issues, and pull requests using natural language, all authenticated with your existing GitHub account.
- **Agentic capabilities:** Build, edit, debug, and refactor code with an AI collaborator that can plan and execute complex tasks.
- **MCP-powered extensibility:** Take advantage of the fact that the coding agent ships with GitHub's MCP server by default and supports custom MCP servers to extend capabilities.
- **Full control:** Preview every action before execution — nothing happens without your explicit approval.

We're still early in our journey, but with your feedback, we're rapidly iterating to make the GitHub Copilot CLI the best possible companion in your terminal.

## 📦 Getting Started

### Supported Platforms

- **Linux**
- **macOS**
- **Windows**

### Prerequisites

- (On Windows) **PowerShell** v6 or higher
- An **active Copilot subscription**. See [Copilot plans](https://github.com/features/copilot/plans?ref_cta=Copilot+plans+signup&ref_loc=install-copilot-cli&ref_page=docs).

If you have access to GitHub Copilot via your organization or enterprise, you cannot use GitHub Copilot CLI if your organization owner or enterprise administrator has disabled it in the organization or enterprise settings. See [Managing policies and features for GitHub Copilot in your organization](http://docs.github.com/copilot/managing-copilot/managing-github-copilot-in-your-organization/managing-github-copilot-features-in-your-organization/managing-policies-for-copilot-in-your-organization) for more information.

### Installation

Install with [WinGet](https://github.com/microsoft/winget-cli) (Windows):

```bash
winget install GitHub.Copilot
```

```bash
winget install GitHub.Copilot.Prerelease
```

Install with [Homebrew](https://formulae.brew.sh/cask/copilot-cli) (macOS and Linux):

```bash
brew install copilot-cli
```

```bash
brew install copilot-cli@prerelease
```

Install with [npm](https://www.npmjs.com/package/@github/copilot) (macOS, Linux, and Windows):

```bash
npm install -g @github/copilot
```

```bash
npm install -g @github/copilot@prerelease
```

Install with the install script (macOS and Linux):

```bash
curl -fsSL https://gh.io/copilot-install | bash
```

Or

```bash
wget -qO- https://gh.io/copilot-install | bash
```

Use `| sudo bash` to run as root and install to `/usr/local/bin`.

Set `PREFIX` to install to `$PREFIX/bin/` directory. Defaults to `/usr/local`
when run as root or `$HOME/.local` when run as a non-root user.

Set `VERSION` to install a specific version. Defaults to the latest version.

For example, to install version `v0.0.369` to a custom directory:

```bash
curl -fsSL https://gh.io/copilot-install | VERSION="v0.0.369" PREFIX="$HOME/custom" bash
```

### Launching the CLI

```bash
copilot
```

On first launch, you'll be greeted with our adorable animated banner! If you'd like to see this banner again, launch `copilot` with the `--banner` flag.

If you're not currently logged in to GitHub, you'll be prompted to use the `/login` slash command. Enter this command and follow the on-screen instructions to authenticate.

#### Authenticate with a Personal Access Token (PAT)

You can also authenticate using a fine-grained PAT with the "Copilot Requests" permission enabled.

1. Visit https://github.com/settings/personal-access-tokens/new
2. Under "Permissions," click "add permissions" and select "Copilot Requests"
3. Generate your token
4. Add the token to your environment via the environment variable `GH_TOKEN` or `GITHUB_TOKEN` (in order of precedence)

### Using the CLI

Launch `copilot` in a folder that contains code you want to work with.

By default, `copilot` utilizes Claude Sonnet 4.5. Run the `/model` slash command to choose from other available models, including Claude Sonnet 4 and GPT-5.

Each time you submit a prompt to GitHub Copilot CLI, your monthly quota of premium requests is reduced by one. For information about premium requests, see [About premium requests](https://docs.github.com/copilot/managing-copilot/monitoring-usage-and-entitlements/about-premium-requests).

For more information about how to use the GitHub Copilot CLI, see [our official documentation](https://docs.github.com/copilot/concepts/agents/about-copilot-cli).

## 🔬 Temporal Experiments (Simulation)

The GitHub Copilot CLI repository includes a lightweight helper script for running temporal experiment simulations. This tool provides a deterministic, reproducible CLI interface for exploring time-symmetric computational models in a classical context.

### What is it?

The `temporal.sh` script is a research-oriented tool that allows you to run temporal experiment stubs with configurable parameters. It generates structured output based on a seed value, making experiments reproducible and suitable for educational and research purposes.

### Installation and Location

The `temporal.sh` helper script is available in the GitHub Copilot CLI repository:

**For users who installed via package managers** (winget, brew, npm):
```bash
# Download the script from the repository (after PR is merged to main)
curl -fsSL https://raw.githubusercontent.com/github/copilot-cli/main/temporal.sh -o temporal.sh
chmod +x temporal.sh
```

**For users who cloned the repository**:
The script is located in the repository root directory and can be run directly.

### Usage

```bash
./temporal.sh [OPTIONS]
```

**Available Options:**
- `--seed SEED` - Set the random seed for deterministic results (integer)
- `--iterations N` - Number of iterations to run (default: 100)
- `--constraint CONST` - Apply a constraint to the simulation (string)
- `--verbose` - Enable verbose output with progress indicators
- `--version` - Show version information
- `--help` - Show help message

**Examples:**

Basic run with auto-generated seed:
```bash
./temporal.sh
```

Deterministic run with specific seed:
```bash
./temporal.sh --seed 42 --iterations 500
```

Run with constraint and verbose output:
```bash
./temporal.sh --seed 12345 --iterations 1000 --constraint "bounded" --verbose
```

### Expected Output

The script produces structured output including:
- Configuration summary (seed, iterations, constraints)
- Simulation progress (in verbose mode)
- Results summary with success rate and convergence scores
- Time-symmetric properties (forward consistency and backward correlation)

Example output:
```
======================================================================
  Temporal Experiment (Simulation) - Classical Stub
======================================================================

Configuration:
  Seed:        42
  Iterations:  100
  Constraint:  none

Running simulation...

======================================================================
  Simulation Results
======================================================================

Summary:
  Total iterations:     100
  Successful:           63
  Failed:               37
  Success rate:         63.00%
  Convergence score:    63

Time-symmetric properties:
  Forward consistency:  0.500
  Backward correlation: 0.900

======================================================================
```

### Reproducibility

The script is fully deterministic when using the same seed value. This means:
- Same seed → Same results every time
- Perfect for reproducible research and experiments
- Suitable for educational demonstrations and testing

### Important: Ethics and Safety Disclaimer

**⚠️ CLASSICAL SIMULATION ONLY**

This tool is a **classical computational simulation** and does NOT:
- Perform actual temporal manipulation
- Achieve physical retrocausality
- Interact with quantum systems
- Modify spacetime or physical reality

The temporal experiment helper is designed exclusively for:
- Research and educational purposes
- Exploring time-symmetric computational models theoretically
- Demonstrating deterministic simulation principles
- Testing classical algorithms in a controlled environment

All results are purely computational and based on deterministic pseudo-random number generation. The script provides a safe, reproducible way to experiment with time-symmetric concepts without any physical implications.

## 📢 Feedback and Participation

We're excited to have you join us early in the Copilot CLI journey.

This is an early-stage preview, and we're building quickly. Expect frequent updates--please keep your client up to date for the latest features and fixes!

Your insights are invaluable! Open issue in this repo, join Discussions, and run `/feedback` from the CLI to submit a confidential feedback survey!
