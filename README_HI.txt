TG WIN — Cloudflare Pages deployment guide (Hindi)

यह केवल FREE POINTS मनोरंजन गेम है। Points की कोई नकद कीमत नहीं है। इसमें deposit, real-money betting, cash prize या withdrawal नहीं है। हर play का रंग तुरंत random demo result होता है; timer केवल display के लिए है। इसे असली prediction/earning platform न बताएं।

A. GitHub पर फाइलें
1) ZIP extract करें। सभी फाइलें और functions/ फ़ोल्डर GitHub repository TG-WIN के root में upload/replace करें।
2) GitHub repository में index.html, app.js, style.css, wrangler.toml और functions/ root पर दिखने चाहिए।

B. Cloudflare Pages
1) Cloudflare Dashboard → Workers & Pages → Create application → Pages → Connect to Git.
2) GitHub repository: TG-WIN चुनें।
3) Project name: tgwin (यदि उपलब्ध हो; नहीं तो कोई दूसरा नाम)।
4) Production branch: main.
5) Framework preset: None.
6) Build command: खाली छोड़ें (None).
7) Build output directory: . (एक dot).
8) Deploy करें। पुराना tg-win Worker delete न करें। Pages project अलग होगा।

C. D1 Database
1) Pages project → Storage & databases / D1 → Create database.
2) D1 database में Console खोलें और schema.sql की पूरी सामग्री चलाएं।
3) Pages project → Settings → Functions → D1 database bindings → Add binding.
   Variable name: DB
   D1 database: अभी बनाई गई database.
4) Binding save करके Pages project redeploy करें।

D. अपना Admin सुरक्षित तरीके से बनाएं (पहली बार ही)
1) Pages project → Settings → Variables and Secrets → Add secret.
   Name: ADMIN_SETUP_SECRET
   Value: कम-से-कम 40 अक्षरों का अपना random secret बनाएं। इसे किसी को न बताएं।
2) Save करके Pages redeploy करें।
3) अपनी वेबसाइट के URL के आगे /setup.html खोलें।
4) Secret, अपना admin username और कम-से-कम 12 अक्षरों का मजबूत password डालें। यह admin केवल एक बार बन सकता है।
5) Admin बनने के बाद Cloudflare Settings से ADMIN_SETUP_SECRET हटा दें और एक बार फिर redeploy करें। /setup.html अपने आप admin नहीं बना सकता, क्योंकि endpoint पहले admin के मौजूद होने पर मना कर देता है।

E. टेस्ट
- Homepage खोलें और अलग username से सामान्य Register करें। हर नए user को 1,000 free points मिलेंगे।
- Admin account से login करें; Admin dashboard दिखना चाहिए।
- Admin dashboard से user points adjust कर सकते हैं।
- वेबसाइट URL *.pages.dev होगा। tgwin.pages.dev तभी मिलेगा जब project name उपलब्ध हो।

Google Search
- Deploy होने के बाद Google Search Console में अपना Pages URL जोड़कर sitemap submit करें। Indexing में समय लग सकता है और इसकी गारंटी नहीं होती।

सुरक्षा नोट
- अपना Cloudflare/GitHub password, OTP या ADMIN_SETUP_SECRET किसी को न भेजें।
- यह starter/demo है, पूर्ण production security audit नहीं। Public launch से पहले rate limiting, abuse protection, privacy policy, terms और security review जोड़ें।
