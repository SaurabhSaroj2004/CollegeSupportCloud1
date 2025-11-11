# College Support - Cloud-based Web App

A cloud-hosted web application for college students to find nearby local support services including hospitals, pharmacies, e-rickshaws, and food delivery services. Built with React, Tailwind CSS, and Firebase.

## Features

- 🔐 **Secure Authentication**: Email/password and Google Sign-In via Firebase Auth
- 📍 **Service Discovery**: Search and filter nearby services by category
- ✅ **Verified Listings**: Admin-verified service information
- 👤 **User Profiles**: Manage personal information and preferences
- 🛡️ **Admin Dashboard**: Review and approve service submissions
- 📱 **Responsive Design**: Works seamlessly on desktop and mobile

## Tech Stack

- **Frontend**: React + Vite + TypeScript
- **Styling**: Tailwind CSS + shadcn/ui
- **Backend**: Firebase (Firestore, Auth, Storage)
- **Routing**: Wouter
- **State Management**: TanStack Query

## Prerequisites

- Node.js 20+ installed
- A Firebase account
- Git (optional)

## Firebase Setup Instructions

Before running the application, you need to set up Firebase:

### 1. Create a Firebase Project

1. Go to [Firebase Console](https://console.firebase.google.com)
2. Click "Add project" or "Create a project"
3. Name your project: `college-support-app` (or your preferred name)
4. Follow the setup wizard (Google Analytics is optional)

### 2. Enable Firebase Services

#### Authentication
1. In Firebase Console, go to **Build > Authentication**
2. Click "Get started"
3. Enable **Email/Password** sign-in method
4. Enable **Google** sign-in method
   - Add your project support email
   - Save

#### Firestore Database
1. Go to **Build > Firestore Database**
2. Click "Create database"
3. Start in **Production mode**
4. Choose your Cloud Firestore location (preferably close to your users)
5. Click "Enable"

#### Storage (Optional - for future image uploads)
1. Go to **Build > Storage**
2. Click "Get started"
3. Start in **Production mode**
4. Use the same location as Firestore
5. Click "Done"

### 3. Get Firebase Configuration

1. In Firebase Console, go to **Project Settings** (gear icon)
2. Scroll down to "Your apps" section
3. Click the **Web** icon (`</>`) to register a web app
4. Register app with nickname: "College Support Web"
5. Copy the `firebaseConfig` object that appears

### 4. Configure Environment Variables

1. In the project root, create a `.env` file (copy from `.env.example`):
   ```bash
   cp .env.example .env
   ```

2. Open `.env` and fill in your Firebase credentials:
   ```env
   VITE_FIREBASE_API_KEY=your_api_key_here
   VITE_FIREBASE_AUTH_DOMAIN=your_project.firebaseapp.com
   VITE_FIREBASE_PROJECT_ID=your_project_id
   VITE_FIREBASE_STORAGE_BUCKET=your_project.appspot.com
   VITE_FIREBASE_MESSAGING_SENDER_ID=your_messaging_sender_id
   VITE_FIREBASE_APP_ID=your_app_id
   ```

### 5. Deploy Firestore Security Rules

1. In Firebase Console, go to **Firestore Database > Rules**
2. Replace the default rules with the content from `firestore.rules` in this project
3. Click "Publish"

### 6. Set Up Firestore Indexes (Optional but Recommended)

1. Go to **Firestore Database > Indexes**
2. Click "Add index" and create indexes based on `firestore.indexes.json`
3. Or wait for Firebase to suggest indexes as you use the app

### 7. Create an Admin User

After setting up Firebase and running the app:

1. Register a new user through the app
2. Go to Firebase Console > **Firestore Database**
3. Find the `users` collection
4. Locate your user document (by email)
5. Edit the document and set `role: "admin"`
6. Save the changes

Now you can access the Admin Dashboard!

## Installation & Running

1. **Install dependencies**:
   ```bash
   npm install
   ```

2. **Start the development server**:
   ```bash
   npm run dev
   ```

3. **Open your browser** and navigate to the URL shown in the terminal (typically `http://localhost:5000`)

## Project Structure

```
├── client/
│   ├── src/
│   │   ├── components/        # Reusable UI components
│   │   ├── lib/              # Firebase config & utilities
│   │   ├── pages/            # Page components
│   │   └── App.tsx           # Main app component
├── firestore.rules           # Firestore security rules
├── firestore.indexes.json    # Firestore indexes configuration
└── .env.example             # Environment variables template
```

## Available Pages

- `/` - Home page with hero and featured services
- `/listings` - Browse all services with filters
- `/service/:id` - Service detail page
- `/profile` - User profile management
- `/admin` - Admin dashboard (requires admin role)
- `/login` - Login/Register page

## Firestore Data Structure

### users Collection
```javascript
{
  name: "John Doe",
  email: "john@college.edu",
  phone: "+91 98765 43210",
  college: "ABC College",
  role: "user", // or "admin"
  createdAt: timestamp
}
```

### services Collection
```javascript
{
  type: "hospital", // or "pharmacy", "erickshaw", "food"
  name: "City Hospital",
  phone: "+91 98765 43210",
  address: "123 College Road",
  location: {
    lat: 26.7,
    lng: 88.4
  },
  openingHours: "24x7",
  notes: "Emergency available",
  createdBy: "<user_uid>",
  verified: true,
  createdAt: timestamp
}
```

## Security Rules Summary

- ✅ Anyone can read services (even unauthenticated)
- ✅ Users can read/write their own profile
- ✅ Only admins can create/verify services
- ✅ Users can only modify their own data

## Deployment (Optional)

### Firebase Hosting

1. Install Firebase CLI:
   ```bash
   npm install -g firebase-tools
   ```

2. Login to Firebase:
   ```bash
   firebase login
   ```

3. Initialize Firebase Hosting:
   ```bash
   firebase init hosting
   ```
   - Select your Firebase project
   - Set public directory to `dist`
   - Configure as single-page app: Yes
   - Don't overwrite index.html

4. Build the project:
   ```bash
   npm run build
   ```

5. Deploy:
   ```bash
   firebase deploy
   ```

## Troubleshooting

### Firebase not initialized
- Make sure you've created `.env` file with correct credentials
- Restart the development server after adding environment variables

### Can't access admin features
- Make sure you've set `role: "admin"` in Firestore for your user document

### Firestore permission denied
- Check that `firestore.rules` are deployed correctly
- Make sure you're authenticated when accessing protected data

## Support

For issues or questions:
- Check Firebase Console for errors
- Review browser console for client-side errors
- Verify Firestore rules are properly deployed

## License

MIT License - feel free to use this project for learning or production!

---

Built with ❤️ for college students
