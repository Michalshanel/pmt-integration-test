# Release & Deployment Workflow

## Branch Strategy
```
main          → production (auto-deploy via Vercel)
staging       → staging environment (auto-deploy)
feature/*     → PR → staging → main
hotfix/*      → PR → main (expedited review)
```

## PR Checklist
Before merging any PR, the author must confirm:
- [ ] Tests pass (unit + E2E)
- [ ] No TypeScript errors (`tsc --noEmit`)
- [ ] Accessibility: no new axe violations
- [ ] PHI: new fields reviewed by compliance
- [ ] Migrations: `prisma migrate` included if schema changed
- [ ] Feature flag: new features gated if not ready for GA

## Deployment Steps
1. **Merge to staging** → Vercel deploys preview URL automatically
2. **QA sign-off** → Priya Nair runs smoke tests on staging
3. **Compliance review** → Required for any PHI-touching change
4. **Merge to main** → Production deploy triggers
5. **Monitor** → Watch error rates in Sentry for 30 minutes post-deploy

## Rollback Procedure
If error rate spikes >1% within 30 minutes of deploy:
1. Revert PR on GitHub (creates a new commit, does not force-push)
2. Vercel auto-deploys the previous build
3. Post incident in #portal-incidents Slack channel
4. Open a post-mortem task in PMT within 24 hours