# ArenaX – Tournament Manager (GitHub Pages + Firebase)

ফাইলসমূহ: `index.html` (অ্যাপ), `firebase-config.js` (আপনার Firebase তথ্য), `firestore.rules` (ডেটাবেস নিরাপত্তা)।

## সেটআপ (একবারই)

1. https://console.firebase.google.com এ নতুন প্রজেক্ট খুলুন।
2. **Build → Authentication → Sign-in method:** *Google* ও *Email/Password* চালু করুন।
   **Settings → Authorized domains:** `আপনার-ইউজারনেম.github.io` যোগ করুন।
3. **Build → Firestore Database → Create database** (Production mode)।
   **Rules** ট্যাবে `firestore.rules` এর লেখা পেস্ট করুন এবং `your-admin-email@gmail.com` এর জায়গায় আপনার অ্যাডমিন জিমেইল বসিয়ে **Publish** করুন।
4. **Project settings → Your apps → Web (`</>`)** থেকে config কপি করে `firebase-config.js` এ বসান এবং `ADMIN_EMAILS` এ একই জিমেইল দিন।
5. GitHub এ নতুন রিপোজিটরি খুলে চারটি ফাইলই আপলোড করুন → **Settings → Pages → Deploy from branch (main / root)**।
6. লিংক খুলে **Google দিয়ে অ্যাডমিন ইমেইলে** সাইন ইন করুন। অ্যাডমিন প্যানেল দেখা যাবে এবং Nagad নম্বরগুলো স্বয়ংক্রিয়ভাবে সেভ হবে।
   টুর্নামেন্টগুলো অ্যাডমিন → টুর্নামেন্ট থেকে আবার তৈরি করতে হবে।

## জেনে রাখুন

- আমি এটা আসল Firebase-এ চালিয়ে পরীক্ষা করতে পারিনি। প্রথমবার চালিয়ে সব ফ্লো দেখে নিন।
- লগইন: Google অথবা ইমেইল+পাসওয়ার্ড। পাসওয়ার্ড ভুললে ইমেইলে রিসেট লিংক যায়। (ইউজারনেম লগইন ও ফোন-নম্বর মিলিয়ে রিসেট এই ভার্সনে নেই; SMS OTP চাইলে Firebase Phone Auth আলাদাভাবে যোগ করতে হবে।)
- অ্যাডমিন হতে হলে ভেরিফাইড ইমেইল লাগে, তাই অ্যাডমিন Google দিয়ে ঢুকবেন।
- Firebase `apiKey` গোপন নয়; নিরাপত্তা আসে `firestore.rules` থেকে, তাই রুলস অবশ্যই পাবলিশ করুন।
- ওয়ালেট ব্যালেন্স ব্রাউজারে হিসাব হয়; অ্যাডমিন অনুমোদনের সময় যাচাই করেন। কড়া নিয়ন্ত্রণে Cloud Functions লাগবে।
- Room ID/Password শুধু অ্যাপের কোডে লুকানো, ডেটাবেস রুলস দিয়ে নয়।
- অটো পেমেন্ট API, পুশ নোটিফিকেশন এবং ওয়ালেট থেকে টাকা তোলা এখনো নেই।
- কাস্টমার সার্ভিস WhatsApp নম্বর `index.html` এ `wa.me` লিখে খুঁজে বদলানো যাবে।
