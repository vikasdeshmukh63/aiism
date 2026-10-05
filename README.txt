AIIMS Gorakhpur - Recruitment Portal (front-end prototype)
==========================================================

Files
-----
index.html     Home page (advertisements, posts, services, instructions,
               Hindi/English switch, help chatbot, compliance footer)
register.html  New Registration (4 steps: personal details, mobile/e-mail/
               Aadhaar OTP verification, password + CAPTCHA, review & declaration)
login.html     Candidate Login (password or OTP login, Forgot Password,
               Forgot Registration ID, 5-attempt lockout)

How to use
----------
Keep all three files in the same folder and open index.html in a browser.
All Home links and the header logo go to index.html.
The AIIMS logo loads from aiimsgorakhpur.edu.in, so an internet connection is
needed to see it. For offline use, save the logo as logo.png in this folder and
replace the logo URL with "logo.png" in all three files.

Prototype test values (remove before go-live)
---------------------------------------------
OTP (all screens):            123456
Test Aadhaar (register):      2345 6789 0124
Already-registered mobile:    9876543210
Login:                        AGKP26123456 or 9123456789 / Demo@1234
Date of birth for reset:      15.08.1990
To switch the demo off, set  var DEMO=false  in register.html and login.html
(this also removes the dark "PROTOTYPE" note).

Before go-live (backend team)
-----------------------------
- Connect real SMS / e-mail OTP, UIDAI Aadhaar authentication, DigiLocker,
  PubMed and Google reCAPTCHA (replaces the built-in CAPTCHA).
- Store passwords hashed on the server; enforce lockout and session timeout
  server-side.
- Fill the placeholders shown in orange italics: helpdesk phone/e-mail,
  STQC certificate no., security audit date, hosting, visitor counter.
- Get the Hindi text vetted by the Rajbhasha cell.
- Confirm with legal/administration whether Aadhaar may be mandatory
  (Aadhaar Act notification); otherwise make it optional with an alternative ID.
- Delete aiims-gkp-rms-landing.html (old page) if it is still in your folder.
