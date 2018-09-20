---
title: Lock::acquire | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- lock::acquire
- acquire
- msclr.lock.acquire
- msclr::lock::acquire
- lock.acquire
dev_langs:
- C++
helpviewer_keywords:
- acquire method
ms.assetid: c214274e-7519-4739-82aa-91b04a32d3f9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 0a1bc71e4474f0d7d22d217adb96aa7340fb933b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46409173"
---
# <a name="lockacquire"></a>lock::acquire

Adquiere un bloqueo en un objeto, opcionalmente esperando para adquirir el bloqueo para siempre, durante un período determinado de tiempo o no en absoluto.

## <a name="syntax"></a>Sintaxis

```
void acquire();
void acquire(
   int _timeout
);
void acquire(
   System::TimeSpan _timeout
);
```

#### <a name="parameters"></a>Parámetros

*_tiempo de espera*<br/>
Valor de tiempo de espera en milisegundos, o como un <xref:System.TimeSpan>.

## <a name="exceptions"></a>Excepciones

Produce <xref:System.ApplicationException> si la adquisición de bloqueo no se produce antes de tiempo de espera.

## <a name="remarks"></a>Comentarios

Si no se proporciona un valor de tiempo de espera, el tiempo de espera predeterminado es <xref:System.Threading.Timeout.Infinite>.

Si ya ha adquirido un bloqueo, esta función no hace nada.

## <a name="example"></a>Ejemplo

En este ejemplo se usa una sola instancia de una clase en varios subprocesos.  La clase utiliza un bloqueo en sí mismo para asegurarse de que los accesos a sus datos internos sean coherentes para cada subproceso.  El subproceso principal de la aplicación utiliza un bloqueo en la misma instancia de la clase para comprobar periódicamente para ver si los subprocesos de trabajo siguen existan, y espera hasta salir hasta que todos los subprocesos de trabajo haya completado sus tareas.

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

```Output
In thread 3, Counter = 0
In thread 3, Counter = 10
In thread 5, Counter = 0
In thread 5, Counter = 10
In thread 7, Counter = 0
In thread 7, Counter = 10
In thread 4, Counter = 0
In thread 4, Counter = 10
In thread 6, Counter = 0
In thread 6, Counter = 10
All threads completed.
```

## <a name="requirements"></a>Requisitos

**Archivo de encabezado** \<msclr\lock.h >

**Namespace** msclr

## <a name="see-also"></a>Vea también

[lock (Miembros)](../dotnet/lock-members.md)<br/>
[lock::try_acquire](../dotnet/lock-try-acquire.md)