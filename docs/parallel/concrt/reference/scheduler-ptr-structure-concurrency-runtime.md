---
title: Estructura scheduler_ptr
ms.date: 11/04/2016
f1_keywords:
- scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::get
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::operator bool
ms.assetid: e88c84af-c306-476d-aef1-f42a0fa0a80f
ms.openlocfilehash: 60d71a26e5dffcadfb900ef15c26a6d9dc6d6f8b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358769"
---
# <a name="scheduler_ptr-structure"></a>Estructura scheduler_ptr

Representa un puntero a un programador. Esta clase existe para permitir la especificación de una duración compartida mediante shared_ptr o simplemente una referencia sin formato mediante el uso de puntero sin formato.

## <a name="syntax"></a>Sintaxis

```cpp
struct scheduler_ptr;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[scheduler_ptr::scheduler_ptr](#ctor)|Sobrecargado. Crea un puntero de programador que va de shared_ptr al programador|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[scheduler_ptr::get](#get)|Devuelve el puntero sin formato al programador|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[scheduler_ptr::operador bool](#operator_bool)|Prueba si el puntero del programador no es null|
|[scheduler_ptr::operador-&gt;](#operator_ptr)|Se comporta como un puntero|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`scheduler_ptr`

## <a name="requirements"></a>Requisitos

**Encabezado:** pplinterface.h

**Espacio de nombres:** simultaneidad

## <a name="scheduler_ptrget-method"></a><a name="get"></a>scheduler_ptr::get Método

Devuelve el puntero sin formato al programador.

```cpp
scheduler_interface* get() const;
```

### <a name="return-value"></a>Valor devuelto

## <a name="scheduler_ptroperator-bool"></a><a name="operator_bool"></a>scheduler_ptr::operador bool

Comprueba si el puntero del programador no es nulo.

```cpp
operator bool() const;
```

## <a name="scheduler_ptroperator-gt"></a><a name="operator_ptr"></a>scheduler_ptr::operador-&gt;

Se comporta como un puntero.

```cpp
scheduler_interface* operator->() const;
```

### <a name="return-value"></a>Valor devuelto

## <a name="scheduler_ptrscheduler_ptr-constructor"></a><a name="ctor"></a>Constructor scheduler_ptr::scheduler_ptr

Crea un puntero del programador desde shared_ptr al programador.

```cpp
explicit scheduler_ptr(std::shared_ptr<scheduler_interface> scheduler);
explicit scheduler_ptr(_In_opt_ scheduler_interface* pScheduler);
```

### <a name="parameters"></a>Parámetros

*Programador*<br/>
El programador que se convertirá.

*pScheduler*<br/>
El puntero del programador que se desea convertir.

## <a name="see-also"></a>Consulte también

[espacio de nombres de simultaneidad](concurrency-namespace.md)
