@startuml
left to right direction
skinparam packageStyle rectangle

actor "Recepcionista" as Rec
actor "Veterinario" as Vet
actor "Administrador" as Admin

rectangle "Sistema VetSys" {
  usecase "Registrar Cliente y Mascota" as UC1
  usecase "Agendar Cita" as UC2
  usecase "Reprogramar Cita" as UC2_ext
  usecase "Registrar Consulta Médica" as UC3
  usecase "Consultar Historial Clínico" as UC4
  usecase "Emitir Receta" as UC5
  usecase "Gestionar Inventario" as UC6
  usecase "Gestionar Usuarios" as UC7
}

Rec --> UC1
Rec --> UC2
Rec --> UC2_ext
UC2_ext .> UC2 : <<extend>>

Vet --> UC3
Vet --> UC4
Vet --> UC5
UC3 ..> UC4 : <<include>>

Admin --> UC6
Admin --> UC7

@enduml