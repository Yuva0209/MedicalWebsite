# Welcome to Your Miaoda Project
Miaoda Application Link URL
    URL:https://medo.dev/projects/app-9yufcmrw4oap

# MediSecure - Role-Based Authentication & Access Control System

A comprehensive healthcare authentication system built with React, TypeScript, Supabase, and shadcn/ui. Features role-based access control with five distinct user roles and complete healthcare management functionality including appointments, prescriptions, and medical records.

## 🚀 Features

### Authentication & Security
- **Secure Authentication**: Username-based authentication powered by Supabase Auth
- **Password Security**: Automatic password hashing with bcrypt (handled by Supabase)
- **JWT Tokens**: Token-based session management with automatic expiry
- **Account Locking**: Automatic account lock after 5 failed login attempts (5-minute lockout)
- **Failed Login Tracking**: Real-time monitoring of failed login attempts
- **Account Activation/Deactivation**: Admins can activate or deactivate user accounts
- **Role-Based Access Control**: Five distinct user roles with differentiated permissions
- **Self-Service Registration**: Users select their role during signup
- **Audit Logging**: Comprehensive logging of all security events and user actions

### Core Healthcare Features
- **📅 Appointment Management**: Schedule, confirm, and manage patient appointments
- **💊 Prescription System**: Create and track patient prescriptions
- **📋 Medical Records**: Comprehensive patient medical history management
- **👥 User Management**: Complete user directory and role management
- **📊 Analytics Dashboard**: Real-time statistics and reporting

### User Roles & Permissions

#### 👨‍💼 Admin
- Full system access and oversight
- **User Management**: Create, view, and manage all users
- **Role Assignment**: Modify user roles
- **Account Control**: Activate/deactivate user accounts
- **Security Dashboard**: View security statistics and metrics
- **Audit Logs**: Access complete system audit trail
- **Failed Login Monitoring**: Track failed login attempts
- **Unauthorized Access Tracking**: Monitor unauthorized access attempts
- Cannot modify their own role (security measure)
- Complete access to all features

#### 👨‍⚕️ Doctor
- **Patient Records**: Create, view, and update medical records
- **Appointments**: View and manage their appointments
- **Prescriptions**: Write and manage prescriptions
- **Patient List**: Access to all patient information
- **Dashboard**: Statistics showing total records, patients, appointments, and prescriptions
- **Today's Schedule**: Quick view of today's appointments with status management

#### 📋 Administrative Staff
- **System Overview**: Comprehensive dashboard with statistics
- **User Management**: View all users and their roles
- **Appointments**: Monitor all appointments across the system
- **Records Access**: View all patient records (read-only)
- **Reporting**: User distribution and appointment status analytics
- **Activity Monitoring**: Track recent system activity

#### 🏥 Receptionist
- **Appointment Scheduling**: Book appointments for patients
- **Check-in Management**: Manage patient check-ins and appointment status
- **User Directory**: Search and view all registered users
- **Today's Schedule**: View and manage today's appointments
- **Patient Registration**: Access to patient information
- **Front Desk Operations**: Complete reception desk functionality

#### 🧑‍🦱 Patient
- **Medical Records**: View personal medical history
- **Appointments**: Book and view appointments
- **Prescriptions**: View active and past prescriptions
- **Profile Management**: View account details
- **Dashboard**: Personal health statistics
- **Secure Access**: Can only view own data

## 📋 Prerequisites

- Node.js 18+ and pnpm
- Supabase account (automatically configured)

## 🛠️ Installation

1. **Clone and Install Dependencies**
```bash
cd /workspace/app-9yufcmrw4oap
pnpm install
```

2. **Environment Setup**
The `.env` file is automatically configured with Supabase credentials.

3. **Database Setup**
The database schema is automatically created with:
- User profiles table with role management (5 roles)
- Patient records table
- Appointments table
- Prescriptions table
- Row Level Security (RLS) policies
- Helper functions for role checks

## 🎯 Usage

### Development

```bash
pnpm run dev
```

The application will be available at `http://localhost:5173`

### User Registration

**IMPORTANT**: The first user to register will automatically become an Admin, regardless of the role they select. This user can then manage other users if needed.

1. Navigate to the signup page
2. Enter your username and password
3. **Select your role** from the dropdown:
   - Patient (default)
   - Doctor
   - Administrative Staff
   - Receptionist
   - Admin
4. Complete registration
5. Sign in with your credentials
6. Access your role-specific dashboard

### Role-Specific Workflows

#### Doctor Workflow
1. Login as doctor
2. View today's appointments on dashboard
3. Create patient records with diagnosis and treatment
4. Write prescriptions for patients
5. Manage appointment status (confirm/complete)
6. Access complete patient history

#### Patient Workflow
1. Login as patient
2. View personal medical records
3. Book appointments with doctors
4. View active prescriptions
5. Check appointment status
6. Access profile information

#### Receptionist Workflow
1. Login as receptionist
2. View today's appointments
3. Schedule new appointments for patients
4. Check-in patients (update appointment status)
5. Search user directory
6. Manage front desk operations

#### Administrative Staff Workflow
1. Login as administrative staff
2. View system overview and statistics
3. Monitor all appointments
4. Access user reports
5. View patient records
6. Track system activity

## 📱 Application Structure

### Pages

- **Home Page** (`/`): Landing page with feature overview
- **Login Page** (`/login`): User authentication
- **Signup Page** (`/signup`): New user registration with role selection
- **Admin Dashboard** (`/admin`): User management and system overview
- **Doctor Dashboard** (`/doctor`): Patient care management with appointments, records, and prescriptions
- **Administrative Staff Dashboard** (`/administrative-staff`): System overview and comprehensive reporting
- **Receptionist Dashboard** (`/receptionist`): Appointment scheduling and user directory
- **Patient Dashboard** (`/patient`): Personal medical records and appointment booking
- **403 Forbidden** (`/403`): Access denied page

### Key Components

- **Navbar**: Responsive navigation with role-based menu items
- **RouteGuard**: Protected routes with role verification
- **AuthContext**: Global authentication state management
- **Tabs**: Organized content sections in dashboards
- **Forms**: React Hook Form integration for data entry
- **Dialogs**: Modal windows for creating appointments, records, and prescriptions

## 🔒 Security Features

### Authentication Security
- **Password Hashing**: Automatic bcrypt hashing via Supabase Auth
- **JWT Authentication**: Secure token-based authentication with 1-hour expiry
- **Account Locking**: Automatic 5-minute lock after 5 failed login attempts
- **Login Attempt Tracking**: Real-time monitoring of failed login attempts
- **Account Status Management**: Admins can activate/deactivate accounts
- **Session Management**: Secure session handling with automatic token refresh

### Audit Logging System
- **Comprehensive Logging**: All security events and user actions are logged
- **Login Tracking**: Success and failure login attempts
- **Unauthorized Access**: Logs all unauthorized access attempts
- **Record Updates**: Tracks all patient record modifications
- **User Creation**: Logs new user registrations
- **Audit Trail**: Complete audit trail with user ID, role, action, status, and timestamp

### Database Security
- **Row Level Security (RLS)**: Enforced at database level
- **Role-based Policies**: Different access levels per role
- **Helper Functions**: Prevent infinite recursion in policies
- **Secure Triggers**: Automatic user profile synchronization with role metadata
- **Data Isolation**: Patients can only access their own data
- **Last Updated By**: Tracks who last modified each record

### Application Security
- **Protected Routes**: Role-based route guards with unauthorized access logging
- **Token Management**: Automatic token refresh
- **Secure Password Storage**: Never stored in plain text
- **Input Validation**: Client and server-side validation
- **Permission Checks**: Every action verified against user role
- **403 Error Handling**: Proper unauthorized access responses

## 🗄️ Database Schema

### Profiles Table
```sql
- id (uuid, primary key)
- email (text)
- username (text, unique)
- full_name (text)
- role (enum: admin, doctor, administrativestaff, receptionist, patient)
- created_at (timestamp)
- updated_at (timestamp)
```

### Patient Records Table
```sql
- id (uuid, primary key)
- patient_id (uuid, foreign key)
- diagnosis (text)
- treatment (text)
- notes (text)
- doctor_id (uuid, foreign key)
- last_updated_by (uuid, foreign key) -- Tracks who last modified the record
- created_at (timestamp)
- updated_at (timestamp)
```

### Appointments Table
```sql
- id (uuid, primary key)
- patient_id (uuid, foreign key)
- doctor_id (uuid, foreign key, nullable)
- appointment_date (timestamptz)
- duration_minutes (int, default 30)
- status (enum: scheduled, confirmed, completed, cancelled)
- reason (text)
- notes (text)
- created_at (timestamp)
- updated_at (timestamp)
```

### Prescriptions Table
```sql
- id (uuid, primary key)
- patient_id (uuid, foreign key)
- doctor_id (uuid, foreign key)
- record_id (uuid, foreign key, nullable)
- medication_name (text)
- dosage (text)
- frequency (text)
- duration (text)
- instructions (text)
- status (enum: active, completed, cancelled)
- prescribed_date (timestamptz)
- created_at (timestamp)
- updated_at (timestamp)
```

### Audit Logs Table
```sql
- id (uuid, primary key)
- user_id (uuid, foreign key, nullable)
- user_role (text)
- action (text) -- e.g., login, logout, create_patient_record, unauthorized_access
- resource_type (text) -- e.g., profile, patient_record, appointment
- resource_id (uuid, nullable)
- status (enum: success, failure, unauthorized)
- ip_address (text, nullable)
- user_agent (text, nullable)
- details (jsonb) -- Additional context about the action
- created_at (timestamp)
```

## 🎨 Design System

The application uses a professional healthcare-themed design with:
- **Primary Color**: Medical blue (#0891b2)
- **Responsive Design**: Mobile-first approach
- **Dark Mode**: Full dark mode support
- **Accessible**: WCAG AA compliant color contrasts
- **Modern UI**: shadcn/ui components with Tailwind CSS

## 📊 API Functions

All database operations are encapsulated in `/src/db/api.ts`:

### Profiles
- `getAllProfiles()`: Fetch all user profiles
- `getProfileById(id)`: Get specific user profile
- `updateProfileRole(userId, role)`: Change user role
- `getPatients()`: Get all users with patient role
- `getDoctors()`: Get all users with doctor role

### Patient Records
- `getAllPatientRecords()`: Fetch all patient records
- `getPatientRecordsByPatientId(patientId)`: Get patient-specific records
- `createPatientRecord(record)`: Create new medical record
- `updatePatientRecord(recordId, updates)`: Update existing record
- `deletePatientRecord(recordId)`: Delete medical record

### Appointments
- `getAllAppointments()`: Fetch all appointments
- `getAppointmentsByPatientId(patientId)`: Get patient's appointments
- `getAppointmentsByDoctorId(doctorId)`: Get doctor's appointments
- `createAppointment(appointment)`: Schedule new appointment
- `updateAppointment(appointmentId, updates)`: Update appointment
- `deleteAppointment(appointmentId)`: Cancel appointment

### Prescriptions
- `getAllPrescriptions()`: Fetch all prescriptions
- `getPrescriptionsByPatientId(patientId)`: Get patient's prescriptions
- `createPrescription(prescription)`: Create new prescription
- `updatePrescription(prescriptionId, updates)`: Update prescription

### Audit Logs
- `getAllAuditLogs(limit)`: Fetch audit logs with optional limit
- `logAuditEvent(event)`: Log a security or user action event

### Security
- `checkAccountLocked(userId)`: Check if account is locked
- `handleFailedLogin(userId)`: Handle failed login attempt
- `handleSuccessfulLogin(userId)`: Handle successful login
- `toggleUserActive(userId, isActive)`: Activate/deactivate user account
- `getSecurityStats()`: Get security statistics (locked accounts, failed logins, etc.)

## 🚢 Deployment

### Deploy to Render

1. **Create New Web Service**
   - Connect your repository
   - Select "Node" environment

2. **Configure Build Settings**
   ```
   Build Command: pnpm install && pnpm run build
   Start Command: pnpm run preview
   ```

3. **Environment Variables**
   Add these from your `.env` file:
   ```
   VITE_SUPABASE_URL=your_supabase_url
   VITE_SUPABASE_ANON_KEY=your_supabase_anon_key
   ```

4. **Deploy**
   - Click "Create Web Service"
   - Wait for deployment to complete
   - Access your application at the provided URL

### Deploy to Vercel

```bash
pnpm add -g vercel
vercel
```

Follow the prompts and add environment variables when requested.

### Deploy to Netlify

```bash
pnpm run build
```

Drag and drop the `dist` folder to Netlify, or use the Netlify CLI.

## 🧪 Testing the Application

### Test Scenario 1: Complete Doctor Workflow
1. Register as doctor
2. View today's appointments
3. Create a patient record
4. Write a prescription
5. Confirm an appointment
6. Complete an appointment

### Test Scenario 2: Patient Experience
1. Register as patient
2. Book an appointment
3. View medical records
4. Check prescriptions
5. View appointment status

### Test Scenario 3: Receptionist Operations
1. Register as receptionist
2. Schedule appointment for a patient
3. Check-in patient (confirm appointment)
4. Search user directory
5. View today's schedule

### Test Scenario 4: Administrative Oversight
1. Register as administrative staff
2. View system statistics
3. Monitor appointments
4. Review user distribution
5. Check recent activity

### Test Scenario 5: Admin Management
1. Register first user (becomes admin)
2. View all users
3. Change user roles
4. Monitor system activity

## 📝 Notes

- **First User**: Always becomes admin automatically (security feature)
- **Role Selection**: Users choose their role during signup
- **Role Changes**: Admin can modify roles after registration
- **Data Isolation**: Patients can only see their own data
- **Admin Protection**: Admins cannot change their own role
- **Secure by Default**: All routes are protected unless explicitly public
- **Real-time Updates**: Dashboard statistics update automatically

## 🆕 What's New

### Version 4.0 Updates - Security & Audit Enhancements
- ✅ **Account Locking**: Automatic 5-minute lock after 5 failed login attempts
- ✅ **Failed Login Tracking**: Real-time monitoring with attempt counter
- ✅ **Audit Logging System**: Comprehensive logging of all security events
- ✅ **Login/Logout Tracking**: All authentication events logged
- ✅ **Unauthorized Access Logging**: Tracks and logs unauthorized access attempts
- ✅ **Record Update Tracking**: Logs who last modified patient records
- ✅ **User Activation/Deactivation**: Admins can activate or deactivate accounts
- ✅ **Security Dashboard**: Real-time security statistics and metrics
- ✅ **Audit Log Viewer**: Admin interface to view all system audit logs
- ✅ **Account Status Management**: View locked and deactivated accounts
- ✅ **Enhanced Error Messages**: Detailed feedback on login failures

### Version 3.0 Updates
- ✅ **Appointment System**: Complete appointment scheduling and management
- ✅ **Prescription Management**: Doctors can write and track prescriptions
- ✅ **Enhanced Doctor Dashboard**: Tabs for appointments, records, and prescriptions
- ✅ **Enhanced Patient Dashboard**: Book appointments, view prescriptions, manage profile
- ✅ **Receptionist Appointment Scheduling**: Book appointments for patients
- ✅ **Administrative Staff Analytics**: Comprehensive system overview and reporting
- ✅ **Today's Schedule**: Quick view of today's appointments for doctors and receptionists
- ✅ **Status Management**: Update appointment status (scheduled → confirmed → completed)
- ✅ **Check-in System**: Receptionist can check-in patients
- ✅ **Prescription Tracking**: View active and completed prescriptions

### Version 2.0 Updates
- ✅ **Role Selection During Signup**: Users now select their role when creating an account
- ✅ **Two New Roles Added**: Administrative Staff and Receptionist
- ✅ **Administrative Staff Dashboard**: System overview with comprehensive statistics
- ✅ **Receptionist Dashboard**: User directory with search and check-in management
- ✅ **Enhanced Navigation**: Role-specific menu items for all five roles
- ✅ **Updated Database Schema**: Support for new roles with appropriate permissions
- ✅ **Improved Role Display**: Better formatting for "Administrative Staff" role name

## 🤝 Support

For issues or questions:
1. Check the console for error messages
2. Verify database policies in Supabase dashboard
3. Ensure environment variables are correctly set
4. Check user role assignments in Admin Dashboard
5. Verify appointment and prescription data in database

## 📄 License

Copyright 2026 MediSecure. All rights reserved.

---

Built with ❤️ using React, TypeScript, Supabase, and shadcn/ui
