# Angeelika — Prototype Test Results

## Summary

Angeelika is an experimental phone-scam protection prototype.
Initial tests have demonstrated key call-handling functions and
AI-assisted risk assessment. Detection accuracy has not yet been
established through systematic testing.

## Observed results

| Test area | Observed result | Status |
|---|---|---|
| Call handling | Ringback continued until the Groundwire endpoint answered during a test call. | Tested |
| Suspicious conversation | A test involving PIN and Smart-ID context received a HIGH risk assessment. | Tested |
| High-risk response | Both the caller and Groundwire call channels were disconnected. Channel removal was verified through the telephony interface. | Technically verified |
| False positive | A conversation considered benign, involving transfers, received a HIGH risk assessment. | Issue identified |
| Service operation | Telephony, audio processing and Telegram bot components were running as separate services during server checks. | Verified on server |

## What these results show

- Core call-handling behaviour has been tested in a development environment.
- The prototype is designed to terminate call channels and send a risk report to Telegram when a high-risk result is reached.
- The risk assessment can incorrectly classify benign conversation as high risk.
- The current observations are individual test results, not a measurement of overall detection accuracy.

## Known limitations

- False positives can interrupt legitimate conversations.
- Suspicious conversations may receive a low-risk assessment or go undetected.
- A small number of tests cannot establish reliability or detection accuracy.
- The prototype has not been demonstrated to be production-ready.
- Privacy, reliability and deployment requirements need further evaluation.

## Next steps

1. Test a wider range of suspicious and benign conversations.
2. Record the expected result and the actual result for each test.
3. Investigate false positives and possible missed detections.
4. Repeat the same tests after changes to check whether behaviour improves.
5. Evaluate results across a larger test set before making claims about accuracy.

## Security and privacy

This document contains test observations only.
It excludes phone numbers, personal data, call recordings,
credentials, private server configuration and internal detection rules.
