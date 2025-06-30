# 🏡 Airbnb Clone – Backend System

Welcome to the backend of the **Airbnb Clone** project. This system powers key features like property listings, bookings, user management, secure payments, and admin operations — all built following clean architecture principles and third normal form (3NF) data design.

---

## 📌 Use Case Diagram

The following diagram illustrates key system interactions between users (guests, hosts, administrators) and the backend functionalities.



> 📎 Place the diagram image file in your project at: `docs/airbnb_usecase.png`  
> You can rename your image file `Gemini_Generated_Image_9s64189s64189s64.png` to `airbnb_usecase.png` and move it to the `docs/` folder to match this link.

---

## ✅ Key Use Cases & Mapped Features

| Actor           | Use Case                   | Backend Feature                        |
|----------------|-----------------------------|----------------------------------------|
| **Customer**    | Browse/Search Properties     | 🔎 Filtering + pagination              |
|                 | Book Property                | 📆 Booking management (dates, status) |
|                 | Manage Bookings              | View/edit/cancel bookings             |
|                 | Manage Account               | User profile management               |
|                 | Update Payments              | Connected to Stripe/PayPal logic      |
|                 | Leave Reviews                | ⭐ Linked to completed bookings        |
| **Property Owner** | Process Listing            | CRUD operations on listings           |
|                 | View Property                | Full listing details w/ images        |
|                 | Generate Reports             | Dashboard analytics                   |
| **Administrator** | Handle Customer Support    | View all users/bookings               |
|                 | Generate Reports             | System-wide metrics & activity logs   |
|                 | Manage Listings & Users      | Role-based access, RBAC secured       |

---

## ⚙️ Technical Stack

- **Language**: Node.js / Python (customizable)
- **Database**: PostgreSQL (3NF structure)
- **Authentication**: JWT, OAuth (Google)
- **Payment**: Stripe / PayPal (test-mode support)
- **API**: RESTful with proper status codes
- **Storage**: File system or AWS S3 for images
- **Testing**: Pytest / Jest (unit & integration)

---

## 📁 Project Structure

