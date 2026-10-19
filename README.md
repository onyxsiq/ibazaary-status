# iBazaary cloud status

This repository records automated availability checks for the cloud service used
to activate and administer iBazaary POS. It contains no application source,
customer information or credentials. Shop sales and stock remain local in the
cashier application.

[Latest status and 30-day history](status/supabase.json) ·
[Check runs](https://github.com/onyxsiq/ibazaary-status/actions/workflows/cloud-health.yml)

The monitor runs at 05:17, 13:17 and 21:17 Baghdad time. Each check validates the
database connection and the presence of essential licensing tables. It does not
send SMS messages or read or change customer records. A failed check is recorded
as `healthy: false` and fails the GitHub Actions run.

Always inspect `lastCheckedAt`. A previous successful check does not prove the
service is available now, and a stale timestamp can mean the monitor stopped.
Checks can be delayed by GitHub, and Free hosting does not guarantee availability.

The status document keeps at most 30 days (and 180 samples) of recent checks.
Older status documents remain in Git history. Recorded timestamps and success
booleans are the only monitoring results published here. Real status updates
also keep this public repository active between application releases.

The workflow runs only on its schedule or an owner's manual dispatch. It uses
standard public GitHub Actions runners and needs no paid plan. The dedicated
monitor credential only runs a fixed health check. The workflow's GitHub token
can write status records in this repository and has no access to private source
or installer releases.
