---
name: socratic-ai-rag
description: >-
  Build context-grounded educational AI assistants using Google Gemini API, transcript RAG,
  timestamp linking, and Socratic pedagogical prompting. Use when developing conversational learning agents.
---

# Socratic Educational AI & Transcript RAG Assistant

This skill guides the construction of the "Ustad" AI teaching assistant, ensuring it acts as an inspiring tutor rather than an answer-leaking cheat engine.

## 1. Grounded Context (RAG over Course Transcripts)
- **Course Material Grounding:** The assistant must ONLY answer questions using the current lesson's video transcript, lecture notes, and attached resources.
- **Timestamp Hyperlinking:** Every explanation must cite exact video timestamps:
  - Format: `[Videonun 03:45 dəqiqəsində izah edilir ▶](#seek=225)`
- **Hallucination Prevention:** If the answer is not present in the lesson materials, respond gracefully:
  - *"Bu mövzu cari dərsdə əhatə olunmayıb. Müəllimin təqdim etdiyi materiallar üzrə sual versəniz, sizə məmnuniyyətlə istiqamət verərəm."*

## 2. The Socratic Pedagogical Method
- **Never give direct code or exam answers:** Instead of solving the student's homework, ask probing questions that guide the student to the discovery.
- **Example Interaction:**
  - *Student:* "Why does my loop give IndexOutOfRangeException?"
  - *Socratic Ustad:* "Array-in uzunluğu 5 olduqda, ən sonuncu indeks hansı nömrə olur? Loop-un şərtində `<` yoxsa `<=` yazmısınız?"

## 3. Server-Authoritative Exam Lock
- **State Check:** Before invoking `IAiAssistantService`, verify the student's current enrollment and exam status.
- If the student is currently enrolled in an active, in-progress exam:
  - Immediately return HTTP `403 Forbidden` / `423 Locked`.
  - JSON payload: `{ "error": "EXAM_ACTIVE_AI_LOCKED", "message": "İmtahan zamanı AI köməkçidən istifadə qadağandır." }`
  - This constraint is enforced server-side and cannot be bypassed via frontend script tampering.

## 4. Quick Learning Modes
Support structured quick actions:
- **`ELI5` (Explain Like I'm 5):** Simplified conceptual metaphor.
- **`Flashcard Mode`:** 3 key takeaway questions with spoiler tags for self-testing.
- **`Summary`:** 3-bullet core takeaway.
