# 🏥 Hospital Management System (Java + MySQL)

[![Java](https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=java&logoColor=white)](https://java.com)
[![MySQL](https://img.shields.io/badge/MySQL-00000F?style=for-the-badge&logo=mysql&logoColor=white)](https://mysql.com)
[![JDBC](https://img.shields.io/badge/JDBC-007396?style=for-the-badge&logo=java&logoColor=white)](https://docs.oracle.com/javase/tutorial/jdbc/)

A comprehensive **Hospital Management System** built using **Java JDBC** and **MySQL** that streamlines patient registration, doctor management, and appointment scheduling with robust double-booking prevention.

---

## ✨ Key Features

### 👥 Patient Management
- **Add New Patients** - Register patients with complete details
- **View Patient Records** - Access comprehensive patient database
- **Patient Search** - Quick lookup of patient information

### 🩺 Doctor Management  
- **Doctor Directory** - View all available doctors
- **Specialization Filter** - Browse doctors by medical specialty
- **Availability Status** - Real-time doctor availability tracking

### 📅 Appointment System
- **Smart Booking** - Book appointments with automatic conflict detection
- **Double-Booking Prevention** - Ensures no scheduling conflicts for doctors
- **Date Validation** - Future-date only appointments
- **Appointment History** - Track all scheduled appointments

### 🛡️ Data Integrity
- **Foreign Key Constraints** - Maintains relational integrity
- **Input Validation** - Prevents invalid data entry
- **Transaction Management** - Ensures data consistency

---

## 🗄️ Database Schema

### Patients Table
```sql
CREATE TABLE patients (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    age INT NOT NULL,
    gender VARCHAR(10) NOT NULL
);
```

### Doctors Table  
```sql
CREATE TABLE doctors (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    specialization VARCHAR(100) NOT NULL
);
```

### Appointments Table
```sql
CREATE TABLE appointments (
    id INT AUTO_INCREMENT PRIMARY KEY,
    patient_id INT NOT NULL,
    doctor_id INT NOT NULL,
    appointment_date DATE NOT NULL,
    FOREIGN KEY (patient_id) REFERENCES patients(id),
    FOREIGN KEY (doctor_id) REFERENCES doctors(id)
);
```

### Sample Doctor Data
```sql
INSERT INTO doctors (name, specialization) VALUES
('Dr. Sharma', 'Cardiology'),
('Dr. Verma', 'Neurology'), 
('Dr. Singh', 'Orthopedics');
```

---

## 🚀 Quick Start Guide

### Prerequisites
- **Java JDK 8+** 
- **MySQL Server 5.7+**
- **MySQL Connector/J**

### Step 1: Database Setup
```sql
-- Create database
CREATE DATABASE hospital;
USE hospital;

-- Execute all table creation scripts above
-- Insert sample doctor data
```

### Step 2: Configuration
Update database credentials in `HospitalManagementSystem.java`:
```java
private static final String url = "jdbc:mysql://localhost:3306/hospital";
private static final String username = "root"; 
private static final String password = "your_mysql_password";
```

### Step 3: Compile & Run
```bash
# Compile the project
javac -d bin src/HospitalManagementSystem/*.java

# Run the application  
java -cp bin HospitalManagementSystem.HospitalManagementSystem
```

---

## 📱 User Interface

### Main Menu
```
🏥 HOSPITAL MANAGEMENT SYSTEM 🏥

1. Add Patient
2. View Patients  
3. View Doctors
4. Book Appointment
5. Exit

Enter your choice: 
```

### Sample Workflows

#### 1. Adding a Patient
```
Enter Patient Name: Raj Kumar
Enter Patient Age: 35  
Enter Patient Gender (M/F): M

✅ Patient added successfully! Patient ID: P1001
```

#### 2. Viewing Doctors
```
👨‍⚕️ AVAILABLE DOCTORS 👩‍⚕️

ID  Name          Specialization
1   Dr. Sharma    Cardiology
2   Dr. Verma     Neurology  
3   Dr. Singh     Orthopedics
```

#### 3. Booking Appointment
```
Enter Patient ID: 1
Enter Doctor ID: 2  
Enter Appointment Date (YYYY-MM-DD): 2024-01-15

✅ Appointment booked successfully!
```

---

## 🔧 Technical Architecture

### System Design
```
Java Application → JDBC Driver → MySQL Database
     ↑
Command Line Interface (CLI)
```

### Key Components
- **Database Layer** - MySQL with relational tables
- **Data Access Layer** - JDBC for database operations  
- **Business Logic Layer** - Appointment validation & conflict checking
- **Presentation Layer** - Console-based user interface

### Core Algorithms
```java
// Double-booking prevention
public boolean isDoctorAvailable(int doctorId, Date appointmentDate) {
    // Checks existing appointments for conflicts
}
```

---

## 📊 Sample Outputs

### Patient Registration
```
🆕 NEW PATIENT REGISTRATION
─────────────────────────────
Patient ID:    P1001
Name:          Raj Kumar
Age:           35
Gender:        Male
Status:        ✅ Registered Successfully
```

### Appointment Booking
```
📅 APPOINTMENT BOOKING
─────────────────────
Patient:       Raj Kumar (ID: P1001)  
Doctor:        Dr. Verma - Neurology
Date:          2024-01-15
Status:        ✅ Confirmed

❌ If doctor unavailable:
Status:        ⚠️ Doctor not available on selected date
```

---

## 🛠️ Troubleshooting

### Common Issues & Solutions

| Issue | Cause | Solution |
|-------|-------|----------|
| `ClassNotFoundException` | Missing MySQL connector | Add connector JAR to classpath |
| `Access denied` | Wrong DB credentials | Verify username/password |
| `Connection refused` | MySQL not running | Start MySQL service |
| `Foreign key violation` | Invalid patient/doctor ID | Check if IDs exist |

### Debug Mode
Enable detailed logging by modifying the connection URL:
```java
String url = "jdbc:mysql://localhost:3306/hospital?logger=Slf4JLogger&profileSQL=true";
```

---

## 📈 Future Enhancements

### 🎯 Planned Features
- [ ] **Web-based GUI** using JavaFX/Swing
- [ ] **Multi-user Login System** (Admin, Doctor, Patient)
- [ ] **Automated Email/SMS Notifications**
- [ ] **Medical Records Management**
- [ ] **Billing & Payment Integration**
- [ ] **Report Generation** (PDF/Excel)
- [ ] **REST API** for mobile apps
- [ ] **Real-time Notifications**

### 🔄 Integration Possibilities
- Pharmacy Management System
- Laboratory Information System  
- Insurance Claim Processing
- Telemedicine Module

---

## 🤝 Contributing

We welcome contributions! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 👨‍💻 Developer

**Your Name**  
- GitHub: [@your-username](https://github.com/your-username)
- Email: your.email@example.com

---

## 🆘 Support

If you encounter any issues or have questions:

1. Check the [Troubleshooting](#troubleshooting) section
2. Search existing [GitHub Issues](https://github.com/your-username/HospitalManagementSystem/issues)
3. Create a new issue with detailed description

---

<div align="center">

### ⭐ Don't forget to star this repository if you found it helpful!

**Built with ❤️ using Java & MySQL**

</div>
