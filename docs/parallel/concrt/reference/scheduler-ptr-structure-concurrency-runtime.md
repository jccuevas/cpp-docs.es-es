---
title: scheduler_ptr (estructura)
ms.date: 11/04/2016
f1_keywords:
- scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::get
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::operator bool
ms.assetid: e88c84af-c306-476d-aef1-f42a0fa0a80f
ms.openlocfilehash: 2373fe3bc8cac501d1b6b32ca66996eff47ba6f3
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57295050"
---
# <a name="schedulerptr-structure"></a>scheduler_ptr (estructura)

Representa un puntero a un programador. Esta clase existe para permitir la especificación de una duración compartida mediante shared_ptr o simplemente una referencia sin formato mediante un puntero sin formato.

## <a name="syntax"></a>Sintaxis

```
struct scheduler_ptr;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[scheduler_ptr::scheduler_ptr](#ctor)|Sobrecargado. Crea un puntero de programador que va de shared_ptr al programador|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[scheduler_ptr::get](#get)|Devuelve el puntero sin formato al programador|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[scheduler_ptr::operator bool](#operator_bool)|Prueba si el puntero del programador no es null|
|[scheduler_ptr::operator-&gt;](#operator_ptr)|Se comporta como un puntero|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`scheduler_ptr`

## <a name="requirements"></a>Requisitos

**Encabezado:** pplinterface.h

**Espacio de nombres:** simultaneidad

##  <a name="get"></a>  scheduler_ptr::Get (método)

Devuelve el puntero sin formato al programador.

```
scheduler_interface* get() const;
```

### <a name="return-value"></a>Valor devuelto

##  <a name="operator_bool"></a>  scheduler_ptr::operator bool

Comprueba si el puntero del programador es distinto de null.

```
operator bool() const;
```

##  <a name="operator_ptr"></a>  scheduler_ptr::operator-&gt;

Se comporta como un puntero.

```
scheduler_interface* operator->() const;
```

### <a name="return-value"></a>Valor devuelto

##  <a name="ctor"></a>  scheduler_ptr::scheduler_ptr Constructor

Crea un puntero de programador de shared_ptr al programador.

```
explicit scheduler_ptr(std::shared_ptr<scheduler_interface> scheduler);
explicit scheduler_ptr(_In_opt_ scheduler_interface* pScheduler);
```

### <a name="parameters"></a>Parámetros

*scheduler*<br/>
El programador para convertir.

*pScheduler*<br/>
Para convertir el puntero del programador.

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)
