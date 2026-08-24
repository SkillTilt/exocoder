# ESCALATION_LOG.md — Exocoder work diary
<!-- One entry per real task. "escalated: yes" = the local AI couldn't finish it
     acceptably; a big model or I had to. Classes: code-write | code-debug |
     code-review | research/summarize | writing | data-analysis | ops/infra | other -->

## Before ticket 1 — first-ever run, 2026-08-18 (smoke test, not a ticket)
Toy task (hello.py). Agent claimed success; actually a silent failure — its file-writing
command was broken, the script never ran, and it called empty output "success."
Caught by me checking by hand. This is the exact failure the verification gate must catch.

## Ticket 1 — 2026-08-18
class: code-write
task: write a pytest that pins compute_eval_config_hash to its exact output
model: olmo-3-7b-instruct-4bit (text mode)
escalated: yes
outcome: Agent computed the CORRECT hash value through 7 rounds of reading its own
errors (impressive), but overwrote an existing test file (git restored it), produced
a broken test file, never ran pytest, and claimed success anyway. I wrote the 5-line
test myself around the agent's value. Test passes; now part of the suite (61 tests).
sensitive: false
