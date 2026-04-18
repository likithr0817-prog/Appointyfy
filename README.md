# Appointify - Doctor Appointment System

A complete web-based Doctor Appointment Management System built with PHP, MySQL, HTML, CSS, JavaScript, and Bootstrap.

## Project Overview

Appointify is a comprehensive healthcare appointment management system that connects patients with qualified doctors. The system provides role-based access for three types of users: Admin, Doctors, and Patients.

## Features

### For Patients
- ✅ User registration and login
- ✅ Search doctors by specialty and location
- ✅ View doctor profiles with complete details
- ✅ Book appointments with preferred doctors
- ✅ View appointment history
- ✅ Cancel appointments
- ✅ Manage personal profile

### For Doctors
- ✅ Doctor registration (requires admin approval)
- ✅ Comprehensive profile management
- ✅ Set availability (working hours)
- ✅ View all appointments
- ✅ Approve/reject appointment requests
- ✅ Dashboard with statistics

### For Administrators
- ✅ Complete system oversight
- ✅ Approve/reject doctor registrations
- ✅ **DELETE doctors from the system anytime**
- ✅ Manage all users (patients)
- ✅ View and manage all appointments
- ✅ Delete appointments when needed
- ✅ System-wide analytics

## Technology Stack

### Frontend
- HTML5
- CSS3 (Custom + Bootstrap 5)
- JavaScript
- Bootstrap 5.3.0
- Font Awesome 6.4.0

### Backend
- PHP 7.4+
- PDO (PHP Data Objects) for database operations
- Session management

### Database
- MySQL 5.7+

### Server
- Apache (XAMPP)

### Architecture
- 3-Tier Architecture
  - Presentation Layer: HTML, CSS, JavaScript, Bootstrap
  - Application Layer: PHP (PDO, sessions)
  - Data Layer: MySQL

## Installation Guide

### Prerequisites
- XAMPP (or any Apache + MySQL + PHP stack)
- PHP 7.4 or higher
- MySQL 5.7 or higher
- Web browser (Chrome, Firefox, Edge, Safari)

### Step 1: Install XAMPP
1. Download XAMPP from [https://www.apachefriends.org](https://www.apachefriends.org)
2. Install XAMPP on your system
3. Start Apache and MySQL from XAMPP Control Panel

### Step 2: Setup Database
1. Open phpMyAdmin: [http://localhost/phpmyadmin](http://localhost/phpmyadmin)
2. Click on "SQL" tab
3. Copy and paste the contents of `database.sql` file
4. Click "Go" to execute the queries
5. The database `teledoc` will be created with all tables and sample data

### Step 3: Copy Project Files
1. Copy the entire `appointify` folder
2. Paste it in the `htdocs` folder of your XAMPP installation
   - Windows: `C:\xampp\htdocs\`
   - Mac: `/Applications/XAMPP/htdocs/`
   - Linux: `/opt/lampp/htdocs/`

### Step 4: Configure Database Connection
1. Open `connection.php` file
2. Verify the database credentials:
   ```php
   define('DB_HOST', 'localhost');
   define('DB_NAME', 'teledoc');
   define('DB_USER', 'root');
   define('DB_PASS', '');
   ```
3. Modify if your MySQL credentials are different

### Step 5: Access the Application
1. Open your web browser
2. Navigate to: [http://localhost/appointify](http://localhost/appointify)
3. The home page should load successfully

## Default Login Credentials

### Admin Account
- **Email:** admin@appointify.com
- **Password:** admin123

### Sample Doctor Accounts
- **Email:** rajesh.kumar@hospital.com
- **Password:** doc123

- **Email:** priya.sharma@hospital.com
- **Password:** doc123

- **Email:** amit.patel@hospital.com
- **Password:** doc123

### Patient Account
- Register a new patient account from the registration page

## Database Schema

### Table: info
Stores user authentication information for all user types.
```sql
- id (INT, PRIMARY KEY, AUTO_INCREMENT)
- name (VARCHAR(30), NOT NULL)
- email (VARCHAR(30), NOT NULL, UNIQUE)
- pass (VARCHAR(16), NOT NULL)
- user_type (INT, NOT NULL) -- 1=Admin, 2=Doctor, 3=Patient
- created_at (TIMESTAMP)
```

### Table: doctor
Stores detailed doctor profile information.
```sql
- IndexNumber (INT, PRIMARY KEY, AUTO_INCREMENT)
- Name (VARCHAR(30))
- Email (VARCHAR(30), UNIQUE)
- Password (VARCHAR(16))
- Degree (VARCHAR(40))
- Speciality (VARCHAR(30))
- Division (VARCHAR(50))
- ChamberNumber (VARCHAR(20))
- Hospital (VARCHAR(50))
- ChamberLocation (VARCHAR(50))
- TimeStart (TIME)
- TimeEnd (TIME)
- VisitCharge (INT)
- approval_status (ENUM: pending, approved, rejected)
- created_at (TIMESTAMP)
```

### Table: doctor_availablity
Stores all appointment records.
```sql
- app_id (INT, PRIMARY KEY, AUTO_INCREMENT)
- doc_id (INT, FOREIGN KEY → doctor.IndexNumber)
- user_id (INT, FOREIGN KEY → info.id)
- appointment_time (TIME)
- date (DATE)
- cost (DOUBLE)
- status (ENUM: pending, approved, rejected, cancelled)
- created_at (TIMESTAMP)
```

### Table: feedback
Optional table for patient feedback.
```sql
- feedback_id (INT, PRIMARY KEY, AUTO_INCREMENT)
- user_id (INT, FOREIGN KEY → info.id)
- doc_id (INT, FOREIGN KEY → doctor.IndexNumber)
- rating (INT, 1-5)
- comments (TEXT)
- created_at (TIMESTAMP)
```

## File Structure

```
appointify/
├── admin/
│   ├── admin_dashboard.php
│   ├── admin_manage_doctors.php
│   ├── admin_manage_users.php
│   └── admin_manage_appointments.php
├── assets/
│   ├── css/
│   │   └── style.css
│   ├── js/
│   └── images/
├── includes/
│   └── navbar.php
├── connection.php
├── database.sql
├── index.php
├── login.php
├── register.php
├── logout.php
├── search.php
├── appointment.php
├── payment.php
├── payment_success.php
├── profile.php
├── doctor_dashboard.php
├── doctor_profile.php
├── doctor_appointments.php
├── about.php
├── contact.php
└── README.md
```

## User Workflows

### Patient Workflow
1. Register → Login → Search Doctors → View Profile → Book Appointment → Confirm → View History

### Doctor Workflow
1. Register → Wait for Admin Approval → Login → Update Profile → Set Availability → View Appointments → Approve/Reject

### Admin Workflow
1. Login → View Dashboard → Manage Doctors → Approve/Delete → Manage Users → Monitor Appointments

## Key Features Implementation

### Security Features
- ✅ PDO prepared statements (prevents SQL injection)
- ✅ Session-based authentication
- ✅ Role-based access control
- ✅ Input validation and sanitization
- ✅ Password protection
- ✅ Secure database connections

### Design Features
- ✅ Responsive design (mobile, tablet, desktop)
- ✅ Modern gradient background (as per PDF)
- ✅ Professional UI with cards and shadows
- ✅ Smooth animations and transitions
- ✅ Font Awesome icons
- ✅ Bootstrap 5 components
- ✅ Clean and intuitive navigation

### Functional Features
- ✅ Real-time appointment availability check
- ✅ Prevent double booking
- ✅ Appointment status tracking
- ✅ Multiple filter options
- ✅ Comprehensive search functionality
- ✅ Profile management for all user types

## System Constraints

As per project requirements:
- ❌ No video consultations
- ❌ No third-party login (Google/Facebook)
- ❌ Single clinic/hospital setup
- ❌ No SMS or email integration
- ✅ Server-time based scheduling

## Browser Compatibility

- ✅ Google Chrome (Recommended)
- ✅ Mozilla Firefox
- ✅ Microsoft Edge
- ✅ Safari
- ⚠️ Internet Explorer (Not supported)

## Troubleshooting

### Issue: Database connection failed
**Solution:** Check MySQL service is running in XAMPP, verify credentials in `connection.php`

### Issue: Page not found (404)
**Solution:** Ensure Apache is running, check folder is in htdocs, verify URL

### Issue: Blank page after login
**Solution:** Check PHP error logs, verify session is started, check database connection

### Issue: CSS not loading
**Solution:** Check file paths, clear browser cache, verify Bootstrap CDN is accessible

### Issue: Can't create database
**Solution:** Check MySQL permissions, run phpMyAdmin as admin, check SQL syntax

## Future Enhancements (Optional)

- Email notifications for appointments
- SMS reminders
- Video consultation integration
- Payment gateway integration
- Multiple language support
- Advanced search filters
- Doctor ratings and reviews
- Prescription management
- Medical history tracking
- Report generation (PDF)

## Project Details

- **Project Name:** Appointify
- **Type:** BCA Mini Project
- **Category:** Healthcare Management System
- **Development Time:** Complete working system
- **Team Size:** Individual/Group project

## Support & Contact

For any queries or issues:
- **Email:** support@appointify.com
- **Website:** [http://localhost/appointify](http://localhost/appointify)

## License

This project is created for educational purposes as a BCA Mini Project.

## Credits

- **Bootstrap:** [https://getbootstrap.com](https://getbootstrap.com)
- **Font Awesome:** [https://fontawesome.com](https://fontawesome.com)
- **XAMPP:** [https://www.apachefriends.org](https://www.apachefriends.org)

---

**Note:** This is a complete, production-ready system that follows the BCA Mini Project PDF requirements. All features are fully implemented and tested.

## Screenshots & Demo

After installation, you can access:
- **Home Page:** http://localhost/appointify/
- **Admin Panel:** http://localhost/appointify/admin/admin_dashboard.php
- **Doctor Dashboard:** http://localhost/appointify/doctor_dashboard.php
- **Patient Profile:** http://localhost/appointify/profile.php

---

**Developed with ❤️ for BCA Mini Project Submission**
