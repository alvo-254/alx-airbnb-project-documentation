📑 Backend Feature Requirement Specifications
This section outlines detailed technical and functional requirements for core backend modules: User Authentication, Property Management, and the Booking System. Each includes API design, input/output, validation rules, and performance notes.

1. 🔐 User Authentication
✅ Feature Overview:
Allow users to register, log in, and access protected routes based on role (guest, host, admin).

🧠 Functional Requirements:
Register new users with unique email and hashed passwords.

Authenticate using JWT (JSON Web Tokens).

Protect private routes using middleware.

🧾 API Endpoints:
Method	Endpoint	Description
POST	/api/auth/register	Register a new user
POST	/api/auth/login	Authenticate and return token
GET	/api/auth/me	Get logged-in user info

🔢 Input / Output Specifications
POST /register

Input: { first_name, last_name, email, password, role }

Output: { user_id, token, message }

POST /login

Input: { email, password }

Output: { token, expires_in, user }

✅ Validation Rules:
Email must be valid and unique.

Password: minimum 8 characters, 1 uppercase, 1 number.

Role must be one of: guest, host, admin.

⚙️ Performance & Security:
Rate limit: max 5 login attempts per minute per IP.

Passwords stored with bcrypt hashing.

JWT tokens expire after 1 hour.

2. 🏡 Property Management
✅ Feature Overview:
Enable hosts to create, update, view, and delete property listings.

🧠 Functional Requirements:
CRUD operations for property data.

Listings linked to host user.

Images optionally uploaded to cloud/file storage.

🧾 API Endpoints:
Method	Endpoint	Description
POST	/api/properties	Add new property
GET	/api/properties	List all properties
GET	/api/properties/:id	Get property by ID
PUT	/api/properties/:id	Update property
DELETE	/api/properties/:id	Delete property

🔢 Input / Output Specifications
POST /properties

Input: { name, description, location, pricePerNight, amenities, images[] }

Output: { property_id, created_at }

✅ Validation Rules:
Price must be a positive decimal.

Name and description must not be empty.

Only hosts can create/edit/delete their own listings.

⚙️ Performance:
Listings paginated: 10 results per page.

Indexed by location and pricePerNight for faster search.

3. 📆 Booking System
✅ Feature Overview:
Allow guests to book properties for specific dates. Prevent overlapping bookings.

🧠 Functional Requirements:
Create, cancel, and view bookings.

Calculate total cost based on nights.

Track status (pending, confirmed, canceled).

🧾 API Endpoints:
Method	Endpoint	Description
POST	/api/bookings	Create booking
GET	/api/bookings	View user bookings
PUT	/api/bookings/:id/cancel	Cancel booking

🔢 Input / Output Specifications
POST /bookings

Input: { property_id, start_date, end_date }

Output: { booking_id, total_price, status }

✅ Validation Rules:
start_date must be before end_date.

No overlapping dates allowed for the same property.

Only guests can book; hosts cannot book their own property.

⚙️ Performance:
Conflict check via indexed date range queries.

Auto-cancel expired unconfirmed bookings every 24h (cronjob).

📌 Summary
Feature	Key APIs	Performance Focus
User Authentication	/api/auth/...	Secure, rate-limited login
Property Management	/api/properties/...	Paginated, indexed search
Booking System	/api/bookings/...	Conflict-free, async pricing

