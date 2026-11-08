# SkillOpt Run Budget and Approval

**Experiment ID:** [ID]  
**Skill:** [name/version/hash]  
**Project:** [name]  
**Date:** [date]  
**Requester/approver:** [role/name]

## Objective
[One measurable skill-quality question]

## Run design
- SkillOpt component: [research engine / Sleep / both]
- Backend/provider: [name and verified capability]
- Task manifest: [path/hash]
- Dataset split/exposure: [development/validation/held-out]
- Product snapshot/commit: [commit]
- Execution environment: [worktree/container/other]

## Operational caps
- Maximum tasks in pilot: [number]
- Maximum candidate versions: [number]
- Maximum optimization iterations: [number]
- Maximum concurrent workers: [number]
- Maximum repository test/build scope: [commands]
- Maximum wall-clock duration: [time]
- Subscription usage risk: [low/medium/high; qualitative estimate]
- API/provider spend risk (if applicable): [none/known cap/unknown]

These caps constrain the experiment design; they do not guarantee a specific subscription quota amount.

## Data and safety
- Data classification: [public/internal/confidential/restricted]
- Session data included: [yes/no]
- Redaction/review: [details]
- External data transmission approved: [yes/no/not applicable]
- Secrets excluded: [yes/no]
- Worktree isolation and cleanup: [details]

## Stop conditions
- [ ] Candidate fails critical benchmark/safety criteria.
- [ ] Task manifest or environment becomes invalid.
- [ ] Usage warning/limit indicates stop or reassessment.
- [ ] Run exceeds approved task/iteration/concurrency cap.
- [ ] Unexpected external charge or data transmission risk appears.

## Approval
- Approved scope: [details]
- Approved by: [name/role]
- Date: [date]
- Decision: [approved/declined/needs changes]

## Results and receipt
[Baseline/candidate results, errors, usage observations, artifact hashes, adoption decision, rollback reference]
