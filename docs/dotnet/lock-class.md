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
ms.openlocfilehash: ea09dd3d4a2eaf4cf7708d09509cfecfa4a6c6d5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373078"
---
# <a name="lock-class"></a>lock (Clase)

Esta clase automatiza la toma de un bloqueo para sincronizar el acceso a un objeto desde varios subprocesos.  Cuando se construye adquiere el bloqueo y cuando se destruye libera el bloqueo.

## <a name="syntax"></a>Sintaxis

```cpp
ref class lock;
```

## <a name="remarks"></a>Observaciones

`lock`solo está disponible para objetos CLR y solo se puede usar en código CLR.

Internamente, la <xref:System.Threading.Monitor> clase de bloqueo utiliza para sincronizar el acceso. Para obtener más información, consulte el artículo al que se hace referencia.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|---------|-----------|
|[bloqueo::bloqueo](#lock)|Construye un `lock` objeto, opcionalmente esperando para adquirir el bloqueo para siempre, durante un período de tiempo especificado, o no en absoluto.|
|[lock::~lock](#tilde-lock)|Destruye un `lock` objeto.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|---------|-----------|
|[lock::acquire](#acquire)|Adquiere un bloqueo en un objeto, opcionalmente esperando para adquirir el bloqueo para siempre, durante un período de tiempo especificado, o no en absoluto.|
|[lock::is_locked](#is-locked)|Indica si se mantiene un bloqueo.|
|[lock::release](#release)|Libera un bloqueo.|
|[lock::try_acquire](#try-acquire)|Adquiere un bloqueo en un objeto, esperando una cantidad `bool` de tiempo especificada y devolviendo un para informar del éxito de la adquisición en lugar de producir una excepción.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|---------|-----------|
|[bloqueo::operador&nbsp;bool](#operator-bool)|Operador para `lock` usar en una expresión condicional.|
|[lock::operator==](#operator-equality)|Operador de igualdad.|
|[bloqueo::operador!](#operator-inequality)|Operador de desigualdad.|

## <a name="requirements"></a>Requisitos

**Archivo** \<de encabezado msclr-lock.h>

**Espacio de nombres** msclr

## <a name="locklock"></a><a name="lock"></a>bloqueo::bloqueo

Construye un `lock` objeto, opcionalmente esperando para adquirir el bloqueo para siempre, durante un período de tiempo especificado, o no en absoluto.

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
El objeto que se va a bloquear.

*_timeout*<br/>
Valor de tiempo de espera <xref:System.TimeSpan>en milisegundos o como archivo .

### <a name="exceptions"></a>Excepciones

Se <xref:System.ApplicationException> produce si la adquisición de bloqueo no se produce antes del tiempo de espera.

### <a name="remarks"></a>Observaciones

Las tres primeras formas del constructor `_object` intentan adquirir un bloqueo <xref:System.Threading.Timeout.Infinite> dentro del período de tiempo de espera especificado (o si no se especifica ninguna).

La cuarta forma del constructor no adquiere `_object`un bloqueo en . `lock_later`es miembro del [lock_when enum](../dotnet/lock-when-enum.md). Utilice [lock::acquire](../dotnet/lock-acquire.md) o [lock::try_acquire](../dotnet/lock-try-acquire.md) para adquirir el bloqueo en este caso.

El bloqueo se liberará automáticamente cuando se llame al destructor.

`_object`no puede <xref:System.Threading.ReaderWriterLock>ser .  Si es así, se producirá un error del compilador.

### <a name="example"></a>Ejemplo

En este ejemplo se utiliza una única instancia de una clase en varios subprocesos. La clase utiliza un bloqueo en sí mismo para asegurarse de que los accesos a sus datos internos son coherentes para cada subproceso. El subproceso de aplicación principal utiliza un bloqueo en la misma instancia de la clase para comprobar periódicamente si todavía existen subprocesos de trabajo. A continuación, la aplicación principal espera para salir hasta que todos los subprocesos de trabajo hayan completado sus tareas.

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

## <a name="locklock"></a><a name="tilde-lock"></a>bloqueo::-bloqueo

Destruye un `lock` objeto.

```cpp
~lock();
```

### <a name="remarks"></a>Observaciones

El destructor llama a [lock::release](../dotnet/lock-release.md).

### <a name="example"></a>Ejemplo

En este ejemplo se utiliza una única instancia de una clase en varios subprocesos.  La clase utiliza un bloqueo en sí mismo para asegurarse de que los accesos a sus datos internos son coherentes para cada subproceso.  El subproceso de aplicación principal utiliza un bloqueo en la misma instancia de la clase para comprobar periódicamente si todavía existen subprocesos de trabajo. A continuación, la aplicación principal espera para salir hasta que todos los subprocesos de trabajo hayan completado sus tareas.

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

## <a name="lockacquire"></a><a name="acquire"></a>bloqueo::adquirir

Adquiere un bloqueo en un objeto, opcionalmente esperando para adquirir el bloqueo para siempre, durante un período de tiempo especificado, o no en absoluto.

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
Valor de tiempo de <xref:System.TimeSpan>espera en milisegundos o como archivo .

### <a name="exceptions"></a>Excepciones

Se <xref:System.ApplicationException> produce si la adquisición de bloqueo no se produce antes del tiempo de espera.

### <a name="remarks"></a>Observaciones

Si no se proporciona un valor de <xref:System.Threading.Timeout.Infinite>tiempo de espera, el tiempo de espera predeterminado es .

Si ya se ha adquirido un bloqueo, esta función no hace nada.

### <a name="example"></a>Ejemplo

En este ejemplo se utiliza una única instancia de una clase en varios subprocesos.  La clase utiliza un bloqueo en sí mismo para asegurarse de que los accesos a sus datos internos son coherentes para cada subproceso. El subproceso de aplicación principal utiliza un bloqueo en la misma instancia de la clase para comprobar periódicamente si todavía existen subprocesos de trabajo. A continuación, la aplicación principal espera para salir hasta que todos los subprocesos de trabajo hayan completado sus tareas.

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

## <a name="lockis_locked"></a><a name="is-locked"></a>cerradura::is_locked

Indica si se mantiene un bloqueo.

```cpp
bool is_locked();
```

### <a name="return-value"></a>Valor devuelto

`true`si se mantiene `false` un bloqueo, de lo contrario.

### <a name="example"></a>Ejemplo

En este ejemplo se utiliza una única instancia de una clase en varios subprocesos.  La clase utiliza un bloqueo en sí mismo para asegurarse de que los accesos a sus datos internos son coherentes para cada subproceso.  El subproceso de aplicación principal utiliza un bloqueo en la misma instancia de la clase para comprobar periódicamente si aún existen subprocesos de trabajo y espera a salir hasta que todos los subprocesos de trabajo hayan completado sus tareas.

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

## <a name="lockoperator-bool"></a><a name="operator-bool"></a>bloqueo::operador bool

Operador para `lock` usar en una expresión condicional.

```cpp
operator bool();
```

### <a name="return-value"></a>Valor devuelto

`true`si se mantiene `false` un bloqueo, de lo contrario.

### <a name="remarks"></a>Observaciones

Este operador realmente `_detail_class::_safe_bool` convierte a `bool` que es más seguro que porque no se puede convertir a un tipo entero.

### <a name="example"></a>Ejemplo

En este ejemplo se utiliza una única instancia de una clase en varios subprocesos.  La clase utiliza un bloqueo en sí mismo para asegurarse de que los accesos a sus datos internos son coherentes para cada subproceso. El subproceso de aplicación principal utiliza un bloqueo en la misma instancia de la clase para comprobar periódicamente si todavía existen subprocesos de trabajo. La aplicación principal espera para salir hasta que todos los subprocesos de trabajo hayan completado sus tareas.

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

## <a name="lockrelease"></a><a name="release"></a>lock::release

Libera un bloqueo.

```cpp
void release();
```

### <a name="remarks"></a>Observaciones

Si no se mantiene `release` ningún bloqueo, no hace nada.

No es posible llamar a esta función explícitamente. Cuando `lock` un objeto sale del ámbito, su destructor llama `release`.

### <a name="example"></a>Ejemplo

En este ejemplo se utiliza una única instancia de una clase en varios subprocesos. La clase utiliza un bloqueo en sí mismo para asegurarse de que los accesos a sus datos internos son coherentes para cada subproceso. El subproceso de aplicación principal utiliza un bloqueo en la misma instancia de la clase para comprobar periódicamente si todavía existen subprocesos de trabajo. A continuación, la aplicación principal espera para salir hasta que todos los subprocesos de trabajo hayan completado sus tareas.

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

## <a name="locktry_acquire"></a><a name="try-acquire"></a>cerradura::try_acquire

Adquiere un bloqueo en un objeto, esperando una cantidad `bool` de tiempo especificada y devolviendo un para informar del éxito de la adquisición en lugar de producir una excepción.

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
Valor de tiempo de <xref:System.TimeSpan>espera en milisegundos o como archivo .

### <a name="return-value"></a>Valor devuelto

`true`si se adquirió la cerradura, `false` de lo contrario.

### <a name="remarks"></a>Observaciones

Si ya se ha adquirido un bloqueo, esta función no hace nada.

### <a name="example"></a>Ejemplo

En este ejemplo se utiliza una única instancia de una clase en varios subprocesos. La clase utiliza un bloqueo en sí mismo para asegurarse de que los accesos a sus datos internos son coherentes para cada subproceso. El subproceso de aplicación principal utiliza un bloqueo en la misma instancia de la clase para comprobar periódicamente si todavía existen subprocesos de trabajo. A continuación, la aplicación principal espera para salir hasta que todos los subprocesos de trabajo hayan completado sus tareas.

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

## <a name="lockoperator"></a><a name="operator-equality"></a>Bloqueo::operador

Operador de igualdad.

```cpp
template<class T> bool operator==(
   T t
);
```

### <a name="parameters"></a>Parámetros

*T*<br/>
El objeto cuya igualdad se va a comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve `true` `t` si es el mismo que `false` el objeto del bloqueo, en caso contrario.

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

## <a name="lockoperator"></a><a name="operator-inequality"></a>bloqueo::operador!

Operador de desigualdad.

```cpp
template<class T> bool operator!=(
   T t
);
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Objeto que se va a comparar para la desigualdad.

### <a name="return-value"></a>Valor devuelto

Devuelve `true` `t` si difiere del objeto del `false` bloqueo, en caso contrario.

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
