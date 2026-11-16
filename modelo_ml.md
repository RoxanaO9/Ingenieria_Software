@startuml
skinparam classAttributeIconSize 0

class Cliente {
  - idCliente: int
  - cedula: String
  - nombreCompleto: String
  - telefono: String
  - direccion: String
  - email: String
}

class Mascota {
  - idMascota: int
  - nombre: String
  - especie: String
  - raza: String
  - fechaNacimiento: Date
  - peso: double
  - sexo: String
}

class Veterinario {
  - idVeterinario: int
  - cedula: String
  - nombre: String
  - especialidad: String
  - numeroLicencia: String
}

class Cita {
  - idCita: int
  - fecha: Date
  - hora: Time
  - motivo: String
  - estado: String
}

class ConsultaMedica {
  - idConsulta: int
  - fechaHora: DateTime
  - motivo: String
  - diagnostico: String
  - observaciones: String
}

class Receta {
  - idReceta: int
  - indicaciones: String
  - dosis: String
  - duracionTratamiento: String
}

class Medicamento {
  - idMedicamento: int
  - nombre: String
  - descripcion: String
  - stock: int
  - precio: double
  - fechaVencimiento: Date
}

class MovimientoInventario {
  - idMovimiento: int
  - tipo: String
  - cantidad: int
  - fecha: DateTime
  - motivo: String
}

Cliente "1" -- "1..*" Mascota : posee >
Veterinario "1" -- "0..*" Cita : atiende >
Mascota "1" -- "0..*" Cita : agenda >
Cita "1" -- "0..1" ConsultaMedica : genera >
ConsultaMedica "1" -- "1..*" Receta : emite >
Receta "1..*" -- "1" Medicamento : contiene >
Medicamento "1" -- "0..*" MovimientoInventario : registra >

@enduml