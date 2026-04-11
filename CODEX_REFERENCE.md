# Codex Reference

All entries, trigger conditions, and implementation notes.
Update this file whenever a new entry is added.

---

## Trial Count Milestones

| Key | Name | Condition |
|-----|------|-----------|
| FIFTH_ENTRY | The Fifth Entry | 5 total trials |
| TENTH_INSCRIPTION | The Tenth Inscription | 10 total trials |
| PATH_BEGINS | The Path Begins | 25 total trials |
| HABIT_FORMS | The Habit Forms | 50 total trials |
| WEIGHT_OF_REPETITION | The Weight of Repetition | 100 total trials |
| DEEPENING | The Deepening | 500 total trials |
| THOUSAND_INSCRIBED | The Thousand Inscribed | 1000 total trials |
| UNCOUNTED_HOURS | The Uncounted Hours | 2000 total trials |
| ENDLESS_LEDGER | The Endless Ledger | 5000 total trials |

---

## Total Catch Milestones

| Key | Name | Condition | Notes |
|-----|------|-----------|-------|
| FIRST_TALLY | The First Tally | 1,000 cumulative catches across all trials | Sums scores.csv column 3 |
| MYRIAD | The Myriad | 10,000 cumulative catches across all trials | Sums scores.csv column 3 |
| LEGION | The Legion | 100,000 cumulative catches across all trials | Sums scores.csv column 3 |

---

## Rolling Average Milestones

Rolling average of the last 20 trials. Fires once on first qualifying trial; requires 20+ trials logged.

| Key | Name | Condition |
|-----|------|-----------|
| ESTABLISHED_FORM | The Established Form | Rolling average of last 20 trials ≥ 25 |
| HIGH_STANDARD | The High Standard | Rolling average of last 20 trials ≥ 50 |
| IMMACULATE | The Immaculate | Rolling average of last 20 trials ≥ 100 |

---

## Catch Milestones

| Key | Name | Condition |
|-----|------|-----------|
| GATHERING_FORM | The Gathering Form | Score ≥ 10 in a single trial |
| STEADY_HAND | The Steady Hand | Score ≥ 25 in a single trial |
| TURNING_POINT | The Turning Point | Score ≥ 50 in a single trial |
| TRIPLE_CROWN | The Triple Crown | Score ≥ 100 in a single trial |
| GOLDEN_SPAN | The Golden Span | Score ≥ 150 in a single trial |
| SECOND_BREATH | The Second Breath | Score ≥ 200 in a single trial |
| RELENTLESS_ARC | The Relentless Arc | Score ≥ 300 in a single trial |
| COLOSSUS_RISES | The Colossus Rises | Score ≥ 400 in a single trial |
| BREAKING_LIMITS | The Breaking of Limits | Score ≥ 500 in a single trial |
| HIGH_CURRENT | The High Current | Score ≥ 750 in a single trial |
| THOUSANDFOLD | The Thousandfold Trial | Score ≥ 1000 in a single trial |

---

## Behavioral

| Key | Name | Condition | Notes |
|-----|------|-----------|-------|
| STILL_HAND | The Still Hand | Any score logged 3+ times across all trials | Not necessarily consecutive |
| SEPTEM | Septem | Same score logged 7 times in a row | Historical scan of full scores.csv |
| NARROW_PATH | The Narrow Path | Last 20 trials span a range of ≤ 10 catches | Max minus min ≤ 10 |
| CLIMB_WITHOUT_FALL | The Climb Without Fall | 5 consecutive trials each strictly higher than the last | |
| THIRTY | The Thirty | Active Chain ≥ 30 days | Fires while chain is live; no historical backfill |
| ANNUM | The Annum | Active Chain ≥ 365 days | Fires while chain is live; no historical backfill |
| FOUR_WATCHES | The Four Watches | 250+ trials each in dawn (05–08), meridian (11–14), dusk (18–20), and vigil (21–03) | Scans full scores.csv on every trial until discovered |
| ASCENT | The Ascent | 5+ entries in pb_history (5 Apex records set) | |
| ECHO_CHAMBER | The Echo Chamber | Current Apex matched 3+ times since it was set | Resets if Apex broken |
| RESONANCE | The Resonance | Current Apex matched on 5+ separate calendar days | Resets if Apex broken |
| UNBROKEN_REFLECTION | The Unbroken Reflection | Current Apex matched on 3 consecutive calendar days | Resets if Apex broken |
| UNBLEMISHED | The Unblemished | Every one of the last 20 trials scored ≥ 50% of Apex | Requires 20+ trials |
| QUIET_INTERVAL | The Quiet Interval | Narrow Path and Unblemished conditions both met simultaneously | Requires 20+ trials |
| FIRST_NAME | The First Name | First time PB reaches a title above Neophyte (PB ≥ 5) | Historical backfill: scans pb_history.csv for first entry ≥ 5 |
| ASSUMPTION | The Assumption | Score ≥ 80% of PB on the trial immediately after crossing a title threshold | Granted unconditionally upon reaching Immortal (1000 catches) if not yet earned |
| NOTED | The Noted | The Witness has spoken 30 times | Counter starts from witness_count creation; no historical backfill |
| SUSTAINED | The Sustained | Spree of 10+ consecutive worthy trials | |
| INEXORABLE | The Inexorable | Spree of 25+ consecutive worthy trials | |
| UNRELENTING | The Unrelenting | Dominance active for 10 consecutive trials | Tracked via dominance_streak state file; no historical backfill |
| ONSLAUGHT | The Onslaught | Spree (3+ consecutive worthy trials) and Dominance (5 of last 10 ≥ 80% Apex) both active simultaneously | |
| FULL_AUGURY | The Full Augury | Chain, Spree, Dominance, and Echo all active simultaneously | Update condition if new auguries are added |

---

## Cross-System

| Key | Name | Condition | Notes |
|-----|------|-----------|-------|
| CONGREGATION | The Congregation | The Witness speaks while ATTENDANT_3 is discovered | Fires inside witness_speak |
| WITNESSED_ASCENT | The Witnessed Ascent | New Apex set while ATTENDANT_2 is discovered | Historical backfill: scans pb_history for records after ATTENDANT_2 date |
| USURPER | The Usurper | Nemesis shifts to a higher score with strictly more occurrences than the old Nemesis had, and the old Nemesis had appeared 100+ times | Tracked via nemesis_state file; no historical backfill; tie counts do not qualify |

---

## Pattern / Numerological

| Key | Name | Condition | Notes |
|-----|------|-----------|-------|
| CORRESPONDENCE | The Correspondence | Any trial where score == trial number (e.g. trial 47, score 47) | Historical scan of full scores.csv |
| SEQUENCE | The Sequence | Three consecutive trials each exactly 1 higher than the last (e.g. 20, 21, 22) | Historical scan of full scores.csv |
| MIRROR | The Mirror | Score ≥ 11 that reads the same forwards and backwards (11, 22, 33 … 99, 101, 111 …) | Historical scan of full scores.csv |
| DEEP_MIRROR | The Deep Mirror | Palindrome score ≥ 101 | Current trial only; no historical scan needed (user has never scored 101+) |
| SIEVE | The Sieve | All 25 primes under 100 (2, 3, 5 … 97) each logged at least once | Self-backfilling: checks full scores.csv on every trial |
| RATIO | The Ratio | Score contains the substring "314" (e.g. 314, 1314, 3140) | Current trial only |

---

## Meta

| Key | Name | Condition | Notes |
|-----|------|-----------|-------|
| ARCHIVIST | The Archivist | 25 Codex entries discovered | Uses live count of codex.csv entries; no backfill needed (fires on next qualifying trial) |
| OMNIA | Omnia | All other Codex entries discovered | `_omnia_total` in check_codex must be updated when new entries are added |

---

## The Attendants

Sequential — each stage requires the previous to be discovered first.

| Key | Name | Trial Count Required |
|-----|------|----------------------|
| ATTENDANT_1 | The First Shadow | 100 |
| ATTENDANT_2 | The Gathering | 500 |
| ATTENDANT_3 | The Silent Assembly | 1000 |
| ATTENDANT_4 | The Nearing | 2000 |
| ATTENDANT_5 | The Established Rite | 5000 |

Attendants appear silently in The Dispatch (no codex discovery announcement). Each stage fires once; earlier stages are not resurfaced.

---

## State Files

Files that must exist for certain entries to function:

| File | Purpose | Default |
|------|---------|---------|
| `witness_count` | Tracks total Witness appearances for NOTED | 0 |
| `nemesis_state` | Tracks current Nemesis score and count for USURPER | 0,0 |
| `title_state` | Tracks whether a title was crossed last trial for ASSUMPTION | 0 |
| `dominance_streak` | Tracks consecutive trials Dominance has been active for UNRELENTING | 0 |

All created automatically by `init_data` if absent.

---

## Backfill Notes

Entries that scan history on first check and record with the original date if the condition was historically met:

- CORRESPONDENCE — scans all of scores.csv
- SEQUENCE — scans all of scores.csv
- MIRROR — scans all of scores.csv
- SIEVE — scans all of scores.csv on every trial until discovered
- WITNESSED_ASCENT — scans pb_history.csv for records after ATTENDANT_2 date

Entries with no historical backfill (counters started fresh):

- NOTED — witness_count starts at 0 on file creation
- USURPER — nemesis_state starts at 0,0 on file creation
- CONGREGATION, FULL_AUGURY, ONSLAUGHT, ASSUMPTION, UNBLEMISHED, CLIMB_WITHOUT_FALL, NARROW_PATH — state-based; fire on next qualifying trial going forward
