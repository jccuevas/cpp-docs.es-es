---
title: Estructura de scheduler_ptr
ms.date: 11/04/2016
f1_keywords:
- scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::get
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::operator bool
ms.assetid: e88c84af-c306-476d-aef1-f42a0fa0a80f
ms.openlocfilehash: fd044a6255a17882c26183223f71564f98c9f7b2
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142773"
---
# <a name="scheduler_ptr-structure"></a>Estructura de scheduler_ptr

Representa un puntero a un programador. Esta clase existe para permitir la especificación de una duración compartida mediante shared_ptr o simplemente una referencia sin formato mediante el puntero sin formato.

## <a name="syntax"></a>Sintaxis

```cpp
struct scheduler_ptr;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[scheduler_ptr:: scheduler_ptr](#ctor)|Sobrecargado. Crea un puntero de programador que va de shared_ptr al programador|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[scheduler_ptr:: get](#get)|Devuelve el puntero sin formato al programador|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[scheduler_ptr:: Operator bool](#operator_bool)|Prueba si el puntero del programador no es null|
|[scheduler_ptr:: Operator-&gt;](#operator_ptr)|Se comporta como un puntero|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`scheduler_ptr`

## <a name="requirements"></a>Requisitos

**Encabezado:** pplinterface. h

**Espacio de nombres:** simultaneidad

## <a name="get"></a>scheduler_ptr:: get (método)

Devuelve el puntero sin formato al programador.

```cpp
scheduler_interface* get() const;
```

### <a name="return-value"></a>Valor devuelto

## <a name="operator_bool"></a>scheduler_ptr:: Operator bool

Comprueba si el puntero del programador no es NULL.

```cpp
operator bool() const;
```

## <a name="operator_ptr"></a>scheduler_ptr:: Operator-&gt;

Se comporta como un puntero.

```cpp
scheduler_interface* operator->() const;
```

### <a name="return-value"></a>Valor devuelto

## <a name="ctor"></a>scheduler_ptr:: scheduler_ptr (constructor)

Crea un puntero de programador de shared_ptr a Scheduler.

```cpp
explicit scheduler_ptr(std::shared_ptr<scheduler_interface> scheduler);
explicit scheduler_ptr(_In_opt_ scheduler_interface* pScheduler);
```

### <a name="parameters"></a>Parámetros

*aquél*<br/>
Programador que se va a convertir.

*pScheduler*<br/>
Puntero de programador que se va a convertir.

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)
