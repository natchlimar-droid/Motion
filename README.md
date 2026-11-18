# NeuroScreen Pro

Client-side mobile neuromotor & cognitive screening platform (MDS-UPDRS Item 3.4 & 3.15 compliant).

## Overview
NeuroScreen Pro runs 100% on-device inside standard mobile and desktop browsers using MediaPipe Vision Tasks (WASM + WebGL). It evaluates fine motor coordination, bradykinesia, tremor, and facial expressivity without uploading raw video.

## Features
- **Bilingual Interface (TH | EN)**: Instant real-time toggle between Thai and English with standardized English export keys for downstream data analytics.
- **Age-Stratified Z-Score Normalization**: Automatically benchmarks tapping cadence and fatigue against normative age cohorts (<40, 40-59, 60-69, 70-79, 80+) to prevent false positives in older adults.
- **Facial & Blink Screening (Module C)**: MediaPipe FaceLandmarker analysis measuring spontaneous blink rate (blinks/min) and smile symmetry to screen for facial masking (hypomimia).
- **Key-Frame Visual Snapshots**: Automatically captures and annotates peak aperture and late-stage fatigue frames directly into the printable medical report.
- **Zero-Backend Cloud Webhook**: One-click sync to Google Sheets or custom REST endpoints without managing dedicated server infrastructure.
- **Bilateral Comparison**: Sequential assessment of right and left hands calculating the Bilateral Asymmetry Index (%).
- **2D Scale Invariance**: Normalizes pinch aperture by 2D palm scale to avoid noisy Z-depth estimations.
- **PWA & Offline Capable**: Installable on iOS Safari and Android Chrome via Service Worker caching.

## Free Google Sheets Webhook Setup
To store screening results directly into Google Sheets:
1. Create a new Google Sheet.
2. Navigate to **Extensions** > **Apps Script**.
3. Replace the script with:
```javascript
function doPost(e) {
  var sheet = SpreadsheetApp.getActiveSpreadsheet().getActiveSheet();
  var data = JSON.parse(e.postData.contents);
  if (sheet.getLastRow() === 0) {
    sheet.appendRow(Object.keys(data));
  }
  sheet.appendRow(Object.values(data));
  return ContentService.createTextOutput(JSON.stringify({"status": "success"})).setMimeType(ContentService.MimeType.JSON);
}
```
4. Click **Deploy** > **New deployment** > Select **Web app**.
5. Set **Execute as:** `Me` and **Who has access:** `Anyone`.
6. Copy the Web App URL and paste it into the **Cloud** settings inside NeuroScreen Pro.

## Deployment on GitHub Pages
1. Go to repository **Settings** > **Pages**.
2. Select branch `main` and folder `/ (root)`.
3. Save to activate the secure HTTPS URL.
