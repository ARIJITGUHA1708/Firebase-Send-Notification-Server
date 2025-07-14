This is a simple Express.js server that sends push notifications to a Flutter app using Firebase Cloud Messaging (FCM).

## 📦 Prerequisites

- Node.js & npm installed
- Firebase project with FCM enabled
- Firebase Admin SDK Service Account key JSON file
- Flutter app with `firebase_messaging` integrated and configured

🚀 Setup Instructions

1. Clone the Repository

```bash
git clone https://github.com/ARIJITGUHA1708/Firebase-Send-Notification-Server.git
cd Firebase-Send-Notification-Server
```

2. Install Dependencies

       npm install

3. Add Your Firebase Service Account Key

Download the serviceAccountKey.json from your Firebase project:

Go to Firebase Console

Project Settings > Service Accounts > Generate new private key

Then, place it in the root folder of your project:

    /Firebase-Send-Notification-Server/
    └── serviceAccountKey.json

4. Start the Server

       node server.js

   If successful, you should see:

       🚀 FCM Notification Server running at http://localhost:3000

5. Upload the p.8 file in Apple Developer Account

API Usage

Endpoint: /send-notification
Method: POST
Content-Type: application/json

     {
    "token": "your_device_fcm_token_here",
    "title": "Hello!",
    "body": "This is a test notification",
    "data": {
      "route": "/profile-screen"
    }
    }

Flutter Setup (Client)

Ensure you have added these packages in your pubspec.yaml:

     firebase_core: ^latest
     firebase_messaging: ^latest

In your Flutter main.dart:

    FirebaseMessaging messaging = FirebaseMessaging.instance;

    String? token = await messaging.getToken();
    print("FCM Token: $token");

Testing

Run your Flutter app to fetch the FCM token.

Call the Node.js /send-notification endpoint with the token and a route.

When the notification is received and tapped, the Flutter app should navigate to the specified screen.

Security Tips

DO NOT commit serviceAccountKey.json to your Git repo.

Add this to your .gitignore file:

    serviceAccountKey.json
    .env





