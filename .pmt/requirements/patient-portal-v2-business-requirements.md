# Business Requirements Document
**Project**: Patient Portal v2
**Owner**: Product Team
**Status**: In Review
**Last updated**: Sprint 2

## Executive Summary
Redesign the patient-facing portal to reduce support call volume by 40%, increase self-service claim status checks by 60%, and launch HIPAA-compliant telehealth in Q3.

## Goals & Success Metrics
| Goal | Metric | Target |
|------|--------|--------|
| Self-service claims | % of patients who check status without calling | 60% ↑ |
| Support deflection | Monthly inbound calls re: claims | 40% ↓ |
| Telehealth adoption | Video visits booked in first 90 days | 5,000 |
| Satisfaction | NPS score | ≥ 45 |
| Onboarding | Time to first successful login | < 3 min |

## User Stories

### Authentication
- As a patient, I can log in using my insurance member ID so I don't need to create a separate password.
- As a patient, I can use Face ID / Touch ID on my phone so login is frictionless.

### Claims
- As a patient, I can see all my claims for the current year at a glance.
- As a patient, I can filter claims by date, provider, and status.
- As a patient, I can download my Explanation of Benefits (EOB) as a PDF.
- As a patient, I can submit a claim appeal directly in the portal.

### Benefits
- As a patient, I can see my current deductible progress and out-of-pocket maximum.
- As a patient, I can look up whether a specific provider or service is in-network.

### Telehealth
- As a patient, I can search for in-network providers by specialty and availability.
- As a patient, I can book a video consultation and receive a calendar invite.
- As a patient, I can message my care team securely within the portal.

## Compliance Requirements
- All PHI must be encrypted at rest (AES-256) and in transit (TLS 1.3).
- Every PHI access must be logged with user ID, timestamp, and action.
- Telehealth sessions must comply with 45 CFR §164 (HIPAA Security Rule).
- Right-of-access data export must be available within 30 days of request.