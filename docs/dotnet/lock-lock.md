---
title: "lock::lock | Microsoft Docs"
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
  - "lock::lock"
  - "lock.lock"
  - "msclr.lock.lock"
  - "msclr::lock::lock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "lock (constructor)"
ms.assetid: c9ad6c71-36ec-49c5-8ebd-f5c3a0cc94f0
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# lock::lock
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Construye un objeto de `lock` , esperando opcionalmente para adquirir el bloqueo para siempre, por un tiempo determinado, o en absoluto.  
  
## Sintaxis  
  
```  
template<class T> lock(  
   T ^ _object  
);  
template<class T> lock(  
   T ^ _object,  
   int _timeout  
);  
template<class T> lock(  
   T ^ _object,  
   System::TimeSpan _timeout  
);  
template<class T> lock(  
   T ^ _object,  
   lock_later  
);  
```  
  
#### Parámetros  
 `_object`  
 Objeto que se va a bloquear.  
  
 `_timeout`  
 Valor de tiempo de espera en milisegundos o como <xref:System.TimeSpan>.  
  
## Excepciones  
 Produce <xref:System.ApplicationException> si la adquisición de bloqueo no aparece antes del tiempo de espera.  
  
## Comentarios  
 Los primeros tres formas de constructor intentan adquirir un bloqueo en `_object` dentro del período de tiempo de espera especificado \(o de <xref:System.Threading.Timeout.Infinite> si no se especifica ninguno\).  
  
 El cuarto formulario de constructor no adquiere un bloqueo en `_object`.  `lock_later` es miembro de [lock\_when \(Enumeración\)](../dotnet/lock-when-enum.md).  Utilice [lock::acquire](../dotnet/lock-acquire.md) o [lock::try\_acquire](../dotnet/lock-try-acquire.md) para adquirir el bloqueo en este caso.  
  
 El bloqueo automáticamente se liberará cuando se llama al destructor.  
  
 El valor de `_object` no puede ser <xref:System.Threading.ReaderWriterLock>.  Si es, un error del compilador lo.  
  
## Ejemplo  
 Este ejemplo utiliza una sola instancia de una clase a través de varios subprocesos.  La clase utiliza un bloqueo en sí misma para garantizar que los accesos a sus datos internos son coherentes para cada subproceso.  El subproceso de aplicación principal utiliza un bloqueo en la misma instancia de la clase compruebe periódicamente para ver si todavía existen algunos subprocesos de trabajo, y espera para salir hasta que todos los subprocesos de trabajo completen sus tareas.  
  
```  
// msl_lock_lock.cpp  
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
 [lock::~lock](../dotnet/lock-tilde-lock.md)   
 [lock::acquire](../dotnet/lock-acquire.md)   
 [lock::try\_acquire](../dotnet/lock-try-acquire.md)