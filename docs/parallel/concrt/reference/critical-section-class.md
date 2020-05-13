---
title: critical_section (Clase)
ms.date: 11/04/2016
f1_keywords:
- critical_section
- CONCRT/concurrency::critical_section
- CONCRT/concurrency::critical_section::critical_section::scoped_lock Class
- CONCRT/concurrency::critical_section::critical_section
- CONCRT/concurrency::critical_section::lock
- CONCRT/concurrency::critical_section::native_handle
- CONCRT/concurrency::critical_section::try_lock
- CONCRT/concurrency::critical_section::try_lock_for
- CONCRT/concurrency::critical_section::unlock
helpviewer_keywords:
- critical_section class
ms.assetid: fa3c89d6-be5d-4d1b-bddb-8232814e6cf6
ms.openlocfilehash: 24f96282a7728c6db6e0b05d36406f15383913f3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372677"
---
# <a name="critical_section-class"></a>critical_section (Clase)

Una exclusión mutua no reentrante que es explícitamente consciente del runtime de simultaneidad.

## <a name="syntax"></a>Sintaxis

```cpp
class critical_section;
```

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Nombre|Descripción|
|----------|-----------------|
|`native_handle_type`|Referencia a un objeto `critical_section`.|

### <a name="public-classes"></a>Clases públicas

|Nombre|Descripción|
|----------|-----------------|
|[critical_section::scoped_lock (Clase)](#critical_section__scoped_lock_class)|Un contenedor RAII seguro `critical_section` para excepciones para un objeto.|

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[critical_section](#ctor)|Construye una nueva sección crítica.|
|[Destructor de critical_section](#dtor)|Destruye una sección crítica.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[Cerradura](#lock)|Adquiere esta sección crítica.|
|[native_handle](#native_handle)|Devuelve un identificador nativo específico de la plataforma, si existe.|
|[try_lock](#try_lock)|Intenta adquirir la cerradura sin bloquearla.|
|[try_lock_for](#try_lock_for)|Intenta adquirir el bloqueo sin bloquear durante un número específico de milisegundos.|
|[Desbloquear](#unlock)|Desbloquea la sección crítica.|

## <a name="remarks"></a>Observaciones

Para obtener más información, consulte Estructuras de datos de [sincronización](../../../parallel/concrt/synchronization-data-structures.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`critical_section`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrt.h

**Espacio de nombres:** simultaneidad

## <a name="critical_section"></a><a name="ctor"></a>Critical_section

Construye una nueva sección crítica.

```cpp
critical_section();
```

## <a name="critical_section"></a><a name="dtor"></a>Critical_section

Destruye una sección crítica.

```cpp
~critical_section();
```

### <a name="remarks"></a>Observaciones

Se espera que el bloqueo ya no se mantenga cuando se ejecuta el destructor. Permitir que la sección crítica se destruya con el bloqueo todavía retenido da como resultado un comportamiento indefinido.

## <a name="lock"></a><a name="lock"></a>Cerradura

Adquiere esta sección crítica.

```cpp
void lock();
```

### <a name="remarks"></a>Observaciones

A menudo es más seguro utilizar la `critical_section` construcción [scoped_lock](#critical_section__scoped_lock_class) para adquirir y liberar un objeto de una manera segura y segura.

Si el contexto de llamada ya mantiene el bloqueo, se producirá una [excepción improper_lock.](improper-lock-class.md)

## <a name="native_handle"></a><a name="native_handle"></a>native_handle

Devuelve un identificador nativo específico de la plataforma, si existe.

```cpp
native_handle_type native_handle();
```

### <a name="return-value"></a>Valor devuelto

Una referencia a la sección crítica.

### <a name="remarks"></a>Observaciones

Un `critical_section` objeto no está asociado a un identificador nativo específico de la plataforma para el sistema operativo Windows. El método simplemente devuelve una referencia al propio objeto.

## <a name="critical_sectionscoped_lock-class"></a><a name="critical_section__scoped_lock_class"></a>clase critical_section::scoped_lock

Un contenedor RAII seguro `critical_section` para excepciones para un objeto.

```cpp
class scoped_lock;
```

## <a name="scoped_lockscoped_lock"></a><a name="critical_section__scoped_lock_ctor"></a>scoped_lock::scoped_lock

Construye un `scoped_lock` objeto y `critical_section` adquiere el `_Critical_section` objeto pasado en el parámetro. Si otro subproceso mantiene la sección crítica, esta llamada se bloqueará.

```cpp
explicit _CRTIMP scoped_lock(critical_section& _Critical_section);
```

### <a name="parameters"></a>Parámetros

*_Critical_section*<br/>
La sección crítica para bloquear.

## <a name="scoped_lockscoped_lock"></a><a name="critical_section__scoped_lock_dtor"></a>scoped_lock::scoped_lock

Destruye un `scoped_lock` objeto y libera la sección crítica proporcionada en su constructor.

```cpp
~scoped_lock();
```

## <a name="try_lock"></a><a name="try_lock"></a>try_lock

Intenta adquirir la cerradura sin bloquearla.

```cpp
bool try_lock();
```

### <a name="return-value"></a>Valor devuelto

Si se adquirió el bloqueo, el valor **true**; de lo contrario, el valor **false**.

## <a name="try_lock_for"></a><a name="try_lock_for"></a>try_lock_for

Intenta adquirir el bloqueo sin bloquear durante un número específico de milisegundos.

```cpp
bool try_lock_for(unsigned int _Timeout);
```

### <a name="parameters"></a>Parámetros

*_Timeout*<br/>
El número de milisegundos que hay que esperar antes de agotar el tiempo de espera.

### <a name="return-value"></a>Valor devuelto

Si se adquirió el bloqueo, el valor **true**; de lo contrario, el valor **false**.

## <a name="unlock"></a><a name="unlock"></a>Desbloquear

Desbloquea la sección crítica.

```cpp
void unlock();
```

## <a name="see-also"></a>Consulte también

[espacio de nombres de simultaneidad](concurrency-namespace.md)<br/>
[Clase reader_writer_lock](reader-writer-lock-class.md)
