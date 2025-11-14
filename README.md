# 🛡️ Smart Tourist Safety Management System

A **production-ready single-page application** for comprehensive tourist safety monitoring with separate interfaces for authorities and tourists, powered by Firebase.

## 🌟 Key Features

### 🔐 Authentication System
- **Login**: Secure email/password authentication with role-based access
- **Signup**: Create new accounts for tourists or authorities
- **Forgot Password**: Email-based password reset functionality
- **Form Validation**: Email format, password strength, and field validation

### 👮 Authority Dashboard
- **Real-time Statistics**: Active tourists, alerts, and incident counts
- **Live Tourist Map**: Interactive Leaflet map with real-time location tracking
- **Tourist Management**: Search, filter (by status), and export tourist data to CSV
- **Alert Broadcasting**: Send custom alerts with severity levels to all tourists
- **Incident Monitoring**: Track and respond to SOS alerts instantly

### 👤 Tourist Interface
- **Safety Score**: Personalized safety rating based on location
- **Emergency SOS**: One-click emergency alert with GPS coordinates
- **Itinerary Planner**: Add, view, and manage travel plans
- **Nearby Places**: Find hospitals, police stations, tourist spots, and restaurants
- **Safety Tips**: Comprehensive safety guidelines and emergency contacts
- **Active Alerts**: Real-time notifications from authorities
- **Location Tracking**: Toggle GPS tracking ON/OFF

## 🚀 Quick Start

### 1. Firebase Setup

1. Go to [Firebase Console](https://console.firebase.google.com/)

2. Create a new project```

3. Enable **Authentication** (Email/Password)┌─────────────────────────────────────────────────────────┐

4. Enable **Cloud Firestore**│                    Frontend Layer                        │

5. Enable **Storage**├──────────────────────┬──────────────────────────────────┤

6. Copy your Firebase config│   Admin Dashboard    │      Tourist Website            │

│   (Firebase Hosting) │      (GitHub Pages)              │

### 2. Update Configuration│   - React + Vite     │      - React + Vite              │

│   - Material-UI      │      - Material-UI               │

Open `index.html` and replace the Firebase configuration (around line 380):│   - Leaflet Maps     │      - Leaflet Maps              │

└──────────────────────┴──────────────────────────────────┘

```javascript                         ↓

const firebaseConfig = {┌─────────────────────────────────────────────────────────┐

    apiKey: "YOUR_API_KEY",│              Firebase Services (Backend)                 │

    authDomain: "YOUR_PROJECT_ID.firebaseapp.com",├─────────────────────────────────────────────────────────┤

    projectId: "YOUR_PROJECT_ID",│  • Authentication (Email/Password)                       │

    storageBucket: "YOUR_PROJECT_ID.appspot.com",│  • Firestore Database (Real-time NoSQL)                  │

    messagingSenderId: "YOUR_MESSAGING_SENDER_ID",│  • Storage (File uploads)                                │

    appId: "YOUR_APP_ID"│  • Security Rules (Role-based access control)            │

};│  • Firebase Hosting (Static site deployment)             │

```└─────────────────────────────────────────────────────────┘

```

### 3. Deploy Firestore Rules

### Key Design Decisions

```bash

firebase deploy --only firestore:rules- ❌ **No Cloud Functions** (avoids Blaze plan requirement)

firebase deploy --only storage:rules- ✅ **Client-Side Logic** (React handles all business logic)

```- ✅ **Firebase Security Rules** (database-level authorization)

- ✅ **Custom Claims** (JWT-based role management)

### 4. Create Test Users- ✅ **Firestore Real-Time** (live updates without polling)



In Firebase Console → Authentication, create users:## 📁 Project Structure



**Authority User:**```

- Email: `authority@demo.com`SIH-2025/

- Password: `password123`├── frontend/              # Admin Dashboard (Police/Tourism Dept)

│   ├── src/

**Tourist User:**│   │   ├── components/   # MapComponent, Layout, etc.

- Email: `tourist@demo.com`│   │   ├── pages/        # Dashboard, Tourists, Alerts, Incidents

- Password: `password123`│   │   ├── config/       # Firebase config

│   │   └── main.tsx      # App entry point

Then in Firestore, create documents:│   ├── index.html

│   ├── package.json

**users/authority-uid:**│   └── vite.config.ts

```json│

{├── tourist-site/          # Tourist-Facing Website

  "email": "authority@demo.com",│   ├── src/

  "role": "authority",│   │   ├── components/   # Layout, shared components

  "name": "Authority User"│   │   ├── pages/        # Home, Safety, Emergency, Profile

}│   │   ├── config/       # Firebase config

```│   │   └── main.tsx

│   ├── index.html

**users/tourist-uid:**│   ├── package.json

```json│   └── README.md

{│

  "email": "tourist@demo.com",├── firebase.json          # Firebase project configuration

  "role": "tourist",├── firestore.rules        # Database security rules

  "name": "Tourist User"├── firestore.indexes.json # Database indexes

}├── storage.rules          # File storage rules

```├── .firebaserc           # Firebase project ID

│

### 5. Deploy to GitHub Pages├── populate-sample-data.js # Script to add test data

├── set-admin-claims.js     # Script to set user roles

#### Method 1: Automatic (Recommended)│

├── README.md              # This file

1. Push code to GitHub├── DEPLOYMENT.md          # Deployment guide

2. Go to **Settings** → **Pages**└── ENVIRONMENT_SETUP.md   # Environment setup guide

3. Source: **GitHub Actions**```

4. The workflow will auto-deploy on every push

## 🚀 Quick Start

#### Method 2: Firebase Hosting

### Prerequisites

```bash

firebase login- Node.js v18+ & npm

firebase init hosting- Firebase CLI (`npm install -g firebase-tools`)

firebase deploy --only hosting- Git (for GitHub Pages deployment)

```- Firebase project created at https://console.firebase.google.com



Your site will be live at: `https://your-project.web.app`### 1. Firebase Setup



## 📁 Project Structure```bash

# Login to Firebase

```firebase login

SIH-2025/

├── index.html              # Single-page application# Link to your Firebase project

├── firebase.json           # Firebase configurationfirebase use --add

├── firestore.rules         # Firestore security rules

├── storage.rules           # Storage security rules# Start Firebase Emulators (for local development)

├── .github/firebase emulators:start

│   └── workflows/```

│       └── deploy.yml      # GitHub Actions workflow

└── README.md               # This fileEmulator UI will be available at http://localhost:4000

```

### 2. Admin Dashboard Setup

## 🔧 Local Testing

```bash

### Test with Live Server (VS Code)cd frontend



1. Install "Live Server" extension# Install dependencies

2. Right-click `index.html`npm install

3. Select "Open with Live Server"

# Create .env file

### Test with Python# Copy Firebase credentials from Firebase Console → Project Settings

VITE_FIREBASE_API_KEY=your_api_key

```bashVITE_FIREBASE_AUTH_DOMAIN=your_project.firebaseapp.com

python -m http.server 8000VITE_FIREBASE_PROJECT_ID=your_project_id

```VITE_FIREBASE_STORAGE_BUCKET=your_project.appspot.com

VITE_FIREBASE_MESSAGING_SENDER_ID=your_sender_id

Then open: `http://localhost:8000`VITE_FIREBASE_APP_ID=your_app_id



### Test with Firebase Emulators# Start development server

npm run dev

```bash```

firebase emulators:start

```Dashboard will open at http://localhost:3000



Update Firebase config to use emulators:### 3. Tourist Site Setup



```javascript```bash

// Add after firebase.initializeApp(firebaseConfig)cd tourist-site

if (location.hostname === "localhost") {

  auth.useEmulator("http://localhost:9099");# Install dependencies

  db.useEmulator("localhost", 8080);npm install

  storage.useEmulator("localhost", 9199);

}# Create .env file (use same Firebase credentials)

```# Copy the same values as admin dashboard



## 🌐 Live Demo# Start development server  

npm run dev

After deployment:```

- **GitHub Pages**: `https://yourusername.github.io/SIH-2025/`

- **Firebase Hosting**: `https://your-project.web.app`Tourist site will open at http://localhost:3001



## 🔐 Security### 4. Add Sample Data (Optional)



- Role-based access control (Authority vs Tourist)```bash

- Firestore security rules enforced server-side# Make sure Firebase emulators are running first!

- Storage rules for file uploadsnode populate-sample-data.js

- Authentication required for all features```



## 📊 Database CollectionsThis adds sample tourists, alerts, and incidents to test with.



### users### 5. Test the System

```json

{1. Open Emulator UI: http://localhost:4000

  "uid": "unique-id",2. Open Admin Dashboard: http://localhost:3000

  "email": "user@example.com",3. Login with test user (create one via the login page)

  "role": "tourist" | "authority",4. View the dashboard with sample data

  "name": "User Name"5. Check the map showing tourist locations

}

```## 🌐 Deployment



### tourists### Admin Dashboard (Firebase Hosting)

```json

{```bash

  "touristId": "uid",cd frontend

  "name": "Tourist Name",npm run build

  "country": "India",firebase deploy --only hosting

  "lastLocation": {```

    "latitude": 28.6139,

    "longitude": 77.2090Your dashboard will be live at `https://your-project-id.web.app`

  },

  "lastUpdated": "timestamp"### Tourist Website (GitHub Pages)

}

``````bash

cd tourist-site

### alertsnpm run build

```json

{# Push dist/ folder to GitHub

  "title": "Alert Title",# Enable GitHub Pages in repository settings

  "message": "Alert message",# Source: Deploy from a branch → main → /dist folder

  "severity": "low" | "medium" | "high",```

  "status": "active",

  "timestamp": "timestamp",Your site will be live at `https://your-username.github.io/tourist-safety/`

  "authorityId": "uid"

}## 🔒 Security

```

### Firebase Security Rules

### itinerary

```json- **Authentication Required**: All operations require user login

{- **Role-Based Access Control**: 

  "touristId": "uid",  - `admin` - Full access

  "location": "Location name",  - `police` / `tourism_dept` / `operator` - Read/write alerts, incidents, tourists

  "dateTime": "timestamp",  - `tourist` - Read own data, create alerts/incidents

  "notes": "Notes",- **Custom Claims**: Roles stored in JWT tokens

  "status": "planned" | "completed" | "cancelled"- **Client-Side Validation**: Rules enforced at database level

}

```## 📊 Features Breakdown



## 🎨 Customization### Admin Dashboard Features

- 📈 Real-time statistics (tourists, alerts, incidents)

### Change Colors- 🗺️ Interactive Leaflet map with tourist locations

- 👥 Tourist management (view, edit, track)

Edit the CSS gradient in `<style>` section:- 🚨 Alert system (create, resolve, monitor)

- 📝 Incident reports (E-FIR management)

```css- 📊 Analytics dashboard (trends)

background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);- ⚙️ Settings (geofence zones, notifications)

```

### Tourist Website Features

### Add More Features- 🏠 Home dashboard (safety status, quick actions)

- 🛡️ Safety score (real-time risk assessment)

The code is modular and easy to extend:- 🆘 Emergency button (one-click SOS)

- Add new sections in HTML- 🗺️ Interactive map (current location, safe zones)

- Create new functions in JavaScript- 📅 Itinerary tracker (plans with safety info)

- Add new Firestore collections- 👤 Profile management (details, emergency contacts)

- 🔔 Push notifications (alerts, warnings)

## 📱 Responsive Design

## 🧪 Testing

The application is fully responsive and works on:

- 📱 Mobile devices (375px+)### Local Testing with Emulators

- 📱 Tablets (768px+)

- 💻 Desktops (1920px+)```bash

# Start emulators

## 🐛 Troubleshootingfirebase emulators:start



### "Permission Denied" Error# View Emulator UI

- Check Firestore rules are deployedopen http://localhost:4000

- Verify user has correct role in `users` collection

# Test admin dashboard

### Map Not Loadingcd frontend && npm run dev

- Check internet connection (Leaflet requires CDN)

- Verify tourist has `lastLocation` in Firestore# Test tourist site

cd tourist-site && npm run dev

### Login Not Working```

- Ensure Firebase Authentication is enabled

- Check email/password in Firebase Console### Create Test Users

- Verify Firebase config is correct

```bash

## 💡 Tips# After creating a user through the UI, set their role:

node set-admin-claims.js admin@test.com admin

1. **Test Locally First**: Use emulators before deploying```

2. **Backup Data**: Export Firestore data regularly

3. **Monitor Usage**: Check Firebase Console for quotas**Note:** Requires downloading a service account key from Firebase Console

4. **Security**: Never commit Firebase API keys to public repos

## 📱 Mobile Responsiveness

## 📄 License

Both sites are fully mobile-responsive:

MIT License - Free to use for SIH 2025- Material-UI responsive grid system

- Touch-friendly UI components

## 🤝 Support- Mobile-first map interface

- Hamburger menu for small screens

For issues or questions:- PWA-ready architecture

1. Check Firebase Console logs

2. Review browser console errors## 🌍 Future Enhancements

3. Test with Firebase emulators

- [ ] PWA with offline support

---- [ ] Push notifications (FCM)

- [ ] Multilingual UI (i18n)

**Built for SIH 2025** 🇮🇳- [ ] Voice-activated SOS

- [ ] Machine learning safety predictions
- [ ] WhatsApp/Telegram bot integration

## 🤝 Contributing

This is a Smart India Hackathon 2025 project.

1. Fork the repository
2. Create a feature branch
3. Commit changes
4. Push to branch
5. Open a Pull Request

## 📄 License

Created for Smart India Hackathon 2025.

## 👥 Team

SIH 2025 Team

---

**Built with ❤️ for Smart India Hackathon 2025**
