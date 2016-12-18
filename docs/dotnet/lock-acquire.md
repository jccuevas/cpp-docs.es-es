---
title: "lock::acquire | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "lock::acquire"
  - "acquire"
  - "msclr.lock.acquire"
  - "msclr::lock::acquire"
  - "lock.acquire"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "acquire (método)"
ms.assetid: c214274e-7519-4739-82aa-91b04a32d3f9
caps.latest.revision: 14
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# lock::acquire
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Adquiere un bloqueo en un objeto, esperando opcionalmente para adquirir el bloqueo para siempre, por un tiempo determinado, o en absoluto.  
  
## Sintaxis  
  
```  
void acquire();  
void acquire(  
   int _timeout  
);  
void acquire(  
   System::TimeSpan _timeout  
);  
```  
  
#### Parámetros  
 `_timeout`  
 Valor de tiempo de espera en milisegundos o como <xref:System.TimeSpan>.  
  
## Excepciones  
 Produce <xref:System.ApplicationException> si la adquisición de bloqueo no aparece antes del tiempo de espera.  
  
## Comentarios  
 Si un valor de tiempo de espera no se proporciona, el tiempo de espera predeterminado es <xref:System.Threading.Timeout.Infinite>.  
  
 Si un bloqueo se ha adquirido ya, esta función no hace nada.  
  
## Ejemplo  
 Este ejemplo utiliza una sola instancia de una clase a través de varios subprocesos.  La clase utiliza un bloqueo en sí misma para garantizar que los accesos a sus datos internos son coherentes para cada subproceso.  El subproceso de aplicación principal utiliza un bloqueo en la misma instancia de la clase compruebe periódicamente para ver si todavía existen algunos subprocesos de trabajo, y espera para salir hasta que todos los subprocesos de trabajo completen sus tareas.  
  
```  
// msl_lock_acquire.cpp  
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
 [lock \(Miembros\)](../dotnet/lock-members.md)   
 [lock::try\_acquire](../dotnet/lock-try-acquire.md)