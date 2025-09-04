# Blockchain_app

# Proyecto Blockchain - Registro de Revistas Depredadoras 🔗

Este proyecto implementa una red blockchain en **Hyperledger Fabric** para registrar y consultar revistas depredadoras.  
Forma parte del trabajo final de la materia **Fundamentos de Blockchain y Sistemas DLT**.

---

##  Descripción

La red permite registrar revistas académicas sospechosas o depredadoras en un **ledger inmutable**.  
Cada revista contiene los siguientes datos:

- **ID** (único para cada revista)  
- **Nombre**  
- **Editorial**  
- **País**  
- **Clasificación** (ejemplo: sospechosa, confirmada, depredadora)  
- **Fecha de registro**  

El chaincode (`revistas`) está desarrollado en **Go** y desplegado en un canal (`mychannel`) de la red Fabric.

---

##  Requisitos previos

Antes de clonar este repositorio asegúrate de tener instalado en tu máquina:

- [Docker](https://docs.docker.com/get-docker/)  
- [Docker Compose](https://docs.docker.com/compose/install/)  
- [Go](https://go.dev/doc/install) (para compilar chaincode)  
- [Hyperledger Fabric binaries](https://hyperledger-fabric.readthedocs.io/en/release-2.5/install.html)  

---

##  Instrucciones de uso

1. **Clonar el repositorio**  

   ```bash
   git clone https://github.com/DariethSV/blockchain_app.git
   cd blockchain_app

2. **Levantar la red de prueba**

   
