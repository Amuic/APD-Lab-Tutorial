# Multithreading în Java
## Crearea și folosirea thread-urilor în Java
În Java putem crea thread-uri în doua moduri:
- folosind clasa Thread
- folosind interfața Runnable
### Clasa Thread
Pentru a crea un thread, putem extinde clasa Thread, unde suprascriem metoda run, în care thread-ul execută toate operațiile asignate acestuia.
```java
class MyThread extends Thread {
    // date pe care le pasam thread-ului
    private int threadId; 

    public MyThread (int threadId) {
        this.threadId = threadId;
    }

    // aceasta metoda se apeleaza in mod automat
    @Override
    public void run() {
        System.out.println("Threadul nr. " + threadId + " asculta manele");
    }
}
```
### Interfața Runnable
```java
class MyRunnable implements Runnable {
    // date pe care le pasam thread-ului
    private int threadId;

    public MyRunnable (int threadId) {
        this.threadId = threadId;
    }

    // aceasta metoda se apeleaza in mod automat
    @Override
    public void run() {
        System.out.println("Threadul nr. " + threadId + " asculta manele");
    }
}
```
## Synchronized
Cu keyword-ul `synchronized` putem folosi lock-uri / mutecși în Java.

## Volatile
Cu ajutorul keyword-ului `volatile`, un thread poate vedea schimbările efectuate asupra unei variabile de către alt thread și să țină cont de aceste schimbări.

### Referințe - Java multithreading
[Concepte din Java multithreading explicate](http://tutorials.jenkov.com/java-concurrency/index.html)
