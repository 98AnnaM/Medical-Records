# Medical-Records
REST API that handles the processes that concern patients' visits to doctors and keep track of the history of diseases. 

Entities:
- Doctor - has a name, birth date, a Set of Specialties (Pediatrics, Surgery, Cardiologist), and can be a general practitioner or not.
- Specialty - has name.
- Patient - has a name, can have or don't have health insurance and can have or don't have a GP (one of the doctors who is a GP).
- Diagnosis - has name.
- HealthSystem - holds the value of the fee that a patient has to pay when he/she visits a doctor.
- Visit - has a Patient, a Doctor, a Set of Diagnoses, a fee that must be paid (HealthSystem) and a visit date (LocalDate).  

A patient can be examined by a doctor. The doctor has to give one or more diagnoses the patient. When the patient visits the doctor there is a fee. If the patient has health insurance, he/she doesn't have to pay the fee otherwise, the patient has to pay the fee.

## DataBase Model

![image](https://github.com/98AnnaM/Medical-Records/assets/147516467/1032f0bc-f02d-4f73-bff1-6f0bc84d0592)

## Application functionalities

Patients:
- Getting all patients: GET request to `/patients`
- Getting information about specific patient (by patient id): GET request to `/patients/:id`
- Creating a new patient: POST request to `/patients`
  
  (request body should contain patient name, id of the GP and a boolean value, showing if the patient is insured)
- Editing an existing patient (by patient id): PUT request to `/patients/:id`

  (request body should contain patient name, id of the GP and a boolean value, showing if the patient is insured)
- Deleting an existing patient (by patient id): DELETE request to `/patients/:id`
- Get all patients with Insurance: GET request to `/patients/has-insurance`
- Get the percentage of patients without Insurance: GET request to `/patients/percent-without-insurance`

Doctors:
- Getting all doctors: GET request to `/doctors`
- Getting information about specific doctor (by doctor id): GET request to `/doctors/:id
- Creating a new doctor: POST request to `/doctors`

  (request body should contain doctor's name, birthdate, a set of specialties of the doctor and a boolean isGp, showing if the doctor is a GP or not)
- Editing an existing doctor (by doctor id): PUT request to `/doctors/:id`

  (request body should contain doctor's name, birthdate, a set of specialties of the doctor and a boolean isGp, showing if the doctor is a GP or not)
- Deleting an existing doctor (by doctor id): DELETE request to `/doctors/:id`

Visits:
- Getting all visits: GET request to `/visits`
- Getting information about specific visit (by visit id): GET request to `/visits/:id`
- Creating a new visit: POST request to `/visits`

  (request body should contain request body should contain id of the patient, id of the doctor, a set of diagnosis IDs and id of the HealthSystem)
- Editing an existing patient (by patient id): PUT request to `/visits/:id`

  (request body should contain request body should contain id of the patient, id of the doctor, a set of diagnosis IDs and id of the HealthSystem)
- Deleting an existing visit (by visit id): DELETE request to `/visits/:id`
- Get the total income from all visits: GET request to `/visits/total-income`
- Get the total income from the visits of a specific doctor (by the id of the doctor): GET request to `/visits/total-income-by-doctor/:doctorId`
- Get the count of visits of a specific patient (by the id of the patient): GET request to `/visits/count-visits-by-patient/:patientId`
- Get the count of visits with a specific diagnosis (by the id of the diagnosis): GET request to `/visits/count-visits-by-diagnosis/:diagnosisId`
- Get the count of doctors with income bigger than a specific value (by value of minIncome): GET request to `/visits/count-doctors-by-income/:minIncome`
- Get the total income from the visits with a specific diagnosis (by the id of the diagnosis): GET request to `/visits/total-income-by-diagnosis/:diagnosisId`
- Get the total income from the visits of patients without insurance: GET request to `/visits/total-income-by-patients-no-insurance`
- Get the total income from the visits to a specific doctor from insured patients (by the id of the doctor): GET request to `/visits/total-income-by-doctor-insured-patients/:doctorId`