---
title: "AI Projects"
permalink: /projects/
layout: single
author_profile: false
---

## AI Transcription + Summarization Pipeline

**Summary**  
An offline-first transcription and summarization system using WhisperX, Mistral, and custom automation scripts. Built to capture meeting audio, transcribe speakers, and generate concise summaries—all on local hardware for privacy.

<p align="center">
  <img src="/assets/images/transcription_pipeline.png" alt="Transcription Pipeline Diagram" width="600">
</p>

**Stack**  
- WhisperX with speaker diarization  
- `ffmpeg` for audio processing  
- VB-CABLE for system audio routing  
- PowerShell + Python scripts  
- Mistral-7B GGUF model (local)

**My Role**  
- Designed architecture  
- Wrote full setup, deployment, and troubleshooting documentation  
- Created PowerShell automation script for meeting capture  
- Wrote `redactor.py` for privacy-safe name removal

[View full repo and docs on GitHub →](https://github.com/DG-Crawford/ai-transcription-pipeline)

---

##Redactor Script (Privacy Layer)

**Summary**  
A standalone name redaction utility written in Python, integrated as a post-processing step for the transcription pipeline.

**Features**  
- Regex pattern-based scrubbing  
- Command line flags for optional redaction types  
- Output to cleaned `.txt` for summarization

**My Role**  
- Developed script  
- Documented usage in both README and longform  
- Designed to integrate cleanly with transcription workflows

[🔗 View script in repo →](https://github.com/DG-Crawford/ai-transcription-pipeline/blob/main/redactor.py)

---

##Future Projects

**Data-Centric AI Ops Docs (WIP)**  
Upcoming documentation projects that simulate the onboarding experience for data-centric AI workflows, including:
- Static site docs for a fictional model zoo
- Prompt engineering pattern guide
- ML pipeline troubleshooting sample

*Coming soon.*
