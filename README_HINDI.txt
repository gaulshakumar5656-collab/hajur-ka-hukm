हजूर का हुक्म — वेबसाइट स्टार्टर

इस ZIP में:
- index.html : लोगों को दिखने वाला मुख्य पेज
- admin.html : हजूर का लॉगिन और संदेश बदलने का पैनल
- supabase_setup.sql : सुरक्षित बैकएंड/डेटाबेस के लिए SQL

महत्वपूर्ण:
यह तैयार शुरुआती प्रोजेक्ट है, अभी लाइव वेबसाइट नहीं है। डोमेन पर प्रकाशित करने और वास्तविक एडमिन लॉगिन चालू करने के लिए Supabase और होस्टिंग सेटअप करना बाकी है।

सेटअप के चरण:
1. https://supabase.com पर प्रोजेक्ट बनाएँ।
2. SQL Editor में supabase_setup.sql चलाएँ।
3. Authentication > Users में हजूर का ईमेल/पासवर्ड वाला यूजर बनाएँ।
4. उस यूजर की UUID कॉपी करें। SQL Editor में चलाएँ:
   insert into public.site_admins (user_id) values ('यहाँ-UUID');
5. Project Settings > API से Project URL और anon/public key लें।
6. index.html और admin.html दोनों में:
   YOUR_SUPABASE_PROJECT_URL
   YOUR_SUPABASE_ANON_KEY
   को अपनी असली जानकारी से बदलें।
7. Supabase Database > Replication/ Publications में site_message के लिए Realtime चालू करें (यदि उपलब्ध UI में publication चुनना हो, तो supabase_realtime में site_message जोड़ें)।
8. दोनों HTML फाइलें होस्टिंग पर अपलोड करें। मुख्य वेबसाइट index.html होगी; एडमिन पेज /admin.html पर खुलेगा।

सुरक्षा:
- anon/public key वेबसाइट में रखना सामान्य है; service_role key कभी भी HTML/ब्राउज़र में न डालें।
- केवल site_admins में जोड़ा गया Auth user संदेश बदल सकता है।
- पासवर्ड किसी के साथ साझा न करें।
- पहले परीक्षण के लिए अलग admin account बनाएँ।

डोमेन:
डोमेन का नाम और वह कहाँ से खरीदा है यह मिलने पर DNS को होस्टिंग से जोड़ने के सटीक चरण बताए जा सकते हैं।
