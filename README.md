
# 🚗 Uni_Ride

**Uni_Ride** is a Flutter-based ride-sharing mobile application designed to help university students find and share rides with other students traveling to or from their university.

The application matches students based on their **trip direction, university, time, and location**, making it easier to find nearby students with similar transportation needs.

---

## 📱 About the Project

Finding transportation to university can sometimes be difficult or expensive, especially for students who travel at similar times every day.

**Uni_Ride** provides a simple solution by allowing students to:

* Enter their university trip information.
* Choose their trip direction.
* Select their preferred time.
* Use their location to find nearby students.
* Join a group with students who have similar trips.
* View their current ride group.
* Keep track of their previous rides.

---

## ✨ Features

### 🔐 Authentication

* User registration and login.
* Firebase Authentication.
* Google Sign-In support.
* Logout functionality.

### 🚘 Ride Requests

Users can create a ride request by providing:

* Name
* Phone number
* University
* Trip type
* Time
* Current location

### 👥 Group Matching

Uni_Ride automatically searches for students who have matching ride requests.

Students are matched based on:

* Same trip type
* Same university
* Same time
* Location within a specific distance

The application calculates the distance between users using their latitude and longitude.

### 📍 Location Matching

The application uses geographical coordinates to determine how close users are to each other.

Users within the defined matching distance can appear in the same ride group.

### 👥 My Group

Users can view the students currently matched with their ride request.

The group displays information such as:

* Student name
* University

### 📜 Ride History

Users can view their previous ride requests through the Ride History page.

### 🔄 Real-Time Updates

Ride data is stored in Firebase Cloud Firestore and retrieved using Firestore streams, allowing the group page to update when matching ride data changes.

### 🔃 Pull to Refresh

The group page supports pull-to-refresh so users can manually refresh the displayed ride information.

---

## 🛠️ Technologies Used

* **Flutter**
* **Dart**
* **Firebase Authentication**
* **Cloud Firestore**
* **Geolocator**
* **Provider / MVVM architecture** where applicable
* **Material Design**

---

## 🔥 Firebase

Uni_Ride uses Firebase for authentication and data storage.

### Firebase Authentication

Used for:

* User registration
* Login
* Google authentication
* Logout

### Cloud Firestore

Ride requests are stored in the:

```text
ride_requests
```

collection.

Each ride request contains information such as:

```text
userId
userName
latitude
longitude
university
tripType
time
createdAt
```

---

## 📍 Ride Matching Logic

When a user opens the **My Group** page, the application searches Firestore for ride requests that have:

```text
Same trip type
Same university
Same time
```

After retrieving the matching requests, the application calculates the distance between the current user and each matching user.

The distance is calculated using:

```dart
Geolocator.distanceBetween()
```

Users who are within the allowed distance are added to the group.

The results are then sorted from the nearest user to the farthest user.

The application currently displays up to:

```text
3 matching users
```

---

## 📂 Project Structure

A simplified project structure:

```text
lib/
│
├── main.dart
│
├── auth.dart
├── rideinfo.dart
├── history.dart
├── group_page.dart
├── app_theme.dart
│
├── models/
│   ├── ride_model.dart
│   ├── ride_service.dart
│   └── findgroups.dart
│
└── ...
```

### Important Files

| File                | Purpose                                 |
| ------------------- | --------------------------------------- |
| `main.dart`         | Application entry point                 |
| `auth.dart`         | Authentication and login                |
| `rideinfo.dart`     | Creating ride requests                  |
| `group_page.dart`   | Displaying the user's ride group        |
| `history.dart`      | Displaying ride history                 |
| `ride_model.dart`   | Ride request data model                 |
| `ride_service.dart` | Firestore operations and matching logic |
| `findgroups.dart`   | Distance calculation                    |
| `app_theme.dart`    | Application theme and colors            |

---

## 🚀 Getting Started

### 1. Clone the Repository

```bash
git clone YOUR_REPOSITORY_URL
```

### 2. Open the Project

```bash
cd uni_ride
```

### 3. Install Dependencies

```bash
flutter pub get
```

### 4. Configure Firebase

Create a Firebase project and connect it to the Flutter application.

Enable:

* Firebase Authentication
* Email/Password Authentication
* Google Sign-In
* Cloud Firestore

Make sure the Firebase configuration files are correctly added to the project.

### 5. Run the Application

```bash
flutter run
```

---

## 🗃️ Firestore Structure

The main Firestore collection is:

```text
ride_requests
```

Example document:

```text
ride_requests
│
└── document_id
    ├── userId: "user123"
    ├── userName: "Sura"
    ├── latitude: 32.581577
    ├── longitude: 35.844351
    ├── university: "Jordan University of Science and Technology"
    ├── tripType: "Go to uni"
    ├── time: "8 AM"
    └── createdAt: Timestamp
```

---

## 🎯 Project Goal

The main goal of Uni_Ride is to provide university students with a simple way to discover nearby students who have similar transportation needs and potentially share rides.

This can help students find suitable ride groups based on their university schedule and location.

---

## 🔮 Future Improvements

Possible future features include:

* 💬 In-app chat between group members
* ⭐ Rating and review system
* 🔔 Notifications for new matching rides
* 🗺️ Interactive map
* 🚗 Driver and passenger roles
* 📍 Live location sharing
* 🔒 Improved privacy and security
* 🧭 More advanced route matching
* 📅 Recurring university trips
* 👥 Larger and customizable ride groups

---

## 👩‍💻 Development

This project was developed as a Flutter application using Firebase services for authentication and cloud data management.

---

## 📄 License

This project is intended for educational and development purposes.
