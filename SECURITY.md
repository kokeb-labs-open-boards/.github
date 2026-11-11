# Security policy

## Reporting a vulnerability

Report privately, through a GitHub security advisory.

GitHub's private reporting works only on public repositories, and every repository in this organization is public.
If the advisory form is not offered, use the email address in the [Kokeb Labs security
policy](https://github.com/kokeb-labs/.github/blob/main/SECURITY.md) and put the same details in it as you would in
the form below.

To report through a GitHub security advisory:

1. Open the affected repository on GitHub.
2. Go to **Security** > **Advisories** > **Report a vulnerability**.
3. Describe the issue, the affected repository and tag or commit, the MCU and board if relevant, and the steps to
   reproduce.

Do not open a public issue, pull request or discussion for a suspected vulnerability.

If you are not sure which repository is affected, report it against the board or library you were using. We move it if
needed.

## Scope

In scope:

- The designs in `kokeb-labs-open-boards`: for example a board that exposes a debug or programming interface that
  lets an attacker change firmware or read secrets in a way the documentation says it prevents, a circuit that can
  leave an output energised or unsafe on a fault, or firmware examples with a memory-safety flaw.
- The GitHub Actions workflows in every repository, for example a secret exposed to a pull request from a fork, or
  untrusted input reaching a privileged job.

The template and the shared CI (`board-template`, `driver-template`, `ci-tools`) and the chip drivers belong to
Kokeb Labs and Kokeb Labs Drivers; report those under the [Kokeb Labs security
policy](https://github.com/kokeb-labs/.github/blob/main/SECURITY.md). It works the same way.

Out of scope: vulnerabilities in third-party code the examples use (ESP-IDF, FreeRTOS and similar), and in parts
themselves. Report those upstream or to the part vendor, and tell us too if our design makes the problem
exploitable.

## What to expect

- We acknowledge a report within 3 business days.
- Within 10 business days we confirm or reject it and send an assessment: severity (CVSS v4.0 base score), the
  affected releases and a fix plan. After that we update you at least every 14 days, in the advisory or by email,
  until the fix ships.
- The fix ships in a tagged release. The advisory is published once that release is out. Reporters are credited if
  they want to be.

### Fix targets

From confirmation to a tagged release with the fix:

| Severity (CVSS v4.0) | Target |
| --- | --- |
| Critical (9.0 to 10.0) | 7 days |
| High (7.0 to 8.9) | 30 days |
| Medium (4.0 to 6.9) | 90 days |
| Low (0.1 to 3.9) | the next planned release |

Severity is raised by one step, up to critical, when the flaw can change what a motor, actuator or other physical
output does, or can defeat a safety function. Those flaws are also recorded as problem reports under the handbook's
problem resolution process (IEC 62304 clause 9). If we expect to miss a target, we tell you why and give a new date
before the target passes.

### Coordinated disclosure

- We ask you to keep the report private until the fix is released, or for 90 days after your report, whichever
  comes first. We may agree a longer date with you when a fix needs hardware or a field update. A shorter date is
  also possible if the flaw is already public or being exploited.
- If a flaw is being exploited, we publish an advisory with mitigations before the fix when that protects users
  better than waiting.
- We do not take legal action against good-faith research that follows this policy, stays within the scope above,
  and avoids harm to people, data and other people's devices.

### CVE identifiers

Every confirmed vulnerability in a released version gets a CVE. We request it through the repository's GitHub
security advisory, and GitHub is the CVE Numbering Authority. The CVE is published with the advisory. A flaw
that never reached a release, or only affects a private repository with no outside users, is fixed and recorded in
the changelog without a CVE.

Each release carries `SHA256SUMS`, and an SPDX SBOM for any software in it. With them, users can check whether they
are affected and verify the fixed release they download.

## Supported versions

Only the latest release of each repository receives security fixes. Projects that pin an older release should move
to the fixed one.
