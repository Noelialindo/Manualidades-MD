rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    // Reglas para el catálogo de Manualidades MD
    match /catalog/{document=**} {
      // Cualquier persona (clientes) puede ver los trabajos, fotos y videos para ganar su confianza
      allow read: if true; 
      
      // Solo tú o usuarios autenticados (administradores) pueden agregar, modificar o actualizar fotos, videos y precios
      allow write: if request.auth != null; 
    }
  }
}
