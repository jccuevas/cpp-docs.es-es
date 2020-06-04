---
title: reader_writer_lock (Clase)
ms.date: 11/04/2016
f1_keywords:
- reader_writer_lock
- CONCRT/concurrency::reader_writer_lock
- CONCRT/concurrency::reader_writer_lock::scoped_lock
- CONCRT/concurrency::reader_writer_lock::scoped_lock_read
- CONCRT/concurrency::reader_writer_lock::reader_writer_lock
- CONCRT/concurrency::reader_writer_lock::lock
- CONCRT/concurrency::reader_writer_lock::lock_read
- CONCRT/concurrency::reader_writer_lock::try_lock
- CONCRT/concurrency::reader_writer_lock::try_lock_read
- CONCRT/concurrency::reader_writer_lock::unlock
helpviewer_keywords:
- reader_writer_lock class
ms.assetid: 91a59cd2-ca05-4b74-8398-d826d9f86736
ms.openlocfilehash: 13b44387f3e9489090ec31345fe4347ff5f205ca
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376238"
---
# <a name="reader_writer_lock-class"></a>reader_writer_lock (Clase)

Un bloqueo de lectura o escritura basado en cola, con preferencia del sistema de escritura y con giro solo local. El bloqueo permite el acceso primero en entrar, primero en salir (FIFO) a los sistemas de escritura y lectores agotados bajo una carga continua de sistemas de escritura.

## <a name="syntax"></a>Sintaxis

```cpp
class reader_writer_lock;
```

## <a name="members"></a>Miembros

### <a name="public-classes"></a>Clases públicas

|Nombre|Descripción|
|----------|-----------------|
|[reader_writer_lock::scoped_lock (Clase)](#scoped_lock_class)|Un contenedor RAII seguro para excepciones que se puede utilizar para adquirir `reader_writer_lock` objetos de bloqueo como escritor.|
|[reader_writer_lock::scoped_lock_read (Clase)](#scoped_lock_read_class)|Un contenedor RAII seguro para excepciones que se puede utilizar para adquirir `reader_writer_lock` objetos de bloqueo como lector.|

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[reader_writer_lock](#ctor)|Construye un nuevo objeto `reader_writer_lock`.|
|[Destructor de reader_writer_lock](#dtor)|Destruye el objeto `reader_writer_lock`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[Cerradura](#lock)|Adquiere el bloqueo lector-escritor como escritor.|
|[lock_read](#lock_read)|Adquiere el bloqueo lector-escritor como lector. Si hay escritores, los lectores activos tienen que esperar hasta que terminen. El lector simplemente registra un interés en la cerradura y espera a que los escritores la liberen.|
|[try_lock](#try_lock)|Intenta adquirir el bloqueo lector-escritor como escritor sin bloquear.|
|[try_lock_read](#try_lock_read)|Intenta adquirir el bloqueo lector-escritor como lector sin bloqueo.|
|[Desbloquear](#unlock)|Desbloquea el bloqueo lector-escritor en función de quién lo bloqueó, lector o escritor.|

## <a name="remarks"></a>Observaciones

Para obtener más información, consulte Estructuras de datos de [sincronización](../../../parallel/concrt/synchronization-data-structures.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`reader_writer_lock`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrt.h

**Espacio de nombres:** simultaneidad

## <a name="lock"></a><a name="lock"></a>Cerradura

Adquiere el bloqueo lector-escritor como escritor.

```cpp
void lock();
```

### <a name="remarks"></a>Observaciones

A menudo es más seguro utilizar la `reader_writer_lock` construcción [scoped_lock](#scoped_lock_class) para adquirir y liberar un objeto como escritor de una manera segura y segura.

Después de que un escritor intente adquirir el bloqueo, cualquier lector futuro se bloqueará hasta que los escritores hayan adquirido y liberado correctamente el bloqueo. Este bloqueo está sesgado hacia los escritores y puede matar de hambre a los lectores bajo una carga continua de escritores.

Los escritores están encadenados para que un escritor que salga del bloqueo libere al siguiente escritor en la línea.

Si el contexto de llamada ya mantiene el bloqueo, se producirá una [excepción improper_lock.](improper-lock-class.md)

## <a name="lock_read"></a><a name="lock_read"></a>lock_read

Adquiere el bloqueo lector-escritor como lector. Si hay escritores, los lectores activos tienen que esperar hasta que terminen. El lector simplemente registra un interés en la cerradura y espera a que los escritores la liberen.

```cpp
void lock_read();
```

### <a name="remarks"></a>Observaciones

A menudo es más seguro utilizar la `reader_writer_lock` construcción [scoped_lock_read](#scoped_lock_read_class) para adquirir y liberar un objeto como lector de una manera segura y segura.

Si hay escritores esperando en la cerradura, el lector esperará hasta que todos los escritores en la fila hayan adquirido y liberado el bloqueo. Este bloqueo está sesgado hacia los escritores y puede matar de hambre a los lectores bajo una carga continua de escritores.

## <a name="reader_writer_lock"></a><a name="ctor"></a>reader_writer_lock

Construye un nuevo objeto `reader_writer_lock`.

```cpp
reader_writer_lock();
```

## <a name="reader_writer_lock"></a><a name="dtor"></a>Reader_writer_lock

Destruye el objeto `reader_writer_lock`.

```cpp
~reader_writer_lock();
```

### <a name="remarks"></a>Observaciones

Se espera que el bloqueo ya no se mantenga cuando se ejecuta el destructor. Permitir que el bloqueo del lector de lector se destruya con el bloqueo todavía mantenido da como resultado un comportamiento indefinido.

## <a name="reader_writer_lockscoped_lock-class"></a><a name="scoped_lock_class"></a>clase reader_writer_lock::scoped_lock

Un contenedor RAII seguro para excepciones que se puede utilizar para adquirir `reader_writer_lock` objetos de bloqueo como escritor.

```cpp
class scoped_lock;
```

## <a name="scoped_lockscoped_lock"></a><a name="scoped_lock_ctor"></a>scoped_lock::scoped_lock

Construye un `scoped_lock` objeto y `reader_writer_lock` adquiere el `_Reader_writer_lock` objeto pasado en el parámetro como un escritor. Si otro subproceso mantiene el bloqueo, esta llamada se bloqueará.

```cpp
explicit _CRTIMP scoped_lock(reader_writer_lock& _Reader_writer_lock);
```

### <a name="parameters"></a>Parámetros

*_Reader_writer_lock*<br/>
El `reader_writer_lock` objeto a adquirir como escritor.

## <a name="scoped_lockscoped_lock"></a><a name="scoped_lock_dtor"></a>scoped_lock::scoped_lock

Destruye un `reader_writer_lock` objeto y libera el bloqueo proporcionado en su constructor.

```cpp
~scoped_lock();
```

## <a name="reader_writer_lockscoped_lock_read-class"></a><a name="scoped_lock_read_class"></a>clase reader_writer_lock::scoped_lock_read

Un contenedor RAII seguro para excepciones que se puede utilizar para adquirir `reader_writer_lock` objetos de bloqueo como lector.

```cpp
class scoped_lock_read;
```

## <a name="scoped_lock_readscoped_lock_read"></a><a name="scoped_lock_read_ctor"></a>scoped_lock_read::scoped_lock_read

Construye un `scoped_lock_read` objeto y `reader_writer_lock` adquiere el `_Reader_writer_lock` objeto pasado en el parámetro como lector. Si otro subproceso mantiene el bloqueo como escritor o hay escritores pendientes, esta llamada se bloqueará.

```cpp
explicit _CRTIMP scoped_lock_read(reader_writer_lock& _Reader_writer_lock);
```

### <a name="parameters"></a>Parámetros

*_Reader_writer_lock*<br/>
El `reader_writer_lock` objeto a adquirir como lector.

## <a name="a-namescoped_lock_read_dtor--reader_writer_lockscoped_lock_readscoped_lock_read-destructor"></a><a name="scoped_lock_read_dtor">reader_writer_lock::scoped_lock_read::scoped_lock_read Destructor

Destruye un `scoped_lock_read` objeto y libera el bloqueo proporcionado en su constructor.

```cpp
~scoped_lock_read();
```

## <a name="try_lock"></a><a name="try_lock"></a>try_lock

Intenta adquirir el bloqueo lector-escritor como escritor sin bloquear.

### <a name="syntax"></a>Sintaxis

```cpp
bool try_lock();
```

### <a name="return-value"></a>Valor devuelto

Si se adquirió el bloqueo, el valor **true**; de lo contrario, el valor **false**.

## <a name="try_lock_read"></a><a name="try_lock_read"></a>try_lock_read

Intenta adquirir el bloqueo lector-escritor como lector sin bloqueo.

```cpp
bool try_lock_read();
```

### <a name="return-value"></a>Valor devuelto

Si se adquirió el bloqueo, el valor **true**; de lo contrario, el valor **false**.

## <a name="unlock"></a><a name="unlock"></a>Desbloquear

Desbloquea el bloqueo lector-escritor en función de quién lo bloqueó, lector o escritor.

```cpp
void unlock();
```

### <a name="remarks"></a>Observaciones

Si hay escritores esperando en la cerradura, la liberación de la cerradura siempre irá al siguiente escritor en orden FIFO. Este bloqueo está sesgado hacia los escritores y puede matar de hambre a los lectores bajo una carga continua de escritores.

## <a name="see-also"></a>Consulte también

[espacio de nombres de simultaneidad](concurrency-namespace.md)<br/>
[Clase critical_section](critical-section-class.md)
