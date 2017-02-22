---
title: "lock_when (Enumeraci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "msclr::lock_when"
  - "msclr.lock_when"
  - "lock_when"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "lock_when (enumeración)"
ms.assetid: 6b87bbe9-63cd-450d-a02e-bb91ffd0dcea
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# lock_when (Enumeraci&#243;n)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Especifica difirió el bloqueo.  
  
## Sintaxis  
  
```  
enum lock_when {  
   lock_later  
};  
```  
  
## Comentarios  
 Cuando se pasa a [lock::lock](../dotnet/lock-lock.md), `lock_later` especifica que el bloqueo no debería ser ahora tomado.  
  
## Ejemplo  
 Este ejemplo utiliza una sola instancia de una clase a través de varios subprocesos.  La clase utiliza un bloqueo en sí misma para garantizar que los accesos a sus datos internos son coherentes para cada subproceso.  El subproceso de aplicación principal utiliza un bloqueo en la misma instancia de la clase compruebe periódicamente para ver si todavía existen algunos subprocesos de trabajo, y espera para salir hasta que todos los subprocesos de trabajo completen sus tareas.  
  
```  
// msl_lock_lock_when.cpp  
// compile with: /clr  
#include <msclr/lock.h>  
  
using namespace System;  
using namespace System::Threading;  
using namespace msclr;  
  
ref class CounterClass {  
private:  
   int Counter;     
  
public:  
   property int ThreadCount;  
  
   // function called by multiple threads, use lock to keep Counter consistent  
   // for each thread  
   void UseCounter() {  
      try {  
         lock l(this); // wait infinitely  
  
         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,   
            Counter);  
  
         for (int i = 0; i < 10; i++) {  
            Counter++;  
            Thread::Sleep(10);  
         }  
  
         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,   
            Counter);  
  
         Counter = 0;  
         // lock is automatically released when it goes out of scope and its destructor is called  
      }  
      catch (...) {  
         Console::WriteLine("Couldn't acquire lock!");  
      }  
  
      ThreadCount--;  
   }  
};  
  
int main() {  
   // create a few threads to contend for access to the shared data  
   CounterClass^ cc = gcnew CounterClass;  
   array<Thread^>^ tarr = gcnew array<Thread^>(5);  
   ThreadStart^ startDelegate = gcnew ThreadStart(cc, &CounterClass::UseCounter);  
   for (int i = 0; i < tarr->Length; i++) {  
      tarr[i] = gcnew Thread(startDelegate);  
      cc->ThreadCount++;  
      tarr[i]->Start();  
   }  
  
   // keep our main thread alive until all worker threads have completed  
   lock l(cc, lock_later); // don't lock now, just create the object  
   while (true) {  
      if (l.try_acquire(50)) { // try to acquire lock, don't throw an exception if can't  
         if (0 == cc->ThreadCount) {  
            Console::WriteLine("All threads completed.");  
            break; // all threads are gone, exit while  
         }  
         else {  
            Console::WriteLine("{0} threads exist, continue waiting...", cc->ThreadCount);  
            l.release(); // some threads exist, let them do their work  
         }  
      }  
   }  
}  
```  
  
  **En el subproceso 3, contador \= 0**  
**En el subproceso 3, contador \= 10**  
**En el subproceso 5, contador \= 0**  
**En el subproceso 5, contador \= 10**  
**En el subproceso 7, contador \= 0**  
**En el subproceso 7, contador \= 10**  
**En el subproceso 4, contador \= 0**  
**En el subproceso 4, contador \= 10**  
**En el subproceso 6, contador \= 0**  
**En el subproceso 6, contador \= 10**  
**Todos los subprocesos completos.**   
## Requisitos  
 **Archivo de encabezado** \<msclr\\lock.h\>  
  
 msclr de**Namespace**  
  
## Vea también  
 [bloquear](../dotnet/lock.md)