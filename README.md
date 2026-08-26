rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /{document=**} {
      // Cualquier persona puede ver tus trabajos
      allow read: if true; 
      // Solo usuarios que hayan iniciado sesión pueden modificar los datos
      allow write: if request.auth != null; 
    }
  }
}
