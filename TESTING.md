# Angeelika — Prototype Testing

## Purpose

This document summarizes selected tests performed during the
development of the Angeelika phone scam protection prototype.

The results describe observations from a development environment.
They do not establish production readiness or overall detection accuracy.

## Test observations

| Area | Observation | Status |
|---|---|---|
| Telephony | Ringback continued until the Groundwire endpoint answered during a test call. | Tested |
| Service architecture | Telephony, audio processing and Telegram bot components run as separate services. | Verified on server |
| Risk assessment | A test involving PIN and Smart-ID context was classified as high risk. | Tested |
| False positives | A benign conversational context involving transfers was classified as high risk. | Further testing needed |

## Known limitations

- Risk assessments can produce false positives.
- Some fraudulent conversations may not be detected.
- More test scenarios are needed to evaluate consistency and accuracy.
- The current results are observations from individual tests, not a statistical evaluation.
- Privacy, reliability and deployment requirements need further assessment.

## Security and privacy

This document contains high-level test observations only.
It excludes call recordings, transcripts containing personal data,
credentials, server configuration and internal detection rules.

## Next steps

- Expand the test set with both suspicious and benign conversations.
- Record expected and observed outcomes.
- Investigate false positives and refine the system.
- Repeat tests after changes and compare results.
