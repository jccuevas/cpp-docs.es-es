---
title: network_link_registry (Clase)
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
ms.openlocfilehash: 2537ed857651b5210b104a270b3d827246b8339a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385237"
---
# <a name="networklinkregistry-class"></a>network_link_registry (Clase)

La clase base abstracta `network_link_registry` que administra los vínculos entre los bloques de origen y de destino.

## <a name="syntax"></a>Sintaxis

```
template<class _Block>
class network_link_registry;
```

#### <a name="parameters"></a>Parámetros

*_Block*<br/>
Tipo de los datos del bloque que se almacenan en el `network_link_registry`.

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Name|Descripción|
|----------|-----------------|
|`const_pointer`|Un tipo que proporciona un puntero a un `const` elemento en un `network_link_registry` objeto.|
|`const_reference`|Un tipo que proporciona una referencia a un `const` elemento almacenado en un `network_link_registry` objeto para leer y realizar operaciones const.|
|`iterator`|Un tipo que proporciona un iterador que puede leer o modificar cualquier elemento en un `network_link_registry` objeto.|
|`type`|Un tipo que representa el tipo de bloque que se almacenan en la `network_link_registry` objeto.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[add](#add)|Cuando se invalida en una clase derivada, agrega un vínculo a la `network_link_registry` objeto.|
|[begin](#begin)|Cuando se invalida en una clase derivada, devuelve un iterador al primer elemento en el `network_link_registry` objeto.|
|[contains](#contains)|Cuando se invalida en una clase derivada, busca el `network_link_registry` objeto para un bloque especificado.|
|[count](#count)|Cuando se invalida en una clase derivada, devuelve el número de elementos de la `network_link_registry` objeto.|
|[remove](#remove)|Cuando se invalida en una clase derivada, quita un bloque especificado desde el `network_link_registry` objeto.|

## <a name="remarks"></a>Comentarios

El `network link registry` no es seguro para el acceso simultáneo.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`network_link_registry`

## <a name="requirements"></a>Requisitos

**Encabezado:** agents.h

**Espacio de nombres:** simultaneidad

##  <a name="add"></a> Agregar

Cuando se invalida en una clase derivada, agrega un vínculo a la `network_link_registry` objeto.

```
virtual void add(_EType _Link) = 0;
```

### <a name="parameters"></a>Parámetros

*_Link*<br/>
Un puntero a un bloque que se va a agregar.

##  <a name="begin"></a> comenzar

Cuando se invalida en una clase derivada, devuelve un iterador al primer elemento en el `network_link_registry` objeto.

```
virtual iterator begin() = 0;
```

### <a name="return-value"></a>Valor devuelto

Un iterador que direcciona el primer elemento en el `network_link_registry` objeto.

### <a name="remarks"></a>Comentarios

Indica el estado final del iterador por un `NULL` vínculo.

##  <a name="contains"></a> Contiene

Cuando se invalida en una clase derivada, busca el `network_link_registry` objeto para un bloque especificado.

```
virtual bool contains(_EType _Link) = 0;
```

### <a name="parameters"></a>Parámetros

*_Link*<br/>
Un puntero a un bloque que se va a buscar en el `network_link_registry` objeto.

### <a name="return-value"></a>Valor devuelto

**True** si se encontró el bloque, **false** en caso contrario.

##  <a name="count"></a> recuento

Cuando se invalida en una clase derivada, devuelve el número de elementos de la `network_link_registry` objeto.

```
virtual size_t count() = 0;
```

### <a name="return-value"></a>Valor devuelto

El número de elementos en el `network_link_registry` objeto.

##  <a name="remove"></a> Quitar

Cuando se invalida en una clase derivada, quita un bloque especificado desde el `network_link_registry` objeto.

```
virtual bool remove(_EType _Link) = 0;
```

### <a name="parameters"></a>Parámetros

*_Link*<br/>
Un puntero a un bloque que se va a quitar, si se encuentra.

### <a name="return-value"></a>Valor devuelto

**True** si el vínculo ha encontrado y eliminado, **false** en caso contrario.

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[single_link_registry (clase)](single-link-registry-class.md)<br/>
[multi_link_registry (clase)](multi-link-registry-class.md)
