স্মার্ট মেস ম্যানেজার — PWA + Shared Cloud Data
================================================

গুরুত্বপূর্ণ:
- এটি একটি সেটআপ-প্রয়োজনীয় স্টার্টার প্যাকেজ। Firebase project/config না বসালে অনলাইন হিসাব চলবে না।
- এই ডেমো Firestore Rules-এ লগইন করা anonymous user-দের একই ডেটা পড়া/লেখার অনুমতি আছে। লিংক পাওয়া যে কেউ হিসাব পরিবর্তন করতে পারে। বাস্তব মেসে ব্যবহার করার আগে Authentication এবং নিরাপদ Rules তৈরি করুন।
- অ্যাপের বর্তমান manager PIN (1234) ক্লায়েন্ট কোডে আছে; এটি নিরাপত্তা নয়।
- CDN-এ React/Babel/Tailwind/Firebase থাকায় প্রথম লোডে ইন্টারনেট দরকার। PWA shell ক্যাশ হয়, কিন্তু ক্লাউড ডেটা অফলাইনে sync হবে না।

A. Firebase সেটআপ
1. https://console.firebase.google.com/ খুলে Add project দিয়ে একটি project তৈরি করুন।
2. Project settings > General > Your apps > Web app (</>) যোগ করুন; config কপি করুন।
3. Authentication > Sign-in method > Anonymous চালু করুন।
4. Firestore Database তৈরি করুন (production mode নির্বাচন করা ভালো)।
5. index.html-এ firebaseConfig খুঁজে PASTE_YOUR_API_KEY, PASTE_YOUR_PROJECT_ID, PASTE_YOUR_APP_ID ইত্যাদি নিজের config দিয়ে বদলান।
6. Firestore > Rules-এ firestore.rules ফাইলের demo rule বসিয়ে Publish করলে টেস্ট চলবে। এই rule অনিরাপদ; শুধু পরীক্ষার জন্য।

B. নিরাপদে প্রকাশ করার আগে
- Manager ও member-এর আলাদা পরিচয়/লগইন তৈরি করুন।
- Firestore-এ server-side role যাচাই করে manager ছাড়া deposits, expenses, fines, members পরিবর্তন নিষিদ্ধ করুন।
- manager PIN কোড থেকে সরান; ক্লায়েন্টে থাকা PIN গোপন রাখা যায় না।
- গুরুত্বপূর্ণ ডেটার ব্যাকআপ/এক্সপোর্ট যোগ করুন।

C. GitHub Pages-এ বিনামূল্যে প্রকাশ
1. ZIP Extract করুন।
2. GitHub-এ smart-mess-manager নামে public repository তৈরি করুন।
3. এই ফোল্ডারের সব ফাইল repository root-এ upload/commit করুন (index.html root-এ থাকতে হবে)।
4. Repository > Settings > Pages > Deploy from a branch > main > /(root) > Save।
5. প্রকাশিত HTTPS URL খুলে পরীক্ষা করুন। GitHub Pages URL যদি /repository-name/ হয়, এই প্যাকেজের relative paths সে জন্য সেট করা।
6. Android Chrome-এ URL খুলে menu > Install app বা Add to Home screen চাপুন।

D. Shared data টেস্ট
- দুইটি আলাদা ফোন/ব্রাউজারে প্রকাশিত URL খুলুন।
- একটি ফোনে test entry যোগ করুন; অন্যটিতে একই তথ্য আসছে কি না দেখুন।
- টেস্টের আগে বাস্তব/গুরুত্বপূর্ণ হিসাব যোগ করবেন না।

Troubleshooting
- “Firebase সেটআপ বাকি” দেখালে firebaseConfig পূরণ হয়নি।
- permission-denied এলে Authentication/Firestore Rules পরীক্ষা করুন।
- “Missing or insufficient permissions” হলে demo rule ঠিকমতো publish হয়েছে কি না দেখুন।
