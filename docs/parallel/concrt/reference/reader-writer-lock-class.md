---
title: reader_writer_lock (clase)
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
ms.openlocfilehash: 1a7386e527b5327d928bfdcb3281c88666f1b106
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78867176"
---
# <a name="reader_writer_lock-class"></a>reader_writer_lock (clase)

Un bloqueo de lectura o escritura basado en cola, con preferencia del sistema de escritura y con giro solo local. El bloqueo permite el acceso primero en entrar, primero en salir (FIFO) a los sistemas de escritura y lectores agotados bajo una carga continua de sistemas de escritura.

## <a name="syntax"></a>Sintaxis

```cpp
class reader_writer_lock;
```

## <a name="members"></a>Members

### <a name="public-classes"></a>Clases públicas

|Nombre|Descripción|
|----------|-----------------|
|[reader_writer_lock:: scoped_lock (clase)](#scoped_lock_class)|Un contenedor de a seguro para excepciones que se puede usar para adquirir `reader_writer_lock` bloquear objetos como un escritor.|
|[reader_writer_lock:: scoped_lock_read (clase)](#scoped_lock_read_class)|Un contenedor de a seguro para excepciones que se puede usar para adquirir `reader_writer_lock` bloquear objetos como un lector.|

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[reader_writer_lock](#ctor)|Construye un nuevo objeto `reader_writer_lock`.|
|[~ reader_writer_lock destructor](#dtor)|Destruye el objeto `reader_writer_lock`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[lock](#lock)|Adquiere el bloqueo de lectura y escritura como un escritor.|
|[lock_read](#lock_read)|Adquiere el bloqueo de lectura y escritura como un lector. Si hay escritores, los lectores activos tienen que esperar hasta que se hayan realizado. El lector simplemente registra un interés en el bloqueo y espera a que los escritores lo liberen.|
|[try_lock](#try_lock)|Intenta adquirir el bloqueo de lectura y escritura como escritor sin bloqueos.|
|[try_lock_read](#try_lock_read)|Intenta adquirir el bloqueo de lectura y escritura como lector sin bloqueo.|
|[unlock](#unlock)|Desbloquea el bloqueo de lector-escritor en función de quién lo bloqueó, lector o escritor.|

## <a name="remarks"></a>Observaciones

Para obtener más información, vea [Synchronization Data Structures](../../../parallel/concrt/synchronization-data-structures.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`reader_writer_lock`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrt. h

**Espacio de nombres:** simultaneidad

## <a name="lock"></a>bloquea

Adquiere el bloqueo de lectura y escritura como un escritor.

```cpp
void lock();
```

### <a name="remarks"></a>Observaciones

A menudo es más seguro utilizar la construcción [scoped_lock](#scoped_lock_class) para adquirir y liberar un objeto `reader_writer_lock` como un escritor de una manera segura de excepciones.

Una vez que un escritor intenta adquirir el bloqueo, los lectores futuros se bloquearán hasta que los escritores hayan adquirido y liberado correctamente el bloqueo. Este bloqueo se sesga hacia los escritores y puede privar a los lectores bajo una carga continua de escritores.

Los escritores están encadenados de forma que un escritor que sale del bloqueo libera el siguiente escritor en línea.

Si el contexto ya contiene el bloqueo, se producirá una excepción [improper_lock](improper-lock-class.md) .

## <a name="lock_read"></a>lock_read

Adquiere el bloqueo de lectura y escritura como un lector. Si hay escritores, los lectores activos tienen que esperar hasta que se hayan realizado. El lector simplemente registra un interés en el bloqueo y espera a que los escritores lo liberen.

```cpp
void lock_read();
```

### <a name="remarks"></a>Observaciones

A menudo es más seguro utilizar la construcción [scoped_lock_read](#scoped_lock_read_class) para adquirir y liberar un objeto `reader_writer_lock` como un lector de una manera segura de excepciones.

Si hay escritores en espera del bloqueo, el lector esperará hasta que todos los escritores de la línea hayan adquirido y liberado el bloqueo. Este bloqueo se sesga hacia los escritores y puede privar a los lectores bajo una carga continua de escritores.

## <a name="ctor"></a>reader_writer_lock

Construye un nuevo objeto `reader_writer_lock`.

```cpp
reader_writer_lock();
```

## <a name="dtor"></a>~ reader_writer_lock

Destruye el objeto `reader_writer_lock`.

```cpp
~reader_writer_lock();
```

### <a name="remarks"></a>Observaciones

Se espera que el bloqueo ya no se mantenga cuando se ejecuta el destructor. Permitir que el bloqueo del escritor de lectura se desstructe con el bloqueo conservado tiene como resultado un comportamiento indefinido.

## <a name="scoped_lock_class"></a>reader_writer_lock:: scoped_lock (clase)

Un contenedor de a seguro para excepciones que se puede usar para adquirir `reader_writer_lock` bloquear objetos como un escritor.

```cpp
class scoped_lock;
```

## <a name="scoped_lock_ctor"></a>scoped_lock:: scoped_lock

Construye un objeto `scoped_lock` y adquiere el `reader_writer_lock` objeto pasado en el parámetro `_Reader_writer_lock` como un escritor. Si otro subproceso mantiene el bloqueo, esta llamada se bloqueará.

```cpp
explicit _CRTIMP scoped_lock(reader_writer_lock& _Reader_writer_lock);
```

### <a name="parameters"></a>Parámetros

*_Reader_writer_lock*<br/>
Objeto `reader_writer_lock` que se va a adquirir como escritor.

## <a name="scoped_lock_dtor"></a>scoped_lock:: ~ scoped_lock

Destruye un objeto `reader_writer_lock` y libera el bloqueo proporcionado en su constructor.

```cpp
~scoped_lock();
```

## <a name="scoped_lock_read_class"></a>reader_writer_lock:: scoped_lock_read (clase)

Un contenedor de a seguro para excepciones que se puede usar para adquirir `reader_writer_lock` bloquear objetos como un lector.

```cpp
class scoped_lock_read;
```

## <a name="scoped_lock_read_ctor"></a>scoped_lock_read:: scoped_lock_read

Construye un objeto `scoped_lock_read` y adquiere el `reader_writer_lock` objeto pasado en el parámetro `_Reader_writer_lock` como un lector. Si otro subproceso mantiene el bloqueo como escritor o hay escritores pendientes, esta llamada se bloqueará.

```cpp
explicit _CRTIMP scoped_lock_read(reader_writer_lock& _Reader_writer_lock);
```

### <a name="parameters"></a>Parámetros

*_Reader_writer_lock*<br/>
Objeto `reader_writer_lock` que se va a adquirir como lector.

## <a name="a-namescoped_lock_read_dtor--reader_writer_lockscoped_lock_readscoped_lock_read-destructor"></a><a name="scoped_lock_read_dtor"> reader_writer_lock:: scoped_lock_read:: ~ scoped_lock_read (destructor)

Destruye un objeto `scoped_lock_read` y libera el bloqueo proporcionado en su constructor.

```cpp
~scoped_lock_read();
```

## <a name="try_lock"></a>try_lock

Intenta adquirir el bloqueo de lectura y escritura como escritor sin bloqueos.

### <a name="syntax"></a>Sintaxis

```cpp
bool try_lock();
```

### <a name="return-value"></a>Valor devuelto

Si se ha adquirido el bloqueo, el valor **es true**; de lo contrario, el valor **es false**.

## <a name="try_lock_read"></a>try_lock_read

Intenta adquirir el bloqueo de lectura y escritura como lector sin bloqueo.

```cpp
bool try_lock_read();
```

### <a name="return-value"></a>Valor devuelto

Si se ha adquirido el bloqueo, el valor **es true**; de lo contrario, el valor **es false**.

## <a name="unlock"></a>Pulsa

Desbloquea el bloqueo de lector-escritor en función de quién lo bloqueó, lector o escritor.

```cpp
void unlock();
```

### <a name="remarks"></a>Observaciones

Si hay escritores en espera del bloqueo, la liberación del bloqueo siempre irá al siguiente escritor en orden FIFO. Este bloqueo se sesga hacia los escritores y puede privar a los lectores bajo una carga continua de escritores.

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[critical_section (clase)](critical-section-class.md)
