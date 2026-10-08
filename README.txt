AIIMS Gorakhpur - Recruitment Portal (front-end prototype)
==========================================================

Files
-----
index.html      Home page (advertisements, posts, How to Apply, services,
                instructions, Hindi/English switch, help chatbot, compliance footer).
                One "Login / Register" button opens candidate.html.
candidate.html  Candidate Login & Registration on ONE page:
                - Login tab: password login, or OTP login on the registered mobile
                  number OR Aadhaar number (UIDAI OTP), Forgot Password,
                  Forgot Registration ID, 5-attempt lockout
                - After login: candidate profile with General, Education,
                  Experience, Documents and Other sections, plus completion
                  progress and required-field checks
                - New Registration tab: 4 steps (personal details, mobile/e-mail/
                  Aadhaar OTP, password + CAPTCHA, review & declaration)
                Deep links: candidate.html#register, candidate.html#forgot
staff.html      Staff & Committee Login (separate from candidates; no self-registration).
                User ID + password + CAPTCHA, then OTP on the registered mobile.
                Role is taken from the account: Super Admin, Recruitment Admin,
                HOD, Director, Screening Officer, Interview Panel, Auditor.
                After login, staff land on a role-aware dashboard with a sidebar,
                live browser-record metrics and clearly labelled illustrative
                sample charts. Super Admin and Recruitment Admin can create
                drafts, configure eligibility and enter an approved 200-point roster; HOD, Recruitment Admin
                and Director review sequential approval queues. Approved drafts
                can be published or closed. Reports include a browser-local
                audit log with CSV export. Screening/shortlisting, interviews,
                document verification, merit/results and offers are currently
                workflow descriptions, not live operational modules.
                On saving a valid draft, the system generates
                AIIMS-GKP-YYYY-XXX: the three-digit sequence starts at 001 and
                resets each calendar year (maximum 999 per year), with Draft
                status, an empty eligibility-rules container and a roster
                placeholder.
                Linked from "Staff Login" on the home page and the candidate page.
campus.webp     Campus sketch used as the background of candidate.html
register.html,  Old addresses kept only as redirects to candidate.html
login.html      (#register / login tab), so old links and bookmarks still work.

How to use
----------
Keep all files in the same folder and open index.html in a browser.
All Home links and AIIMS logo links go to index.html. The staff login uses the
same split-screen branding layout as candidate login; its masthead is shown
only after sign-in on the staff dashboard.
The AIIMS logo loads from aiimsgorakhpur.edu.in, so an internet connection is
needed to see it. For offline use, save the logo as logo.png in this folder and
replace the logo URL with "logo.png" in all three files.

Prototype test values (remove before go-live)
---------------------------------------------
OTP (all screens):            123456
Test Aadhaar (register and Aadhaar OTP login): 2345 6789 0124
Already-registered mobile:    9876543210
Login:                        AGKP26123456 or 9123456789 / Demo@1234
Staff login (staff.html), password Admin@1234, OTP 123456:
  superadmin, recadmin, hod.cardio, director, screening01, panel01, auditor01
Date of birth for reset:      15.08.1990
In demo mode, New Registration opens with sample data already filled in
(OTP and CAPTCHA are filled automatically too), so reviewers can click
Save & Continue through all 4 steps. "Fill sample registration" fills any
remaining blank fields; "Clear form" empties it. Candidate login, OTP, password
reset, Registration ID retrieval and each profile section also have demo-fill
shortcuts. Profile sample actions only fill blank fields and never create
document files.
Staff login/OTP, recruitment draft and eligibility forms have demo-fill
shortcuts. The 200-point roster shortcut contains format-test data only; it is
not an institute-approved roster and must not be used for a real recruitment.
Sample-fill buttons are hidden when DEMO=false. Legal declarations/consents
remain unchecked and document uploads still require real files.
To switch the demo off, set  var DEMO=false  in candidate.html and staff.html
(this also removes the dark "PROTOTYPE" note and the sample data).

Before go-live (backend team)
-----------------------------
- The Recruitment ID is issued only when a Super Admin or Recruitment Admin
  saves a valid recruitment entry (post type, department, vacancy count and
  recruitment type). The year is the creation year; the sequence resets to 001
  each calendar year and increments per recruitment, up to 999. Recruitment
  IDs are separate from candidate Registration IDs and submitted Application
  IDs.
- The staff dashboard's draft, eligibility, roster, approval, publication,
  closure and audit flows are a browser-only demonstration using localStorage.
  Implement server-backed workflow records, role enforcement, atomic approval
  transitions, a durable audit trail and database-enforced Recruitment ID
  uniqueness before production. The downstream candidate application,
  screening, interview, verification, selection, result and offer modules are
  not implemented as working services in this prototype.
- Recruitment records and sequence numbers currently use this browser's
  localStorage for the prototype. Replace with an atomic server-side sequence
  and database uniqueness constraint before production so simultaneous users,
  other devices and browsers cannot issue duplicate IDs.
- Connect real SMS / e-mail OTP, UIDAI Aadhaar authentication, DigiLocker,
  PubMed and Google reCAPTCHA (replaces the built-in CAPTCHA).
- Connect candidate profile saves and document uploads to secure backend
  storage; profile edits and selected files are not persisted in this prototype.
- Staff accounts must be created by the Super Admin on the server; remove the
  dummy STAFF list from staff.html. Enforce role permissions on the server,
  not only in the page.
- Store passwords hashed on the server; enforce lockout and session timeout
  server-side.
- Fill the placeholders shown in orange italics: helpdesk phone/e-mail,
  STQC certificate no., security audit date, hosting, visitor counter.
- Get the Hindi text vetted by the Rajbhasha cell.
- Confirm with legal/administration whether Aadhaar may be mandatory
  (Aadhaar Act notification); otherwise make it optional with an alternative ID.
- Delete aiims-gkp-rms-landing.html (old page) if it is still in your folder.

Campus photo on the login page (optional)
-----------------------------------------
The left panel of candidate.html shows a blueprint-style sketch of the AIIMS
Gorakhpur campus (file: campus.webp, keep it next to candidate.html).
To use a real AIIMS Gorakhpur campus photo instead, save it in this folder as
campus.jpg and, in candidate.html, change  .side-l{--photo:none}  to
.side-l{--photo:url('campus.jpg')}. The navy overlay keeps the text readable.
