# Clinical Transcript Navigator

AI-powered clinical transcript extraction and SOP routing 
assistant for healthcare Care Teams.

**Live demo:** https://premier-call-transcript.vercel.app
**Built with:** Claude Opus · Google Gemini · Streamlit · Python

## What It Does
Extracts structured clinical facts from unstructured patient 
call transcripts, evaluates them against clinical SOPs, and 
delivers prioritized routing recommendations with confidence 
scoring — in under 30 seconds.

## Architecture
- **Stage 1:** Claude Opus extracts 13 clinical flags 
  with source quotes and field-level confidence
- **Stage 2:** Deterministic Python SOP rule engine 
  evaluates all 8 rules — same output every run
- **Stage 3:** Google Gemini independently scores 
  recommendation quality across 4 dimensions
- **Stage 4:** Specialist reviews, agrees or disagrees, 
  pushes structured output to EHR

## Setup
\`\`\`bash
git clone https://github.com/jstrifa-bit/Clinical-Transcript-Navigator
cd Clinical-Transcript-Navigator
pip install -r requirements.txt
cp .env.example .env  # add your API keys
streamlit run app.py
\`\`\`

## Edge Cases Handled
- Incomplete transcripts → Pending disposition, no false routing
- Inaudible gaps → null flags, never inferred
- Patient contradictions → surfaced explicitly, not resolved
- Wrong file type → blocked before API call
- API timeout → safe fallback, human review triggered
