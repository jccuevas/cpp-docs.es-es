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
ms.openlocfilehash: b2ae1be31233e55aa34d6f3046d90fb2127348c0
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80080043"
---
# <a name="lock-class"></a>lock (Clase)

Esta clase automatiza la toma de un bloqueo para sincronizar el acceso a un objeto desde varios subprocesos.  Cuando se construye, adquiere el bloqueo y, cuando se destruye, libera el bloqueo.

## <a name="syntax"></a>Sintaxis

```cpp
ref class lock;
```

## <a name="remarks"></a>Observaciones

`lock` solo está disponible para los objetos CLR y solo se puede usar en código CLR.

Internamente, la clase Lock usa <xref:System.Threading.Monitor> para sincronizar el acceso. Para obtener más información, consulte el artículo al que se hace referencia.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|---------|-----------|
|[lock::lock](#lock)|Construye un objeto `lock`, de manera opcional, en espera para adquirir el bloqueo de forma indefinida, durante un período de tiempo especificado o no en absoluto.|
|[lock::~lock](#tilde-lock)|Destruye un objeto `lock`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|---------|-----------|
|[lock::acquire](#acquire)|Adquiere un bloqueo en un objeto, de manera opcional, en espera para adquirir el bloqueo de forma indefinida, durante un período de tiempo especificado o no en absoluto.|
|[lock::is_locked](#is-locked)|Indica si se mantiene un bloqueo.|
|[lock::release](#release)|Libera un bloqueo.|
|[lock::try_acquire](#try-acquire)|Adquiere un bloqueo en un objeto, a la espera de una cantidad de tiempo especificada y devuelve un `bool` para notificar el éxito de la adquisición en lugar de producir una excepción.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|---------|-----------|
|[Lock:: Operator&nbsp;bool](#operator-bool)|Operador para usar `lock` en una expresión condicional.|
|[lock::operator==](#operator-equality)|Operador de igualdad.|
|[lock::operator!=](#operator-inequality)|Operador de desigualdad.|

## <a name="requirements"></a>Requisitos

**Archivo de encabezado** \<msclr\lock.h >

**Espacio de nombres** msclr

## <a name="locklock"></a><a name="lock"></a>Lock:: Lock

Construye un objeto `lock`, de manera opcional, en espera para adquirir el bloqueo de forma indefinida, durante un período de tiempo especificado o no en absoluto.

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
Objeto que se va a bloquear.

*_timeout*<br/>
Valor de tiempo de espera en milisegundos o como <xref:System.TimeSpan>.

### <a name="exceptions"></a>Excepciones

Produce <xref:System.ApplicationException> si la adquisición de bloqueos no se produce antes del tiempo de espera.

### <a name="remarks"></a>Observaciones

Las tres primeras formas del constructor intentan adquirir un bloqueo en `_object` dentro del período de tiempo de espera especificado (o <xref:System.Threading.Timeout.Infinite> si no se especifica ninguno).

El cuarto formulario del constructor no adquiere un bloqueo en `_object`. `lock_later` es un miembro de la [enumeración lock_when](../dotnet/lock-when-enum.md). Use [Lock:: acquire](../dotnet/lock-acquire.md) o [lock:: try_acquire](../dotnet/lock-try-acquire.md) para adquirir el bloqueo en este caso.

El bloqueo se liberará automáticamente cuando se llame al destructor.

no se puede <xref:System.Threading.ReaderWriterLock>`_object`.  Si es así, se producirá un error del compilador.

### <a name="example"></a>Ejemplo

En este ejemplo se usa una sola instancia de una clase en varios subprocesos. La clase utiliza un bloqueo para asegurarse de que los accesos a sus datos internos son coherentes para cada subproceso. El subproceso de aplicación principal utiliza un bloqueo en la misma instancia de la clase para comprobar periódicamente si hay algún subproceso de trabajo. A continuación, la aplicación principal espera a salir hasta que todos los subprocesos de trabajo hayan completado sus tareas.

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

## <a name="locklock"></a><a name="tilde-lock"></a>Lock:: ~ Lock

Destruye un objeto `lock`.

```cpp
~lock();
```

### <a name="remarks"></a>Observaciones

El destructor llama a [Lock:: Release](../dotnet/lock-release.md).

### <a name="example"></a>Ejemplo

En este ejemplo se usa una sola instancia de una clase en varios subprocesos.  La clase utiliza un bloqueo para asegurarse de que los accesos a sus datos internos son coherentes para cada subproceso.  El subproceso de aplicación principal utiliza un bloqueo en la misma instancia de la clase para comprobar periódicamente si hay algún subproceso de trabajo. A continuación, la aplicación principal espera a salir hasta que todos los subprocesos de trabajo hayan completado sus tareas.

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

## <a name="lockacquire"></a><a name="acquire"></a>Lock:: acquire

Adquiere un bloqueo en un objeto, de manera opcional, en espera para adquirir el bloqueo de forma indefinida, durante un período de tiempo especificado o no en absoluto.

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
Valor de tiempo de espera en milisegundos o como <xref:System.TimeSpan>.

### <a name="exceptions"></a>Excepciones

Produce <xref:System.ApplicationException> si la adquisición de bloqueos no se produce antes del tiempo de espera.

### <a name="remarks"></a>Observaciones

Si no se proporciona un valor de tiempo de espera, el tiempo de espera predeterminado es <xref:System.Threading.Timeout.Infinite>.

Si ya se ha adquirido un bloqueo, esta función no hace nada.

### <a name="example"></a>Ejemplo

En este ejemplo se usa una sola instancia de una clase en varios subprocesos.  La clase utiliza un bloqueo para asegurarse de que los accesos a sus datos internos son coherentes para cada subproceso. El subproceso de aplicación principal utiliza un bloqueo en la misma instancia de la clase para comprobar periódicamente si hay algún subproceso de trabajo. A continuación, la aplicación principal espera a salir hasta que todos los subprocesos de trabajo hayan completado sus tareas.

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

## <a name="lockis_locked"></a><a name="is-locked"></a>Lock:: is_locked

Indica si se mantiene un bloqueo.

```cpp
bool is_locked();
```

### <a name="return-value"></a>Valor devuelto

`true` si se mantiene un bloqueo, `false` de lo contrario.

### <a name="example"></a>Ejemplo

En este ejemplo se usa una sola instancia de una clase en varios subprocesos.  La clase utiliza un bloqueo para asegurarse de que los accesos a sus datos internos son coherentes para cada subproceso.  El subproceso de aplicación principal utiliza un bloqueo en la misma instancia de la clase para comprobar periódicamente si hay algún subproceso de trabajo y espera a salir hasta que todos los subprocesos de trabajo hayan completado sus tareas.

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

## <a name="lockoperator-bool"></a><a name="operator-bool"></a>Lock:: Operator bool

Operador para usar `lock` en una expresión condicional.

```cpp
operator bool();
```

### <a name="return-value"></a>Valor devuelto

`true` si se mantiene un bloqueo, `false` de lo contrario.

### <a name="remarks"></a>Observaciones

Este operador realmente convierte en `_detail_class::_safe_bool` que es más seguro que `bool` porque no se puede convertir en un tipo entero.

### <a name="example"></a>Ejemplo

En este ejemplo se usa una sola instancia de una clase en varios subprocesos.  La clase utiliza un bloqueo para asegurarse de que los accesos a sus datos internos son coherentes para cada subproceso. El subproceso de aplicación principal utiliza un bloqueo en la misma instancia de la clase para comprobar periódicamente si hay algún subproceso de trabajo. La aplicación principal espera a salir hasta que todos los subprocesos de trabajo hayan completado sus tareas.

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

## <a name="lockrelease"></a><a name="release"></a>Lock:: Release

Libera un bloqueo.

```cpp
void release();
```

### <a name="remarks"></a>Observaciones

Si no se mantiene ningún bloqueo, `release` no hace nada.

No es necesario llamar a esta función explícitamente. Cuando un objeto `lock` sale del ámbito, su Destructor llama a `release`.

### <a name="example"></a>Ejemplo

En este ejemplo se usa una sola instancia de una clase en varios subprocesos. La clase utiliza un bloqueo para asegurarse de que los accesos a sus datos internos son coherentes para cada subproceso. El subproceso de aplicación principal utiliza un bloqueo en la misma instancia de la clase para comprobar periódicamente si hay algún subproceso de trabajo. A continuación, la aplicación principal espera a salir hasta que todos los subprocesos de trabajo hayan completado sus tareas.

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

## <a name="locktry_acquire"></a><a name="try-acquire"></a>Lock:: try_acquire

Adquiere un bloqueo en un objeto, a la espera de una cantidad de tiempo especificada y devuelve un `bool` para notificar el éxito de la adquisición en lugar de producir una excepción.

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
Valor de tiempo de espera en milisegundos o como <xref:System.TimeSpan>.

### <a name="return-value"></a>Valor devuelto

`true` si se adquirió el bloqueo, `false` de lo contrario.

### <a name="remarks"></a>Observaciones

Si ya se ha adquirido un bloqueo, esta función no hace nada.

### <a name="example"></a>Ejemplo

En este ejemplo se usa una sola instancia de una clase en varios subprocesos. La clase utiliza un bloqueo para asegurarse de que los accesos a sus datos internos son coherentes para cada subproceso. El subproceso de aplicación principal utiliza un bloqueo en la misma instancia de la clase para comprobar periódicamente si hay algún subproceso de trabajo. A continuación, la aplicación principal espera a salir hasta que todos los subprocesos de trabajo hayan completado sus tareas.

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

## <a name="lockoperator"></a><a name="operator-equality"></a>Lock:: Operator = =

Operador de igualdad.

```cpp
template<class T> bool operator==(
   T t
);
```

### <a name="parameters"></a>Parámetros

*t*<br/>
El objeto cuya igualdad se va a comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve `true` si `t` es igual que el objeto del bloqueo `false` de lo contrario.

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

## <a name="lockoperator"></a><a name="operator-inequality"></a>Lock:: Operator! =

Operador de desigualdad.

```cpp
template<class T> bool operator!=(
   T t
);
```

### <a name="parameters"></a>Parámetros

*t*<br/>
Objeto cuya desigualdad se va a comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve `true` si `t` difiere del objeto del bloqueo `false` de lo contrario.

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