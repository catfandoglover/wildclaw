# Wildclaw Heartbeat

Proactive scheduled check-ins that run automatically. All times are Central Time (America/Chicago).

## Daily

### Morning Brief — 7:00 AM CT
- Weather in Evanston
- Today's calendar
- Top 3 priorities
- Any follow-ups needed from yesterday

### Evening Wrap — 8:00 PM CT
- Day review
- Workout check
- Family time reminder
- Tomorrow preview

## Weekly

### Sunday Strategy — 7:00 PM CT (Sundays)
- Week in review: wins and dropped balls
- Health check: workouts, sleep trends
- Goals progress
- Week ahead prep
- One thought-provoking question

## Monthly

### Deep Dive — 9:00 AM CT (1st of each month)
- Month in review
- Health trends
- Financial snapshot (when tracking is set up)
- Charitable giving vs goals
- Goal realignment
- Big question for the month

## Task IDs

| Task | ID | Cron |
|------|----|------|
| Morning Brief | `heartbeat-morning-brief` | `0 7 * * *` |
| Evening Wrap | `heartbeat-evening-wrap` | `0 20 * * *` |
| Weekly Strategy | `heartbeat-weekly-strategy` | `0 19 * * 0` |
| Monthly Deep Dive | `heartbeat-monthly-deep-dive` | `0 9 1 * *` |

## Notes

- All tasks run in `main` group context (admin privileges)
- Output is sent to the main channel (currently Wildclaw WhatsApp group)
- When Telegram is set up as the private executive channel, update `chat_jid` for all tasks
- Tasks use `isolated` context mode (fresh container each run)
- To pause a task: `UPDATE scheduled_tasks SET status = 'paused' WHERE id = 'heartbeat-xxx';`
- To resume: `UPDATE scheduled_tasks SET status = 'active' WHERE id = 'heartbeat-xxx';`
