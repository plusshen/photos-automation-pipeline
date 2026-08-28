# LINE Event Photo Review Pipeline

An automated pipeline connecting LINE Messaging API, Google Workspace, and OpenAI Vision to streamline NPO event tracking and photo assessment.

![System Architecture](https://github.com/user-attachments/assets/91c61a98-8e58-4ce3-8e4e-6dd7f7c5a84c)

## 🎯 Problem Statement (解決的痛點)
In non-profit organization (NPO) field operations, staff frequently send event photos to LINE groups. However:
* **Manual Archiving is Time-Consuming:** Administrative staff spend 2–3 hours per week manually downloading, renaming, and uploading photos to Google Drive.
* **Risk of Missing Photos:** Crucial photos (e.g., group photos, sign-in sheets) are often missed or forgotten during field events, and missing them isn't noticed until the event ends.
* **Expiration Risk:** Photos shared in LINE chat rooms expire after 7 days if not archived immediately.

---

## ✨ Key Features (核心功能)
* **Instant Auto-Archiving:** Automatically triggers on LINE photo uploads, fetching binary image data and storing it in dynamic Google Drive folders (`/YYYY-MM_Event/`).
* **AI Photo Assessment (OpenAI Vision):** Analyzes uploaded images in real-time to detect photo types (e.g., Group Photo, Workshop Interaction, Sign-in Sheet).
* **Missing Photo Counter & Feedback:** Tracks progress against a pre-set quota (stored in Google Sheets) and automatically sends instant progress updates back to the LINE chat room.
* **Error Handling & Logging:** Captures unexpected API failures and logs details without breaking the pipeline execution.

---

## 🛠️ Tech Stack & Architecture (技術棧與架構)
* **Automation Platform:** Make.com
* **Integrations:** LINE Messaging API (Push/Reply Messaging), Google Sheets, Google Drive, OpenAI API (GPT-4o Vision)
* **Core Concepts:** Asynchronous handling, Webhook listening, Data mapping, JSON Parsing, Iterator/Aggregator logic.

---

## 🚀 How to Replicate / Installation (部署與匯入步驟)

1. **Import Blueprint:**
   * Download `blueprint.json` from this repository.
   * Go to your **Make.com** dashboard, create a new Scenario, click `...` at the bottom, and select **Import Blueprint**.
2. **Configure API Keys & Connections:**
   * **LINE Messaging API:** Set up your Channel Access Token and Secret in the Webhook module.
   * **OpenAI API:** Add your OpenAI API Key for GPT-4o Vision access.
   * **Google Workspace:** Connect your Google Drive and Google Sheets accounts with appropriate read/write scopes.
3. **Set Up Google Sheets:**
   * Create a spreadsheet with columns: `[Timestamp, Sender, Photo Type, Storage URL]`.

---

## 📁 Repository Contents (專案檔案說明)
* `blueprint.json`: Complete Make.com Scenario export file. Import this directly into Make.
* `README.md`: System documentation and setup guide.
