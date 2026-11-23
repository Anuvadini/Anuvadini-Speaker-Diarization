# Anuvadini Speaker Diarization

Speaker diarization for the 22 scheduled Indian languages and English: who spoke when, with stable speaker identity across a whole recording, in batch or real time.

## Architecture
| Model | Design | Parameters |
|---|---|---|
| End-to-end neural diarization | 8× convolutional subsampling → 17 Conformer blocks (width 512, 8 heads, feed-forward 2,048, kernel 31) → 18-layer Transformer (width 192, 8 heads) → sigmoid outputs for up to 4 simultaneous speakers per 90-second window, including overlapped speech | 113,630,020 |
| Speaker embedding | 6 Conformer blocks (width 256) → attentive statistics pooling → 192-dimensional embedding; links speakers across windows | 9,926,848 |
| **Total** |  | **123,556,868** |

## Capabilities
- Speaker-labelled segments with segment-level and word-level timestamps
- Batch (full-file) diarization and real-time speaker separation
- Robust on telephony and conversational audio, including 8 kHz call-centre recordings and code-mixed speech; attribution preserved across language switches
- Transcription and diarization in a single request together with Anuvadini ASR

## Deployment
Single GPU; Docker / OCI container with REST API; air-gapped. Capacity design: 25,00,00,000 minutes of audio per year = ≥ 475.6× real time sustained.

---
© Anuvadini Foundation. All rights reserved. Documentation only.
