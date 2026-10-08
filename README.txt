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
                - New Registration tab: 4 steps (personal details, mobile/e-mail/
                  Aadhaar OTP, password + CAPTCHA, review & declaration)
                Deep links: candidate.html#register, candidate.html#forgot
staff.html      Staff & Committee Login (separate from candidates; no self-registration).
                User ID + password + CAPTCHA, then OTP on the registered mobile.
                Role is taken from the account: Super Admin, Recruitment Admin,
                HOD, Director, Screening Officer, Interview Panel, Auditor.
                Linked from "Staff Login" on the home page and the candidate page.
campus.webp     Campus sketch used as the background of candidate.html
register.html,  Old addresses kept only as redirects to candidate.html
login.html      (#register / login tab), so old links and bookmarks still work.

How to use
----------
Keep all files in the same folder and open index.html in a browser.
All Home links and the header logo go to index.html.
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
Save & Continue through all 4 steps. "Clear form" empties it.
To switch the demo off, set  var DEMO=false  in candidate.html and staff.html
(this also removes the dark "PROTOTYPE" note and the sample data).

Before go-live (backend team)
-----------------------------
- Connect real SMS / e-mail OTP, UIDAI Aadhaar authentication, DigiLocker,
  PubMed and Google reCAPTCHA (replaces the built-in CAPTCHA).
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
