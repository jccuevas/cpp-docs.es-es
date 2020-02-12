---
title: single_link_registry (clase)
ms.date: 11/04/2016
f1_keywords:
- single_link_registry
- AGENTS/concurrency::single_link_registry
- AGENTS/concurrency::single_link_registry::single_link_registry
- AGENTS/concurrency::single_link_registry::add
- AGENTS/concurrency::single_link_registry::begin
- AGENTS/concurrency::single_link_registry::contains
- AGENTS/concurrency::single_link_registry::count
- AGENTS/concurrency::single_link_registry::remove
helpviewer_keywords:
- single_link_registry class
ms.assetid: 09540a4e-c34e-4ff9-af49-21b8612b6ab3
ms.openlocfilehash: c29caf6d31df316e80b15fe6827c81e34ece8a18
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142724"
---
# <a name="single_link_registry-class"></a>single_link_registry (clase)

El objeto `single_link_registry` es un `network_link_registry` que administra un solo bloque de origen o bloque de destino.

## <a name="syntax"></a>Sintaxis

```cpp
template<class _Block>
class single_link_registry : public network_link_registry<_Block>;
```

### <a name="parameters"></a>Parámetros

*_Block*<br/>
El tipo de datos de bloque que se almacena en el objeto `single_link_registry`.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[single_link_registry](#ctor)|Construye un objeto `single_link_registry`.|
|[~ single_link_registry destructor](#dtor)|Destruye el objeto `single_link_registry`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[add](#add)|Agrega un vínculo al objeto `single_link_registry`. (Invalida [network_link_registry:: Add](network-link-registry-class.md#add)).|
|[begin](#begin)|Devuelve un iterador al primer elemento del objeto `single_link_registry`. (Invalida [network_link_registry:: Begin](network-link-registry-class.md#begin)).|
|[contains](#contains)|Busca un bloque especificado en el objeto de `single_link_registry`. (Invalida [network_link_registry:: Contains](network-link-registry-class.md#contains).)|
|[count](#count)|Cuenta el número de elementos del objeto `single_link_registry`. (Invalida [network_link_registry:: Count](network-link-registry-class.md#count)).|
|[remove](#remove)|Quita un vínculo del objeto `single_link_registry`. (Invalida [network_link_registry:: Remove](network-link-registry-class.md#remove)).|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[network_link_registry](network-link-registry-class.md)

`single_link_registry`

## <a name="requirements"></a>Requisitos

**Encabezado:** agents.h

**Espacio de nombres:** simultaneidad

## <a name="add"></a>agréguela

Agrega un vínculo al objeto `single_link_registry`.

```cpp
virtual void add(_EType _Link);
```

### <a name="parameters"></a>Parámetros

*_Link*<br/>
Un puntero a un bloque que se va a agregar.

### <a name="remarks"></a>Observaciones

El método produce una excepción [invalid_link_target](invalid-link-target-class.md) si ya existe un vínculo en este registro.

## <a name="begin"></a>inicia

Devuelve un iterador al primer elemento del objeto `single_link_registry`.

```cpp
virtual iterator begin();
```

### <a name="return-value"></a>Valor devuelto

Iterador que direcciona el primer elemento del objeto `single_link_registry`.

### <a name="remarks"></a>Observaciones

El estado final se indica mediante un vínculo `NULL`.

## <a name="contains"></a>tuviera

Busca un bloque especificado en el objeto de `single_link_registry`.

```cpp
virtual bool contains(_EType _Link);
```

### <a name="parameters"></a>Parámetros

*_Link*<br/>
Puntero a un bloque que se va a buscar en el objeto `single_link_registry`.

### <a name="return-value"></a>Valor devuelto

**true** si se encontró el vínculo; en caso contrario, **false** .

## <a name="count"></a>contabiliza

Cuenta el número de elementos del objeto `single_link_registry`.

```cpp
virtual size_t count();
```

### <a name="return-value"></a>Valor devuelto

Número de elementos del objeto `single_link_registry`.

## <a name="remove"></a>retirar

Quita un vínculo del objeto `single_link_registry`.

```cpp
virtual bool remove(_EType _Link);
```

### <a name="parameters"></a>Parámetros

*_Link*<br/>
Un puntero a un bloque que se va a quitar, si se encuentra.

### <a name="return-value"></a>Valor devuelto

**true** si el vínculo se encontró y se quitó; de lo contrario, **false** .

## <a name="ctor"></a>single_link_registry

Construye un objeto `single_link_registry`.

```cpp
single_link_registry();
```

## <a name="dtor"></a>~ single_link_registry

Destruye el objeto `single_link_registry`.

```cpp
virtual ~single_link_registry();
```

### <a name="remarks"></a>Observaciones

El método produce una excepción [invalid_operation](invalid-operation-class.md) si se llama antes de que se quite el vínculo.

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[multi_link_registry (clase)](multi-link-registry-class.md)
