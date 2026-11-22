## MySQL Database Design
### Patients Table Columns:
- ID: PRIMARY_KEY, UNIQUE, NOT_NULL, AUTO_INCREMENT
- NAME: CHAR, NOT_NULL
- AGE: INT, NOT_NULL
- EMAIL: EMAIL, NOT_NULL, UNIQUE
- PHONE: INT, NOT_NULL, UNIQUE
- APPOINTMENTS: INT, FOREIGN_KEY->appointment(id)

### Doctors table Columns:
- ID: PRIMARY_KEY, UNIQUE, NOT_NULL, AUTO_INCREMENT
- NAME: CHAR, NOT_NULL
- AVAILABILITY: DATETIME
- EMAIL: EMAIL, NOT_NULL, UNIQUE
- PHONE: INT, NOT_NULL, UNIQUE
- APPOINTMENTS: INT, FOREIGN_KEY->appointments(id)

## Appointments table
- ID: PRIMARY_KEY, UNIQUE, NOT_NULL, AUTO_INCREMENT
- TIME: DATETIME, NOT_NULL
- DOCTOR_ID: INT, FOREIGN_KEY->doctors(id), NOT_NULL
- PATIENT_ID: INT, FOREIGN_KEY->patients(id), NOT_NULL
- STATUS: INT (0 = Scheduled, 1 = Completed, 2 = Cancelled)
- PRESCRIPTION_ID: INT

The prescription_id will be linked to the id of a document stored in MongoDB.

## MongoDB Collection Design
### Collection: prescriptions
```json
{
  "_id": "ObjectId('64abc123456')",
  "patientName": "John Smith",
  "appointmentId": 51,
  "medication": "Paracetamol",
  "dosage": "500mg",
  "doctorNotes": "Take 1 tablet every 6 hours.",
  "refillCount": 2,
  "pharmacy": {
    "name": "Walgreens SF",
    "location": "Market Street"
  }
}
```
### feedback
```json
"_id": "ObjectId('dfderueirue454')",
"patientName":"John Smith",
"appointment_id": 50,
"Note": "The doctor was amazing"
"Rating" : 5
```
### logs
```json
"_id": "ObjectID('qeredf11')",
"dateTime": "21-11-2026 8:11:35",
"message": "login successful",
"user_name": "John Doe"
```

### Messages
```json
"_id": "ObjectID(dfd112ere)",
"DateTime":"21-11-2026 8:11:35",
"sender":"John Doe",
"recipient":"Dr Alex",
"message":"I would like to reschedule the appointment"
```


