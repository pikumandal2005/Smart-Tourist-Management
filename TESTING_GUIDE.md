# 🧪 Testing Guide - Tourist Safety Management System

## 📋 Pre-Testing Checklist

Before you begin testing, ensure:
- [ ] Firebase project is configured in `firebase-config.js`
- [ ] Firebase emulators are running (optional for local testing)
- [ ] `index.html` is opened in a modern browser (Chrome, Firefox, Edge)
- [ ] Browser console is open (F12) to see any errors

---

## 🔐 Authentication Testing

### Test 1: Signup Flow (Tourist)
**Steps:**
1. Open `index.html` in browser
2. Click "Sign up" link
3. Click "Tourist" role button
4. Fill in:
   - Full Name: "John Doe"
   - Email: "john@example.com"
   - Password: "test123456"
   - Confirm Password: "test123456"
5. Click "Create Account"

**Expected Result:**
- ✅ Success message appears
- ✅ Redirects to login page
- ✅ Email is pre-filled in login form
- ✅ User created in Firebase Authentication
- ✅ User data saved in Firestore `users` collection

**Validation Tests:**
- Try password < 6 characters → Should show error
- Try mismatched passwords → Should show error
- Try invalid email format → Should show error
- Try empty fields → Should show error

---

### Test 2: Signup Flow (Authority)
**Steps:**
1. Click "Sign up" link
2. Click "Authority" role button
3. Fill in form with valid data
4. Click "Create Account"

**Expected Result:**
- ✅ Authority account created successfully
- ✅ Role = "authority" saved in Firestore

---

### Test 3: Login Flow (Tourist)
**Steps:**
1. Enter tourist credentials:
   - Email: john@example.com
   - Password: test123456
2. Select "Tourist" role
3. Click "Login"

**Expected Result:**
- ✅ Redirects to Tourist Dashboard
- ✅ Shows safety score
- ✅ Shows quick action buttons
- ✅ Email displayed in header
- ✅ Logout button visible

**Error Cases:**
- Wrong password → Should show error
- Wrong role selected → Should show "Invalid credentials for selected role"
- Empty fields → Should show "Please enter email and password"

---

### Test 4: Login Flow (Authority)
**Steps:**
1. Enter authority credentials
2. Select "Authority" role
3. Click "Login"

**Expected Result:**
- ✅ Redirects to Authority Dashboard
- ✅ Shows statistics cards
- ✅ Shows live map
- ✅ Shows tourist list
- ✅ Shows alert section

---

### Test 5: Forgot Password Flow
**Steps:**
1. Click "Forgot Password?" link
2. Enter email: john@example.com
3. Click "Send Reset Link"

**Expected Result:**
- ✅ Success message: "Password reset email sent!"
- ✅ Email sent to user's inbox (check spam folder)
- ✅ Redirects to login page

**Validation Tests:**
- Empty email → Should show error
- Invalid email format → Should show error

---

## 👮 Authority Dashboard Testing

### Test 6: View Real-Time Statistics
**Steps:**
1. Login as authority
2. Observe statistics cards

**Expected Result:**
- ✅ "Active Tourists" shows count
- ✅ "Active Alerts" shows count
- ✅ "Incidents Today" shows count
- ✅ Numbers update in real-time when data changes

---

### Test 7: Live Tourist Map
**Steps:**
1. Observe the map on authority dashboard
2. Check for tourist markers

**Expected Result:**
- ✅ Map loads with OpenStreetMap tiles
- ✅ Tourist markers appear (if tourists are active)
- ✅ Markers are color-coded (green: safe, red: SOS)
- ✅ Clicking marker shows tourist info popup
- ✅ Map is interactive (zoom, pan)

---

### Test 8: Search Tourists
**Steps:**
1. Type tourist name/email in search box
2. Observe filtered results

**Expected Result:**
- ✅ Tourist list filters in real-time
- ✅ Only matching tourists are shown
- ✅ Case-insensitive search works

---

### Test 9: Filter Tourists by Status
**Steps:**
1. Select filter: "Active"
2. Select filter: "SOS Alert"
3. Select filter: "All Status"

**Expected Result:**
- ✅ Tourist list filters by selected status
- ✅ Combines with search filter
- ✅ Shows relevant tourists only

---

### Test 10: Export Tourist Data
**Steps:**
1. Click "📥 Export" button
2. Check downloads folder

**Expected Result:**
- ✅ CSV file downloads
- ✅ Filename: `tourists_YYYY-MM-DD.csv`
- ✅ Contains columns: Name, Email, Location, Status, Last Updated
- ✅ All visible tourists included in export

---

### Test 11: Broadcast Alert
**Steps:**
1. Enter alert title: "Heavy Rainfall Warning"
2. Enter message: "Stay indoors. Avoid low-lying areas."
3. Select severity: "High"
4. Click "Broadcast Alert"

**Expected Result:**
- ✅ Success message appears
- ✅ Alert saved in Firestore `alerts` collection
- ✅ Alert appears in "Recent Alerts" section
- ✅ All tourists receive the alert instantly

---

### Test 12: View Recent Alerts
**Steps:**
1. Observe "Recent Alerts" section
2. Check timestamps and severity levels

**Expected Result:**
- ✅ Shows last 10 alerts
- ✅ Displays timestamp for each alert
- ✅ Shows severity badge (color-coded)
- ✅ Updates in real-time when new alerts are broadcast

---

## 👤 Tourist Dashboard Testing

### Test 13: View Safety Score
**Steps:**
1. Login as tourist
2. Observe safety score section

**Expected Result:**
- ✅ Safety score displayed (0-100%)
- ✅ Color-coded indicator (green: high, yellow: medium, red: low)
- ✅ Message shows safety status

---

### Test 14: Send Emergency SOS
**Steps:**
1. Click "🚨 SOS" button
2. Allow location permission when prompted
3. Confirm SOS alert

**Expected Result:**
- ✅ Browser asks for location permission
- ✅ GPS coordinates captured
- ✅ SOS alert sent to Firestore
- ✅ Success message appears
- ✅ Authorities see SOS on dashboard
- ✅ Map marker turns red for this tourist

---

### Test 15: View Active Alerts
**Steps:**
1. Observe "Active Alerts" section
2. Wait for authority to broadcast an alert

**Expected Result:**
- ✅ Shows last 5 alerts
- ✅ Updates in real-time
- ✅ Displays timestamp and severity
- ✅ New alerts appear instantly

---

### Test 16: Add Itinerary Item
**Steps:**
1. Scroll to "My Itinerary" section
2. Enter place: "Taj Mahal"
3. Select date: Tomorrow's date
4. Select time: 10:00 AM
5. Click "➕ Add"

**Expected Result:**
- ✅ Success message appears
- ✅ Form fields clear
- ✅ New item appears in itinerary list
- ✅ Item saved in Firestore `itineraries` collection
- ✅ Shows place, date, time

**Validation:**
- Empty fields → Should show "Please fill all fields"

---

### Test 17: View Itinerary
**Steps:**
1. Observe itinerary list
2. Check sorting and formatting

**Expected Result:**
- ✅ All itinerary items displayed
- ✅ Sorted by date/time
- ✅ Shows place name, date, time
- ✅ Option to delete items (if implemented)

---

### Test 18: Find Nearby Hospitals
**Steps:**
1. Scroll to "Nearby Places" section
2. Select category: "🏥 Hospitals"
3. Click "🔍 Find"

**Expected Result:**
- ✅ Shows list of nearby hospitals
- ✅ Displays hospital name
- ✅ Shows distance from current location
- ✅ Shows phone number
- ✅ "Navigate" button available

---

### Test 19: Find Nearby Police Stations
**Steps:**
1. Select category: "🚔 Police Stations"
2. Click "🔍 Find"

**Expected Result:**
- ✅ Shows list of police stations
- ✅ Displays distance and phone number
- ✅ Includes emergency numbers

---

### Test 20: Find Tourist Spots
**Steps:**
1. Select category: "🏛️ Tourist Spots"
2. Click "🔍 Find"

**Expected Result:**
- ✅ Shows tourist attractions
- ✅ Displays ratings (★ stars)
- ✅ Shows distance

---

### Test 21: Find Restaurants
**Steps:**
1. Select category: "🍽️ Restaurants"
2. Click "🔍 Find"

**Expected Result:**
- ✅ Shows restaurant list
- ✅ Displays ratings and distance

---

### Test 22: View Safety Tips
**Steps:**
1. Click "📚 Safety Tips" quick action button
2. Read safety tips modal

**Expected Result:**
- ✅ Modal opens with safety tips
- ✅ Shows 5 sections:
  - General Safety (7 tips)
  - Emergency Contacts (6 numbers)
  - Health & Safety (6 tips)
  - Money & Valuables (5 tips)
  - In Case of Emergency (5 steps)
- ✅ Scrollable content
- ✅ "Close" button works

---

### Test 23: Toggle Location Tracking
**Steps:**
1. Check if location tracking is ON
2. Turn OFF location tracking
3. Turn ON location tracking

**Expected Result:**
- ✅ Location toggle button visible
- ✅ When ON: Location updates every 30 seconds
- ✅ When OFF: Location updates stop
- ✅ Status saved in Firestore

---

### Test 24: View Safety Information
**Steps:**
1. Click "📊 Safety Info" button
2. Observe safety metrics

**Expected Result:**
- ✅ Shows location safety percentage
- ✅ Shows crime rate
- ✅ Shows traffic safety
- ✅ Shows health facilities rating
- ✅ Color-coded badges (green: good, yellow: moderate, red: poor)

---

### Test 25: View Emergency Contacts
**Steps:**
1. Click "📞 Emergency" button
2. Check contact list

**Expected Result:**
- ✅ Shows Police (100)
- ✅ Shows Ambulance (102)
- ✅ Shows Fire Service (101)
- ✅ Shows Tourist Helpline (1363)
- ✅ Phone numbers are clickable (tel: links)

---

## 🔄 Real-Time Features Testing

### Test 26: Real-Time Alert Updates
**Steps:**
1. Open two browser windows
2. Login as authority in window 1
3. Login as tourist in window 2
4. Broadcast alert from authority window

**Expected Result:**
- ✅ Tourist window shows new alert instantly (no refresh needed)
- ✅ Alert appears in "Active Alerts" section
- ✅ Timestamp is correct

---

### Test 27: Real-Time Location Updates
**Steps:**
1. Login as tourist
2. Allow location tracking
3. Open authority dashboard in another window
4. Observe map in authority window

**Expected Result:**
- ✅ Tourist marker appears on map
- ✅ Location updates every 30 seconds
- ✅ Marker position changes when tourist moves

---

### Test 28: Real-Time Statistics
**Steps:**
1. Open authority dashboard
2. Have multiple tourists login/logout
3. Send SOS from tourist account

**Expected Result:**
- ✅ "Active Tourists" count updates
- ✅ "Active Alerts" count updates
- ✅ "Incidents Today" updates when SOS is sent
- ✅ Updates happen without page refresh

---

## 📱 Responsive Design Testing

### Test 29: Mobile View (< 480px)
**Steps:**
1. Open browser DevTools (F12)
2. Toggle device toolbar
3. Select iPhone SE or similar
4. Test all features

**Expected Result:**
- ✅ Single column layout
- ✅ Buttons are touch-friendly
- ✅ Forms are easy to fill
- ✅ Map is responsive
- ✅ No horizontal scrolling

---

### Test 30: Tablet View (768px)
**Steps:**
1. Select iPad or similar device
2. Test all features

**Expected Result:**
- ✅ Two-column grid layout
- ✅ Cards resize appropriately
- ✅ Map displays properly

---

### Test 31: Desktop View (> 768px)
**Steps:**
1. Test on full-screen desktop browser
2. Resize window

**Expected Result:**
- ✅ Three-column grid for authority dashboard
- ✅ Proper spacing and padding
- ✅ Map is large and interactive

---

## 🔒 Security Testing

### Test 32: Firestore Rules
**Steps:**
1. Try to access data without authentication
2. Try to access authority data as tourist
3. Try to modify other users' data

**Expected Result:**
- ✅ Unauthenticated users cannot read/write
- ✅ Tourists cannot access authority-only data
- ✅ Users can only modify their own data
- ✅ Role-based access control works

---

### Test 33: Authentication State
**Steps:**
1. Login and refresh page
2. Close and reopen browser
3. Try to access dashboards without login

**Expected Result:**
- ✅ User stays logged in after refresh
- ✅ Session persists across browser restarts
- ✅ Cannot access dashboards without authentication
- ✅ Automatic redirect to login if not authenticated

---

## 🚨 Error Handling Testing

### Test 34: Network Errors
**Steps:**
1. Disconnect internet
2. Try to login
3. Try to send alert
4. Try to add itinerary

**Expected Result:**
- ✅ User-friendly error messages
- ✅ No app crashes
- ✅ Operations retry when connection restored

---

### Test 35: Invalid Data
**Steps:**
1. Enter invalid email formats
2. Enter very short passwords
3. Leave required fields empty

**Expected Result:**
- ✅ Validation errors shown
- ✅ Form submission blocked
- ✅ Clear error messages

---

## ✅ Test Results Template

Copy this to track your testing:

```
## Test Results - [Date]

### Authentication (Tests 1-5)
- [ ] Signup (Tourist) - PASS/FAIL
- [ ] Signup (Authority) - PASS/FAIL
- [ ] Login (Tourist) - PASS/FAIL
- [ ] Login (Authority) - PASS/FAIL
- [ ] Forgot Password - PASS/FAIL

### Authority Dashboard (Tests 6-12)
- [ ] Statistics - PASS/FAIL
- [ ] Live Map - PASS/FAIL
- [ ] Search Tourists - PASS/FAIL
- [ ] Filter Tourists - PASS/FAIL
- [ ] Export Data - PASS/FAIL
- [ ] Broadcast Alert - PASS/FAIL
- [ ] View Alerts - PASS/FAIL

### Tourist Dashboard (Tests 13-25)
- [ ] Safety Score - PASS/FAIL
- [ ] Emergency SOS - PASS/FAIL
- [ ] Active Alerts - PASS/FAIL
- [ ] Add Itinerary - PASS/FAIL
- [ ] View Itinerary - PASS/FAIL
- [ ] Find Hospitals - PASS/FAIL
- [ ] Find Police - PASS/FAIL
- [ ] Find Tourist Spots - PASS/FAIL
- [ ] Find Restaurants - PASS/FAIL
- [ ] Safety Tips - PASS/FAIL
- [ ] Location Tracking - PASS/FAIL
- [ ] Safety Information - PASS/FAIL
- [ ] Emergency Contacts - PASS/FAIL

### Real-Time Features (Tests 26-28)
- [ ] Real-Time Alerts - PASS/FAIL
- [ ] Real-Time Location - PASS/FAIL
- [ ] Real-Time Statistics - PASS/FAIL

### Responsive Design (Tests 29-31)
- [ ] Mobile View - PASS/FAIL
- [ ] Tablet View - PASS/FAIL
- [ ] Desktop View - PASS/FAIL

### Security & Errors (Tests 32-35)
- [ ] Firestore Rules - PASS/FAIL
- [ ] Authentication State - PASS/FAIL
- [ ] Network Errors - PASS/FAIL
- [ ] Invalid Data - PASS/FAIL

**Overall Status:** PASS / FAIL  
**Issues Found:** [List any bugs or issues]  
**Notes:** [Additional comments]
```

---

## 🎯 Test Coverage

**Total Tests:** 35  
**Critical Tests:** 20 (Must pass for production)  
**Optional Tests:** 15 (Nice to have)

**Testing Time:** ~2-3 hours for full suite

---

## 🐛 Bug Reporting Template

If you find bugs during testing:

```
**Bug Title:** [Short description]
**Test Number:** Test #X
**Severity:** Critical / High / Medium / Low
**Steps to Reproduce:**
1. [Step 1]
2. [Step 2]
3. [Step 3]

**Expected Result:** [What should happen]
**Actual Result:** [What actually happened]
**Browser:** [Chrome/Firefox/Safari version]
**Device:** [Desktop/Mobile/Tablet]
**Screenshots:** [Attach if available]
```

---

## 📞 Support

If you encounter issues during testing:
1. Check browser console for errors (F12)
2. Verify Firebase configuration
3. Ensure Firebase emulators are running (for local testing)
4. Check Firestore rules are deployed
5. Clear browser cache and try again

---

**Happy Testing! 🎉**
