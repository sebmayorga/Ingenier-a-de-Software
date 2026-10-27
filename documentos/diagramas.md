
---
config:
  theme: base
  look: classic
  fontFamily: '''Inter Variable'', sans-serif'
---
flowchart TD
rec([Recepcionista])
vet([Veterinario])
sis[Sistema de la clinica]
lab[Laboratorio externo]
pago[Pasarela de pagos]
rec -->|agenda y cobra| sis
vet -->|consulta expedientes| sis
sis -->|envia estudios| lab
sis -->|cobra consultas| pago


---
config:
  layout: elk
  theme: base
---
flowchart TD
rec([Recepcionista])
subgraph sistema[Sistema de la clinica]
web[App web<br/>React]
api[API<br/>Node.js]
db[(Base de datos<br/>PostgreSQL)]
end
lab[Laboratorio externo]
rec -->|usa| web
web -->|HTTPS/JSON| api
api -->|lee y escribe| db
api -->|SFTP| lab

