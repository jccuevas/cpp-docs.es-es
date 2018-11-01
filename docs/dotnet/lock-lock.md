---
title: lock::lock
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- lock::lock
- lock.lock
- msclr.lock.lock
- msclr::lock::lock
helpviewer_keywords:
- lock constructor
ms.assetid: c9ad6c71-36ec-49c5-8ebd-f5c3a0cc94f0
ms.openlocfilehash: 480e4f6604adc0a6bd0b3b5fff32f37c811a16a4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50470582"
---
# <a name="locklock"></a>lock::lock

Construye un `lock` objeto, opcionalmente esperando para adquirir el bloqueo para siempre, durante un período determinado de tiempo o no en absoluto.

## <a name="syntax"></a>Sintaxis

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

#### <a name="parameters"></a>Parámetros

*_Object*<br/>
El objeto se bloquee.

*_tiempo de espera*<br/>
Valor de tiempo de espera en milisegundos, o como un <xref:System.TimeSpan>.

## <a name="exceptions"></a>Excepciones

Produce <xref:System.ApplicationException> si la adquisición de bloqueo no se produce antes de tiempo de espera.

## <a name="remarks"></a>Comentarios

Los tres primeros formularios del constructor intentan adquirir un bloqueo en `_object` dentro del período de tiempo de espera especificado (o <xref:System.Threading.Timeout.Infinite> si se especifica ninguno).

La cuarta forma del constructor no adquiere un bloqueo en `_object`. `lock_later` es un miembro de la [lock_when (enumeración)](../dotnet/lock-when-enum.md). Use [lock::acquire](../dotnet/lock-acquire.md) o [lock::try_acquire](../dotnet/lock-try-acquire.md) para adquirir el bloqueo en este caso.

El bloqueo se libera automáticamente cuando se llama al destructor.

El valor de `_object` no puede ser <xref:System.Threading.ReaderWriterLock>.  Si es así, se producirá un error del compilador.

## <a name="example"></a>Ejemplo

En este ejemplo se usa una sola instancia de una clase en varios subprocesos.  La clase utiliza un bloqueo en sí mismo para asegurarse de que los accesos a sus datos internos sean coherentes para cada subproceso.  El subproceso principal de la aplicación utiliza un bloqueo en la misma instancia de la clase para comprobar periódicamente para ver si los subprocesos de trabajo siguen existan, y espera hasta salir hasta que todos los subprocesos de trabajo haya completado sus tareas.

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
[lock::~lock](../dotnet/lock-tilde-lock.md)<br/>
[lock::acquire](../dotnet/lock-acquire.md)<br/>
[lock::try_acquire](../dotnet/lock-try-acquire.md)