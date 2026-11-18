# Week 1 Problem Card: ELIA (Edge Language & Intent Agent)

## 1. Problem Statement
Conventional voice assistants and real-time translation tools rely on continuous cloud connectivity. In IoT environments—such as smart homes, eldercare, or industrial facilities—streaming raw audio to external servers introduces **network latency**, **single-point-of-failure risks** when internet drops, and **severe privacy vulnerabilities**. Furthermore, basic IoT sensors lack the contextual intelligence to distinguish between normal conversation, complex user questions, and urgent emergency distress calls.

## 2. Proposed Edge IoT Solution
**ELIA** moves both speech recognition and natural language reasoning directly onto the local edge node:
- **Local Ingestion & STT:** A Python stream replayer feeds audio into an offline Speech-to-Text engine (`Faster-Whisper`) for multilingual transcription and translation.
- **On-Device Edge Intelligence:** A lightweight local Small Language Model (`Llama 3.2 3B` via `Ollama`) evaluates intent in real time—answering user queries offline like a local assistant while detecting distress signals.
- **IoT MQTT Dispatch:** Decisions are published over a local **Mosquitto MQTT** broker to trigger immediate downstream actions (high-priority emergency alerts vs. local Text-to-Speech responses) while filtering out background noise.

## 3. Target Users & Use Cases
- **Multilingual Households & Eldercare:** Instant offline translation, daily Q&A assistance, and hands-free emergency distress alerting without cloud surveillance.
- **Offline / Low-Connectivity IoT Environments:** Industrial or remote edge nodes requiring voice-activated status queries and safety monitoring.

## 4. Technical Constraints & Success Metrics
- **Constraint:** Zero external cloud API calls during runtime; must run on standard edge CPU/GPU hardware.
- **Metric 1 (Latency):** End-to-end local processing (STT + LLM intent routing + MQTT publish) under **1.5 seconds** per utterance.
- **Metric 2 (Reliability):** 100% accurate MQTT topic routing for emergency distress phrases (`QoS 1` or `QoS 2`).
- **Metric 3 (Noise Rejection):** Zero false-positive alerts triggered by ambient background noise.
