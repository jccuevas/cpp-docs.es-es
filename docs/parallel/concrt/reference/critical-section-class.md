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
ms.openlocfilehash: aef3ae6100133374cb89098f118c447effafd840
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78867177"
---
# <a name="critical_section-class"></a>critical_section (Clase)

Una exclusión mutua no reentrante que es explícitamente consciente del runtime de simultaneidad.

## <a name="syntax"></a>Sintaxis

```cpp
class critical_section;
```

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Nombre|Descripción|
|----------|-----------------|
|`native_handle_type`|Referencia a un objeto `critical_section`.|

### <a name="public-classes"></a>Clases públicas

|Nombre|Descripción|
|----------|-----------------|
|[critical_section:: scoped_lock (clase)](#critical_section__scoped_lock_class)|Un contenedor de un objeto de `critical_section` seguro para excepciones.|

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[critical_section](#ctor)|Construye una nueva sección crítica.|
|[~ critical_section destructor](#dtor)|Destruye una sección crítica.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[lock](#lock)|Adquiere esta sección crítica.|
|[native_handle](#native_handle)|Devuelve un identificador nativo específico de la plataforma, si existe uno.|
|[try_lock](#try_lock)|Intenta adquirir el bloqueo sin bloqueos.|
|[try_lock_for](#try_lock_for)|Intenta adquirir el bloqueo sin bloqueos durante un número específico de milisegundos.|
|[unlock](#unlock)|Desbloquea la sección crítica.|

## <a name="remarks"></a>Observaciones

Para obtener más información, vea [Synchronization Data Structures](../../../parallel/concrt/synchronization-data-structures.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`critical_section`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrt. h

**Espacio de nombres:** simultaneidad

## <a name="ctor"></a>critical_section

Construye una nueva sección crítica.

```cpp
critical_section();
```

## <a name="dtor"></a>~ critical_section

Destruye una sección crítica.

```cpp
~critical_section();
```

### <a name="remarks"></a>Observaciones

Se espera que el bloqueo ya no se mantenga cuando se ejecuta el destructor. Permitir que la sección crítica se desstructe con el bloqueo conservado tiene como resultado un comportamiento indefinido.

## <a name="lock"></a>bloquea

Adquiere esta sección crítica.

```cpp
void lock();
```

### <a name="remarks"></a>Observaciones

A menudo es más seguro utilizar la construcción [scoped_lock](#critical_section__scoped_lock_class) para adquirir y liberar un objeto `critical_section` de una manera segura de excepciones.

Si el contexto ya contiene el bloqueo, se producirá una excepción [improper_lock](improper-lock-class.md) .

## <a name="native_handle"></a>native_handle

Devuelve un identificador nativo específico de la plataforma, si existe uno.

```cpp
native_handle_type native_handle();
```

### <a name="return-value"></a>Valor devuelto

Referencia a la sección crítica.

### <a name="remarks"></a>Observaciones

Un objeto `critical_section` no está asociado a un identificador nativo específico de la plataforma para el sistema operativo Windows. El método simplemente devuelve una referencia al propio objeto.

## <a name="critical_section__scoped_lock_class"></a>critical_section:: scoped_lock (clase)

Un contenedor de un objeto de `critical_section` seguro para excepciones.

```cpp
class scoped_lock;
```

## <a name="critical_section__scoped_lock_ctor"></a>scoped_lock:: scoped_lock

Construye un objeto `scoped_lock` y adquiere el `critical_section` objeto pasado en el parámetro `_Critical_section`. Si otro subproceso contiene la sección crítica, esta llamada se bloqueará.

```cpp
explicit _CRTIMP scoped_lock(critical_section& _Critical_section);
```

### <a name="parameters"></a>Parámetros

*_Critical_section*<br/>
Sección crítica que se va a bloquear.

## <a name="critical_section__scoped_lock_dtor"></a>scoped_lock:: ~ scoped_lock

Destruye un objeto `scoped_lock` y libera la sección crítica proporcionada en su constructor.

```cpp
~scoped_lock();
```

## <a name="try_lock"></a>try_lock

Intenta adquirir el bloqueo sin bloqueos.

```cpp
bool try_lock();
```

### <a name="return-value"></a>Valor devuelto

Si se ha adquirido el bloqueo, el valor **es true**; de lo contrario, el valor **es false**.

## <a name="try_lock_for"></a>try_lock_for

Intenta adquirir el bloqueo sin bloqueos durante un número específico de milisegundos.

```cpp
bool try_lock_for(unsigned int _Timeout);
```

### <a name="parameters"></a>Parámetros

*_Timeout*<br/>
Número de milisegundos que se va a esperar antes de que se agote el tiempo de espera.

### <a name="return-value"></a>Valor devuelto

Si se ha adquirido el bloqueo, el valor **es true**; de lo contrario, el valor **es false**.

## <a name="unlock"></a>Pulsa

Desbloquea la sección crítica.

```cpp
void unlock();
```

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[reader_writer_lock (clase)](reader-writer-lock-class.md)
