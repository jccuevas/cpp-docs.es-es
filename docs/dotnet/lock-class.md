---
title: lock (Clase)
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- msclr::lock::lock
- msclr::lock::is_locked
- msclr::lock.is_locked
- msclr::lock::acquire
- msclr::lock::try_acquire
- msclr::lock::release
- msclr::lock::operator==
- msclr::lock::operator!=
helpviewer_keywords:
- msclr::lock class
ms.assetid: 5123edd9-6aed-497d-9a0b-f4b6d6c0d666
ms.openlocfilehash: 43418da36aa2d87608a9d672e4345d24011be0b3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62153445"
---
# <a name="lock-class"></a>lock (Clase)

Esta clase automatiza tomar un bloqueo para sincronizar el acceso a un objeto desde varios subprocesos.  Cuando se construye adquiere el bloqueo y cuando se destruye versiones el bloqueo.

## <a name="syntax"></a>Sintaxis

```cpp
ref class lock;
```

## <a name="remarks"></a>Comentarios

`lock` solo está disponible para los objetos de CLR y sólo puede utilizarse en el código CLR.

Internamente, los usos de la clase de bloqueo <xref:System.Threading.Monitor> para sincronizar el acceso. Para obtener más información, vea el artículo que se hace referencia.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|---------|-----------|
|[lock::lock](#lock)|Construye un `lock` objeto, opcionalmente esperando para adquirir el bloqueo para siempre, durante un período determinado de tiempo o no en absoluto.|
|[lock::~lock](#tilde-lock)|Destructs un `lock` objeto.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|---------|-----------|
|[lock::acquire](#acquire)|Adquiere un bloqueo en un objeto, opcionalmente esperando para adquirir el bloqueo para siempre, durante un período determinado de tiempo o no en absoluto.|
|[lock::is_locked](#is-locked)|Indica si se encuentra un bloqueo.|
|[lock::release](#release)|Libera un bloqueo.|
|[lock::try_acquire](#try-acquire)|Adquiere un bloqueo en un objeto, esperando un período de tiempo especificado y devuelve un `bool` para informar del éxito de adquisición en lugar de producir una excepción.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|---------|-----------|
|[lock::operator&nbsp;bool](#operator-bool)|Operador para el uso de `lock` en una expresión condicional.|
|[lock::operator==](#operator-equality)|Operador de igualdad.|
|[lock::operator!=](#operator-inequality)|Operador de desigualdad.|

## <a name="requirements"></a>Requisitos

**Archivo de encabezado** \<msclr\lock.h >

**Namespace** msclr



## <a name="lock"></a>lock::lock

Construye un `lock` objeto, opcionalmente esperando para adquirir el bloqueo para siempre, durante un período determinado de tiempo o no en absoluto.

```cpp
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

### <a name="parameters"></a>Parámetros

*_object*<br/>
El objeto se bloquee.

*_timeout*<br/>
Valor de tiempo de espera en milisegundos, o como un <xref:System.TimeSpan>.

### <a name="exceptions"></a>Excepciones

Produce <xref:System.ApplicationException> si la adquisición de bloqueo no se produce antes de tiempo de espera.

### <a name="remarks"></a>Comentarios

Los tres primeros formularios del constructor intentan adquirir un bloqueo en `_object` dentro del período de tiempo de espera especificado (o <xref:System.Threading.Timeout.Infinite> si se especifica ninguno).

La cuarta forma del constructor no adquirir un bloqueo en `_object`. `lock_later` es un miembro de la [lock_when (enumeración)](../dotnet/lock-when-enum.md). Use [lock::acquire](../dotnet/lock-acquire.md) o [lock::try_acquire](../dotnet/lock-try-acquire.md) para adquirir el bloqueo en este caso.

El bloqueo se libera automáticamente cuando se llama al destructor.

`_object` no puede ser <xref:System.Threading.ReaderWriterLock>.  Si es así, se producirá un error del compilador.

### <a name="example"></a>Ejemplo

En este ejemplo se usa una sola instancia de una clase entre varios subprocesos. La clase utiliza un bloqueo en sí mismo para asegurarse de que los accesos a sus datos internos sean coherentes para cada subproceso. El subproceso principal de la aplicación utiliza un bloqueo en la misma instancia de la clase para comprobar periódicamente si todavía existen los subprocesos de trabajo. A continuación, la aplicación principal espera para salir hasta que todos los subprocesos de trabajo hayan completado sus tareas.

```cpp
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

## <a name="tilde-lock"></a>lock::~lock

Destructs un `lock` objeto.

```cpp
~lock();
```

### <a name="remarks"></a>Comentarios

El destructor llama a [lock::release](../dotnet/lock-release.md).

### <a name="example"></a>Ejemplo

En este ejemplo se usa una sola instancia de una clase entre varios subprocesos.  La clase utiliza un bloqueo en sí mismo para asegurarse de que los accesos a sus datos internos sean coherentes para cada subproceso.  El subproceso principal de la aplicación utiliza un bloqueo en la misma instancia de la clase para comprobar periódicamente si todavía existen los subprocesos de trabajo. A continuación, la aplicación principal espera para salir hasta que todos los subprocesos de trabajo hayan completado sus tareas.

```cpp
// msl_lock_dtor.cpp
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

## <a name="acquire"></a>lock::acquire

Adquiere un bloqueo en un objeto, opcionalmente esperando para adquirir el bloqueo para siempre, durante un período determinado de tiempo o no en absoluto.

```cpp
void acquire();
void acquire(
   int _timeout
);
void acquire(
   System::TimeSpan _timeout
);
```

### <a name="parameters"></a>Parámetros

*_timeout*<br/>
Valor de tiempo de espera en milisegundos, o como un <xref:System.TimeSpan>.

### <a name="exceptions"></a>Excepciones

Produce <xref:System.ApplicationException> si la adquisición de bloqueo no se produce antes de tiempo de espera.

### <a name="remarks"></a>Comentarios

Si no se proporciona un valor de tiempo de espera, el tiempo de espera predeterminado es <xref:System.Threading.Timeout.Infinite>.

Si ya ha adquirido un bloqueo, esta función no hace nada.

### <a name="example"></a>Ejemplo

En este ejemplo se usa una sola instancia de una clase entre varios subprocesos.  La clase utiliza un bloqueo en sí mismo para asegurarse de que los accesos a sus datos internos sean coherentes para cada subproceso. El subproceso principal de la aplicación utiliza un bloqueo en la misma instancia de la clase para comprobar periódicamente si todavía existen los subprocesos de trabajo. A continuación, la aplicación principal espera para salir hasta que todos los subprocesos de trabajo hayan completado sus tareas.

```cpp
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

## <a name="is-locked"></a>lock::is_locked

Indica si se encuentra un bloqueo.

```cpp
bool is_locked();
```

### <a name="return-value"></a>Valor devuelto

`true` Si se mantiene un bloqueo, `false` en caso contrario.

### <a name="example"></a>Ejemplo

En este ejemplo se usa una sola instancia de una clase entre varios subprocesos.  La clase utiliza un bloqueo en sí mismo para asegurarse de que los accesos a sus datos internos sean coherentes para cada subproceso.  El subproceso principal de la aplicación utiliza un bloqueo en la misma instancia de la clase para comprobar periódicamente para ver si los subprocesos de trabajo siguen existan, y espera hasta salir hasta que todos los subprocesos de trabajo haya completado sus tareas.

```cpp
// msl_lock_is_locked.cpp
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
      l.try_acquire(50); // try to acquire lock, don't throw an exception if can't
      if (l.is_locked()) { // check if we got the lock
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
In thread 4, Counter = 0
In thread 4, Counter = 10
In thread 7, Counter = 0
In thread 7, Counter = 10
In thread 6, Counter = 0
In thread 6, Counter = 10
All threads completed.
```

## <a name="operator-bool"></a>lock::operator bool

Operador para el uso de `lock` en una expresión condicional.

```cpp
operator bool();
```

### <a name="return-value"></a>Valor devuelto

`true` Si se mantiene un bloqueo, `false` en caso contrario.

### <a name="remarks"></a>Comentarios

Este operador convierte realmente en `_detail_class::_safe_bool` que es más seguro que `bool` porque no se puede convertir a un tipo entero.

### <a name="example"></a>Ejemplo

En este ejemplo se usa una sola instancia de una clase entre varios subprocesos.  La clase utiliza un bloqueo en sí mismo para asegurarse de que los accesos a sus datos internos sean coherentes para cada subproceso. El subproceso principal de la aplicación utiliza un bloqueo en la misma instancia de la clase para comprobar periódicamente si todavía existen los subprocesos de trabajo. Espera a que la aplicación principal para salir hasta que todos los subprocesos de trabajo hayan completado sus tareas.

```cpp
// msl_lock_op_bool.cpp
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
      l.try_acquire(50); // try to acquire lock, don't throw an exception if can't
      if (l) { // use bool operator to check for lock
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

## <a name="release"></a>lock::release

Libera un bloqueo.

```cpp
void release();
```

### <a name="remarks"></a>Comentarios

Si no se encuentra ningún bloqueo, `release` no hace nada.

No debe llamar explícitamente a esta función. Cuando un `lock` objeto queda fuera del ámbito, sus llamadas de destructor `release`.

### <a name="example"></a>Ejemplo

En este ejemplo se usa una sola instancia de una clase entre varios subprocesos. La clase utiliza un bloqueo en sí mismo para asegurarse de que los accesos a sus datos internos sean coherentes para cada subproceso. El subproceso principal de la aplicación utiliza un bloqueo en la misma instancia de la clase para comprobar periódicamente si todavía existen los subprocesos de trabajo. A continuación, la aplicación principal espera para salir hasta que todos los subprocesos de trabajo hayan completado sus tareas.

```cpp
// msl_lock_release.cpp
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

## <a name="try-acquire"></a>lock::try_acquire

Adquiere un bloqueo en un objeto, esperando un período de tiempo especificado y devuelve un `bool` para informar del éxito de adquisición en lugar de producir una excepción.

```cpp
bool try_acquire(
   int _timeout_ms
);
bool try_acquire(
   System::TimeSpan _timeout
);
```

### <a name="parameters"></a>Parámetros

*_timeout*<br/>
Valor de tiempo de espera en milisegundos, o como un <xref:System.TimeSpan>.

### <a name="return-value"></a>Valor devuelto

`true` Si se adquirió el bloqueo, `false` en caso contrario.

### <a name="remarks"></a>Comentarios

Si ya ha adquirido un bloqueo, esta función no hace nada.

### <a name="example"></a>Ejemplo

En este ejemplo se usa una sola instancia de una clase entre varios subprocesos. La clase utiliza un bloqueo en sí mismo para asegurarse de que los accesos a sus datos internos sean coherentes para cada subproceso. El subproceso principal de la aplicación utiliza un bloqueo en la misma instancia de la clase para comprobar periódicamente si todavía existen los subprocesos de trabajo. A continuación, la aplicación principal espera para salir hasta que todos los subprocesos de trabajo hayan completado sus tareas.

```cpp
// msl_lock_try_acquire.cpp
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

## <a name="operator-equality"></a>lock::operator==

Operador de igualdad.

```cpp
template<class T> bool operator==(
   T t
);
```

### <a name="parameters"></a>Parámetros

*t*<br/>
El objeto para comparar la igualdad.

### <a name="return-value"></a>Valor devuelto

Devuelve `true` si `t` es el mismo que el objeto de bloqueo, `false` en caso contrario.

### <a name="example"></a>Ejemplo

```cpp
// msl_lock_op_eq.cpp
// compile with: /clr
#include <msclr/lock.h>

using namespace System;
using namespace System::Threading;
using namespace msclr;

int main () {
   Object^ o1 = gcnew Object;
   lock l1(o1);
   if (l1 == o1) {
      Console::WriteLine("Equal!");
   }
}
```

```Output
Equal!
```

## <a name="operator-inequality"></a>lock::operator!=

Operador de desigualdad.

```cpp
template<class T> bool operator!=(
   T t
);
```

### <a name="parameters"></a>Parámetros

*t*<br/>
El objeto para comparar la desigualdad.

### <a name="return-value"></a>Valor devuelto

Devuelve `true` si `t` difiere de objeto del bloqueo, `false` en caso contrario.

### <a name="example"></a>Ejemplo

```cpp
// msl_lock_op_ineq.cpp
// compile with: /clr
#include <msclr/lock.h>

using namespace System;
using namespace System::Threading;
using namespace msclr;

int main () {
   Object^ o1 = gcnew Object;
   Object^ o2 = gcnew Object;
   lock l1(o1);
   if (l1 != o2) {
      Console::WriteLine("Inequal!");
   }
}
```

```Output
Inequal!
```