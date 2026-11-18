# 🛡️ ELIA: Edge Language & Intent Agent

**Sejong Student:** PRADHAN BIBISHA   
**Project Type:** IoT & Edge AI Project

## Overview
**ELIA** is an offline, privacy-preserving Edge AI and IoT intent router. It captures multilingual speech locally, translates and transcribes it on-device using **Faster-Whisper**, evaluates conversational or emergency intent using a local Small Language Model (**Ollama / Llama 3.2**), and dispatches real-time actions across an IoT network via an **Eclipse Mosquitto MQTT** broker.

## Key IoT & Edge Capabilities
- **Zero Cloud Dependency:** 100% local inference eliminates cloud latency and ensures strict audio privacy.
- **Smart Intent & Problem Solving:** Acts as an offline conversational assistant while continuously monitoring for emergency distress phrases.
- **MQTT Pub/Sub Architecture:** Routes structured JSON intents to dedicated MQTT topics (`elia/alerts/emergency`, `elia/chat/response`) for downstream IoT actuators and local Text-to-Speech (TTS).
