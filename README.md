# My Medicine Check / GlutenMed Libya — Website prototype

Bilingual (Arabic/English), responsive, four-page static website for the University of Tripoli pharmacy graduation project.

## Pages
- `index.html` — medicine search and research tool overview
- `faq.html` — frequently asked questions
- `participate.html` — patient and pharmacist survey entry points
- `submit.html` — questions, medicine photo submissions, and review workflow

## Dataset
`data/medicines.json` contains all 111 rows from the supplied audited Excel file and preserves the source fields: product ID/type, brand/generic names, manufacturer/country, dosage form/strength, therapeutic category, excipient-list completeness, source, exact excipient wording, source specification, category, and evidence.

Category counts: A=45, B=14, C=44, D=8.

## Configure Google Forms / Sheets
Edit `config.js` and add public responder URLs for:
- `patientSurveyUrl`
- `pharmacistSurveyUrl`
- `questionFormUrl`

Optional: `medicinesCsvUrl` can point to a published read-only Google Sheets CSV using the dataset field names or the original Excel column headings. The local JSON is the fallback.

Optional: `approvedQuestionsCsvUrl` is reserved for an administrator-approved public answer feed; this prototype does not automatically publish raw submissions.

For image uploads, create a Google Form with a File upload question. Google Forms file upload normally requires respondents to sign in to a Google account. Store responses and uploaded files privately. Do not publish the response spreadsheet or uploaded images.

## Admin review process
1. Receive a question/photo in a private Google Form response sheet/Drive folder.
2. Check the exact brand, strength, dosage form, package/leaflet version, excipient wording and source.
3. Record the evidence and date of verification.
4. Obtain the required scientific/admin approval.
5. Only then update the public dataset / approved answers feed.
6. Never publish patient identifiers, prescriptions or raw uploaded photos.

## Free hosting
This is a static site and can be hosted using GitHub Pages on a public repository at no hosting cost. No server, login system, or private backend is included. Google services have usage limits and Google Forms file uploads require sign-in. A custom domain is optional and may cost money.

## Local preview
Run `python -m http.server 8000` from this folder and open `http://localhost:8000`. Do not open `index.html` as a `file://` URL because browsers may block local JSON fetches.

## Scientific limitations
The category is documentary only; it is not a laboratory test and does not prove that a medicine is safe or unsafe. A/Green and D/Blue do not prove gluten-free status; B/Red does not quantify gluten; C/Amber means documentation is incomplete/ambiguous, not proof of gluten. Users must not stop essential medicines without professional advice. The source guide recommends rechecking entries every 6–12 months and whenever a new presentation is dispensed.

## AI phase (not included)
AI is intentionally not connected in this prototype. A future assistant should answer only from approved database records and vetted references, identify missing evidence, refuse to infer a product's status from a generic name alone, and route medicine-specific questions to a pharmacist. Never expose Google API keys in client-side JavaScript; any AI API integration requires a protected backend and may not remain free.
