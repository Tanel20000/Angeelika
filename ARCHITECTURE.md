# Angeelika — System Architecture

## Overview

Angeelika is an experimental prototype for AI-assisted phone scam
risk assessment. It combines telephony infrastructure, speech
processing and AI-based analysis.

## High-level workflow

    Incoming phone call
            |
            v
    Asterisk telephony server
            |
            v
    Audio processing service
            |
            v
    Speech-to-text
            |
            v
    AI-based risk assessment
            |
            v
    Risk report or notification
            |
            v
    Telegram interface

The Telegram conversational bot runs as a separate service.

## Main components

### Telephony
Asterisk provides telephony infrastructure and handles integration
with SIP-based telephony.

### Audio processing
A dedicated Python service receives audio for processing and
coordinates speech recognition and subsequent analysis.

### Speech recognition
A speech-to-text model converts speech into text for further analysis.

### AI-based analysis
An AI model evaluates conversation text for potential indicators of
telephone fraud. The assessment is experimental and may produce
false positives or miss suspicious conversations.

### Telegram
Telegram supports notifications and a separate conversational bot.

## Engineering work

- Python application development
- Linux server administration and service management
- Integration of external AI APIs
- SIP telephony and Asterisk integration
- Speech processing and AI-based analysis
- Troubleshooting and iterative testing
- Evaluation of detection quality and false positives

## Limitations

This is a prototype under active development. Reliability, detection
quality, privacy requirements and deployment readiness require
continued evaluation.

## Security

This public document describes the architecture at a high level.
It excludes credentials, private configuration, personal data,
call recordings and internal detection rules.
