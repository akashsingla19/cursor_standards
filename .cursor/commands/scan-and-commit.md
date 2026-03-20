# Scan secrets and commit

Scan all staged changes for secrets before committing.

## Steps

1. Run `git diff --cached --diff-filter=ACMR` to get staged changes
2. If nothing staged, say "Nothing staged" and stop
3. Scan EVERY added line (lines with +) using policy in `.cursor/rules/secret-scanner.mdc`
4. Output verdict in the exact format from the rule

5. If REJECTED:
   - Show findings
   - Say: "❌ Commit blocked. Fix issues, re-stage, and run this command again."
   - Do NOT create .commit-approved
   - Do NOT run git commit

6. If APPROVED:
   - Create the approval token: `echo approved > .commit-approved`
   - Run: `git commit -m "$input"`
   - The pre-commit hook will see .commit-approved and allow the commit
   - The hook auto-deletes .commit-approved after use
