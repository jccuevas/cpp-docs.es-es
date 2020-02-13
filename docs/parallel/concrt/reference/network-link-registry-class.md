---
title: network_link_registry (clase)
ms.date: 11/04/2016
f1_keywords:
- network_link_registry
- AGENTS/concurrency::network_link_registry
- AGENTS/concurrency::network_link_registry::add
- AGENTS/concurrency::network_link_registry::begin
- AGENTS/concurrency::network_link_registry::contains
- AGENTS/concurrency::network_link_registry::count
- AGENTS/concurrency::network_link_registry::remove
helpviewer_keywords:
- network_link_registry class
ms.assetid: 3e7b4097-09f1-4252-964e-b15b8f7f7fc6
ms.openlocfilehash: 430190c11ec06a4f26eb9d8c4237552848420ad7
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77138888"
---
# <a name="network_link_registry-class"></a>network_link_registry (clase)

La clase base abstracta `network_link_registry` que administra los vínculos entre los bloques de origen y de destino.

## <a name="syntax"></a>Sintaxis

```cpp
template<class _Block>
class network_link_registry;
```

### <a name="parameters"></a>Parámetros

*_Block*<br/>
El tipo de datos de bloque que se almacena en el `network_link_registry`.

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Typedefs públicos

|Nombre|Descripción|
|----------|-----------------|
|`const_pointer`|Un tipo que proporciona un puntero a un `const` elemento de un objeto `network_link_registry`.|
|`const_reference`|Un tipo que proporciona una referencia a un elemento `const` almacenado en un objeto `network_link_registry` para leer y realizar operaciones const.|
|`iterator`|Un tipo que proporciona un iterador que puede leer o modificar cualquier elemento de un objeto de `network_link_registry`.|
|`type`|Tipo que representa el tipo de bloque almacenado en el objeto `network_link_registry`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[add](#add)|Cuando se reemplaza en una clase derivada, agrega un vínculo al objeto `network_link_registry`.|
|[begin](#begin)|Cuando se reemplaza en una clase derivada, devuelve un iterador al primer elemento del objeto `network_link_registry`.|
|[contains](#contains)|Cuando se reemplaza en una clase derivada, busca un bloque especificado en el objeto `network_link_registry`.|
|[count](#count)|Cuando se reemplaza en una clase derivada, devuelve el número de elementos del objeto `network_link_registry`.|
|[remove](#remove)|Cuando se reemplaza en una clase derivada, quita un bloque especificado del objeto `network_link_registry`.|

## <a name="remarks"></a>Observaciones

El `network link registry` no es seguro para el acceso simultáneo.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`network_link_registry`

## <a name="requirements"></a>Requisitos

**Encabezado:** agents.h

**Espacio de nombres:** simultaneidad

## <a name="add"></a>agréguela

Cuando se reemplaza en una clase derivada, agrega un vínculo al objeto `network_link_registry`.

```cpp
virtual void add(_EType _Link) = 0;
```

### <a name="parameters"></a>Parámetros

*_Link*<br/>
Un puntero a un bloque que se va a agregar.

## <a name="begin"></a>inicia

Cuando se reemplaza en una clase derivada, devuelve un iterador al primer elemento del objeto `network_link_registry`.

```cpp
virtual iterator begin() = 0;
```

### <a name="return-value"></a>Valor devuelto

Iterador que direcciona el primer elemento del objeto `network_link_registry`.

### <a name="remarks"></a>Observaciones

El estado final del iterador se indica mediante un vínculo de `NULL`.

## <a name="contains"></a>tuviera

Cuando se reemplaza en una clase derivada, busca un bloque especificado en el objeto `network_link_registry`.

```cpp
virtual bool contains(_EType _Link) = 0;
```

### <a name="parameters"></a>Parámetros

*_Link*<br/>
Un puntero a un bloque que se está buscando en el objeto `network_link_registry`.

### <a name="return-value"></a>Valor devuelto

**true** si se encontró el bloque; de lo contrario, **false** .

## <a name="count"></a>contabiliza

Cuando se reemplaza en una clase derivada, devuelve el número de elementos del objeto `network_link_registry`.

```cpp
virtual size_t count() = 0;
```

### <a name="return-value"></a>Valor devuelto

Número de elementos del objeto `network_link_registry`.

## <a name="remove"></a>retirar

Cuando se reemplaza en una clase derivada, quita un bloque especificado del objeto `network_link_registry`.

```cpp
virtual bool remove(_EType _Link) = 0;
```

### <a name="parameters"></a>Parámetros

*_Link*<br/>
Un puntero a un bloque que se va a quitar, si se encuentra.

### <a name="return-value"></a>Valor devuelto

**true** si el vínculo se encontró y se quitó; de lo contrario, **false** .

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[single_link_registry (clase)](single-link-registry-class.md)<br/>
[multi_link_registry (clase)](multi-link-registry-class.md)
