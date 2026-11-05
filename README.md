# FoodBridge - setup checklist

Files in this folder
- index.html            the whole app
- firestore.rules       database security rules
- manifest.webmanifest, sw.js, icon-192.png, icon-512.png   make the app installable on phones
- firebase.json         Firebase Hosting + rules deploy settings

## 1. Rules (do this first)
Firebase Console > Firestore Database > Rules > paste firestore.rules > Publish.

## 2. Put the site online (Firebase Hosting, free plan is enough)
    npm install -g firebase-tools
    firebase login
    firebase init hosting      (choose your project foodbridge-1727f, keep public folder ".", do NOT overwrite index.html)
    firebase deploy

Also add your new site address in
Firebase Console > Authentication > Settings > Authorized domains.

## 3. After the first deploy
1. Log in as admin > Admin Dashboard > All donations > "Secure old donations".
2. Cloudinary > Settings > Upload > preset "foodbridge_upload": allow only jpg/png/webp and set a max file size.
3. Make one real admin: Firebase Console > Firestore > users > your document > role = "admin".
4. Optional: create a second EmailJS template for pickup schedules and put its ID in
   EMAILJS_TEMPLATE_PICKUP inside index.html. Template variables:
   donor_email, donor_name, ngo_name, food_name, pickup_time, pickup_note.

## 4. Test with three accounts
donor, NGO, admin: post, accept, schedule, confirm, chat, complete, rate, report, block.
