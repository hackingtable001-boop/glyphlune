Glyphlune: marketplace for logos and photos, 31 HTML pages (30 site pages + auth.html)

Open index.html in a browser. No server needed. CSS and JS are inline in every page.
The "Store" button in the header opens the mega menu.

Admin panel: the three-line button at the bottom-left of every page.
 - Add items with a mark OR an uploaded photo (photos are resized and stored in the browser).
 - Mark items as exclusive (they disappear from the store after purchase).
 - The password is stored as a hash (ADMIN_H in the script), not as plain text.
   To change it: open any page, press F12, run  h53('your new password')  in the console,
   and put the resulting number into ADMIN_H in every HTML file.
   This is only demo-level protection. Real protection needs a server.

Log in / Sign up: auth.html
 - Google sign-in + 6-digit email code verification (10 min expiry, 5 tries, 60 s resend).
 - Open auth.html and fill the CONFIG block at the top of its script:
     GOOGLE_CLIENT_ID  (Google Cloud Console -> OAuth client ID, Web; add your site to Authorized JavaScript origins)
     EMAILJS           (emailjs.com, connect Gmail; template uses {{to_email}} {{name}} {{code}})
 - Empty config = demo mode: the code is shown on the page instead of being emailed.
 - Verified user is saved in localStorage key 'gl_user'. Verification here is client-side only:
   real security (and SMS via Twilio etc.) needs a server.
Items, cart, wishlist and settings live in the browser (localStorage, about 5 MB).
Showing admin changes to all visitors needs a backend and database.
