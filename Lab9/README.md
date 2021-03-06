# Programarea distribuită în C - MPI
Până acum ați lucrat cu thread-uri în  C și Java.
## Tipuri de date în MPI
| Tipul de date în MPI | Tipul de date în C |
| -------------------- |:------------------:|
| MPI_SHORT            | short              |
| MPI_INT              | int                |
| MPI_LONG             | long               |
| MPI_LONG_LONG        | long long             |
| MPI_UNSIGNED_CHAR    | unsigned char          |
| MPI_UNSIGNED_SHORT   | un       |
| MPI_UNSIGNED         | long               |
## Funcții MPI
### Init - `MPI_Init(int *argc, char ***argv)`
- Construiește environment-ul în care procesele se vor rula
- De regulă se pasează ca argumente cele din linie din comandă (adică cele din `int main (int argc, char **argv)`)
### Finalize - `MPI_Finalize()`
- Se termină procesele.
### Comm_Size - `MPI_Comm_size(MPI_Comm comm, int *size)`
- Întoarce numărul de procese asociate cu un comunicator (de regulă MPI_COMM_WORLD)
- Exemplu: `MPI_Comm_size(MPI_COMM_WORLD, &tasks)`, unde tasks este numărul de procese
### Comm_Rank - `MPI_Comm_rank(MPI_Comm comm, int *rank)`
- Determină rangul / id-ul unui proces
- Exemplu: `MPI_Comm_rank(MPI_COMM_WORLD, &rank)`, unde rank este rangul / id-ul procesului
### Send - `MPI_Send(void* data, int count, MPI_Datatype datatype, int destination, int tag, MPI_Comm communicator)`
- Un proces-sursă trimite date unui proces-destinație.

- data = datele trimise
- count = numărul de date trimise
- datatype = tipul datelor trimise
- destination = id-ul procesului destinație
- tag = tag-ul mesajului trimis (adică al datelor trimise)
- communicator = comunicatorul (de regulă MPI_COMM_WORLD)
### Receive - `MPI_Recv(void* data, int count, MPI_Datatype datatype, int source, int tag, MPI_Comm communicator, MPI_Status* status)`
- Un proces-destinație primește date de la un proces-sursă.

- data = datele primite
- count = numărul de date primite
- datatype = tipul datelor primite
- destination = id-ul procesului sursă
- tag = tag-ul mesajului primit (adică al datelor primite)
- communicator = comunicatorul (de regulă MPI_COMM_WORLD)
- status = starea (de regulă se pune MPI_STATUS_IGNORE - se ignoră status-ul)
### Broadcast - `MPI_Bcast(void* data, int count, MPI_Datatype datatype, int root, MPI_Comm communicator)`
- Un proces trimite aceleași date tuturor proceselor din topologie (inclusiv lui însuși).

- data = datele trimise
- count = numărul de date trimise
- datatype = tipul datelor trimise
- root = id-ul procesului sursă
- communicator = comunicatorul (de regulă MPI_COMM_WORLD)
### Scatter - `MPI_Scatter(void* send_data, int send_count, MPI_Datatype send_datatype, void* recv_data, int recv_count, MPI_Datatype recv_datatype, int root, MPI_Comm communicator)`
- Un proces trimite câte o bucată dintr-un array / colecție tuturor proceselor în parte, inclusiv lui însuși (fiecare proces cu bucata sa din array).
- send_data = datele trimise
- send_datatype = tipul datelor trimise (de regulă recv_datatype == send_datatype)
- send_count = numărul de date trimise fiecărui proces în parte (de regulă recv_count == send_count)
- recv_data = datele primite
- recv_count = numărul de date primite de fiecare proces în parte (de regulă recv_count == send_count)
- recv_datatype = tipul datelor recepționate (de regulă recv_datatype == send_datatype)
- root = id-ul procesului sursă
- communicator = comunicatorul (de regulă MPI_COMM_WORLD)
### Gather - `MPI_Gather(void* send_data, int send_count, MPI_Datatype send_datatype, void* recv_data, int recv_count, MPI_Datatype recv_datatype, int root, MPI_Comm communicator)`
- Un proces primește câte o bucată dintr-un array / colecție de la toate procesele, inclusiv de la însuși (fiecare proces cu bucata sa din array) - reprezintă inversul lui Scatter.
- send_data = datele trimise
- send_datatype = tipul datelor trimise (de regulă recv_datatype == send_datatype)
- send_count = numărul de date trimise fiecărui proces în parte (de regulă recv_count == send_count)
- recv_data = datele primite
- recv_count = numărul de date primite de fiecare proces în parte (de regulă recv_count == send_count)
- recv_datatype = tipul datelor recepționate (de regulă recv_datatype == send_datatype)
- root = id-ul procesului destinație
- communicator = comunicatorul (de regulă MPI_COMM_WORLD)

## Utile
[Tutoriale MPI](https://mpitutorial.com/tutorials/)
