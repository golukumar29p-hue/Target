# TARGET BIHAR BOARD HELP

यह Firebase Authentication और Cloud Firestore आधारित शुरुआती वेबसाइट है। यह केवल HTML फ़ाइल खोलने से पूरी तरह नहीं चलेगी; Firebase configuration और hosting चाहिए।

## सेटअप
1. https://console.firebase.google.com/ पर नया प्रोजेक्ट बनाएँ। Web app register करें और `firebase-config.js` में असली config values डालें। **Firebase web API key पासवर्ड नहीं होती**, फिर भी असली पासवर्ड कोड में न डालें।
2. Firebase Console → Authentication → Sign-in method → Email/Password चालू करें।
3. Firestore Database बनाएँ और Rules टैब में `firestore.rules` की सामग्री डालकर Publish करें। Production में नियमों की समीक्षा करें।
4. वेबसाइट को HTTPS hosting पर रखें (उदाहरण: Firebase Hosting या Netlify)। Firebase Authentication → Settings → Authorized domains में अपना डोमेन जोड़ें। Local testing के लिए `localhost` भी जरूरत पड़ने पर जोड़ें।
5. वेबसाइट पर अपना अकाउंट बनाएँ। Firebase Console → Authentication → Users से अपना **UID** कॉपी करें। Firestore → `admins` collection में उसी UID को document ID बनाकर document बनाएँ; उदाहरण field `role` = `admin`। यह काम केवल Firebase Console से करें, वेबसाइट से नहीं। फिर पेज reload करें। अब Admin बटन दिखेगा।
6. एडमिन पैनल में प्रश्न और नोट जोड़ें। बाकी छात्र अकाउंट बनाकर टेस्ट दे सकते हैं।

## ज़रूरी सीमाएँ
- अभी कोई sample questions नहीं हैं; एडमिन प्रश्न जोड़ता है।
- टेस्ट के सही जवाब browser में भेजे जाते हैं, इसलिए यह अभ्यास टेस्ट है, सुरक्षित/प्रतिस्पर्धी परीक्षा नहीं। छात्र अपने स्कोर को client से बदलकर भेज सकते हैं; विश्वसनीय स्कोर के लिए Cloud Functions/server-side grading चाहिए।
- प्रश्नों/नोट्स को edit/delete करने का UI अभी नहीं है; Firebase Console से बदल सकते हैं।
- Passwords Firebase Authentication संभालता है; अपने Firestore में passwords कभी न रखें।
- विद्यार्थियों का डेटा रखने से पहले privacy policy, consent और data retention व्यवस्था तैयार करें।
