# Agent Relay Local Update Usage

## Good Moments To Trigger

- before commit
- after training
- after evaluation
- before switching to a new chat thread
- before handing work to another agent or teammate
- whenever hooks or repository-local automation are missing

## Example Prompts

- `Use $agent-relay-local-update to refresh STATUS, CHECKPOINT, HANDOFF, and LEADERBOARD before we stop.`
- `Use $agent-relay-local-update to record this run as a failed branch and leave the next step.`
- `Use $agent-relay-local-update to update the trusted best checkpoint after this benchmark run.`
