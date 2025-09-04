<<<<<<< HEAD
# Blockchain_app
### Leidy Carolina Obando Figueroa - Darieth Farid Sanchez 
# Proyecto Blockchain - Registro de Revistas Depredadoras 

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
   
   ```bash
   ./network.sh up createChannel
   
3. **Desplegar el chaincode de revistas**
   
   ```bash
   ./network.sh deployCC -ccn revistas -ccp ../chaincode/revistas -ccl go

4. **Registrar una revista**
   
   ```bash
   ./network.sh cc invoke -C mychannel -ccn revistas -c '{"Args":["CrearRevista","rev1","Fake Journal of AI","Predatory Press","Nigeria","sospechosa","2025-09-04"]}'
   
5. **Consultar una revista por ID**
   
   ```bash
   peer chaincode query -C mychannel -n revistas -c '{"Args":["LeerRevista","rev1"]}'

  
=======
# Running the test network

You can use the `./network.sh` script to stand up a simple Fabric test network. The test network has two peer organizations with one peer each and a single node raft ordering service. You can also use the `./network.sh` script to create channels and deploy chaincode. For more information, see [Using the Fabric test network](https://hyperledger-fabric.readthedocs.io/en/latest/test_network.html). The test network is being introduced in Fabric v2.0 as the long term replacement for the `first-network` sample.

If you are planning to run the test network with consensus type BFT then please pass `-bft` flag as input to the `network.sh` script when creating the channel. This sample also supports the use of consensus type BFT and CA together.
That is to create a network use:
```bash
./network.sh up -bft
```

To create a channel use:

```bash
./network.sh createChannel -bft
```

To restart a running network use:

```bash
./network.sh restart -bft
```

Note that running the createChannel command will start the network, if it is not already running.

Before you can deploy the test network, you need to follow the instructions to [Install the Samples, Binaries and Docker Images](https://hyperledger-fabric.readthedocs.io/en/latest/install.html) in the Hyperledger Fabric documentation.

## Using the Peer commands

The `setOrgEnv.sh` script can be used to set up the environment variables for the organizations, this will help to be able to use the `peer` commands directly.

First, ensure that the peer binaries are on your path, and the Fabric Config path is set assuming that you're in the `test-network` directory.

```bash
 export PATH=$PATH:$(realpath ../bin)
 export FABRIC_CFG_PATH=$(realpath ../config)
```

You can then set up the environment variables for each organization. The `./setOrgEnv.sh` command is designed to be run as follows.

```bash
export $(./setOrgEnv.sh Org2 | xargs)
```

(Note bash v4 is required for the scripts.)

You will now be able to run the `peer` commands in the context of Org2. If a different command prompt, you can run the same command with Org1 instead.
The `setOrgEnv` script outputs a series of `<name>=<value>` strings. These can then be fed into the export command for your current shell.

## Chaincode-as-a-service

To learn more about how to use the improvements to the Chaincode-as-a-service please see this [tutorial](./test-network/../CHAINCODE_AS_A_SERVICE_TUTORIAL.md). It is expected that this will move to augment the tutorial in the [Hyperledger Fabric ReadTheDocs](https://hyperledger-fabric.readthedocs.io/en/release-2.4/cc_service.html)


## Podman

*Note - podman support should be considered experimental but the following has been reported to work with podman 4.1.1 on Mac. If you wish to use podman a LinuxVM is recommended.*

Fabric's `install-fabric.sh` script has been enhanced to support using `podman` to pull down images and tag them rather than docker. The images are the same, just pulled differently. Simply specify the 'podman' argument when running the `install-fabric.sh` script. 

Similarly, the `network.sh` script has been enhanced so that it can use `podman` and `podman-compose` instead of docker. Just set the environment variable `CONTAINER_CLI` to `podman` before running the `network.sh` script:

```bash
CONTAINER_CLI=podman ./network.sh up
````

As there is no Docker-Daemon when using podman, only the `./network.sh deployCCAAS` command will work. Following the Chaincode-as-a-service Tutorial above should work. 


>>>>>>> c30d7f1 (Proyecto blockchain de revistas depredadoras)
