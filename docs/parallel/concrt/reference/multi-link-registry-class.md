---
title: multi_link_registry (clase)
ms.date: 11/04/2016
f1_keywords:
- multi_link_registry
- AGENTS/concurrency::multi_link_registry
- AGENTS/concurrency::multi_link_registry::multi_link_registry
- AGENTS/concurrency::multi_link_registry::add
- AGENTS/concurrency::multi_link_registry::begin
- AGENTS/concurrency::multi_link_registry::contains
- AGENTS/concurrency::multi_link_registry::count
- AGENTS/concurrency::multi_link_registry::remove
- AGENTS/concurrency::multi_link_registry::set_bound
helpviewer_keywords:
- multi_link_registry class
ms.assetid: b2aa73a8-e8a6-4255-b117-d07530c328b2
ms.openlocfilehash: e22df5ee65d0219a46065044385dca46aac297a3
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142377"
---
# <a name="multi_link_registry-class"></a>multi_link_registry (clase)

El objeto `multi_link_registry` es un `network_link_registry` que administra varios bloques de origen o varios bloques de destino.

## <a name="syntax"></a>Sintaxis

```cpp
template<class _Block>
class multi_link_registry : public network_link_registry<_Block>;
```

### <a name="parameters"></a>Parámetros

*_Block*<br/>
El tipo de datos de bloque que se almacena en el objeto `multi_link_registry`.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[multi_link_registry](#ctor)|Construye un objeto `multi_link_registry`.|
|[~ multi_link_registry destructor](#dtor)|Destruye el objeto `multi_link_registry`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[add](#add)|Agrega un vínculo al objeto `multi_link_registry`. (Invalida [network_link_registry:: Add](network-link-registry-class.md#add)).|
|[begin](#begin)|Devuelve un iterador al primer elemento del objeto `multi_link_registry`. (Invalida [network_link_registry:: Begin](network-link-registry-class.md#begin)).|
|[contains](#contains)|Busca un bloque especificado en el objeto de `multi_link_registry`. (Invalida [network_link_registry:: Contains](network-link-registry-class.md#contains).)|
|[count](#count)|Cuenta el número de elementos del objeto `multi_link_registry`. (Invalida [network_link_registry:: Count](network-link-registry-class.md#count)).|
|[remove](#remove)|Quita un vínculo del objeto `multi_link_registry`. (Invalida [network_link_registry:: Remove](network-link-registry-class.md#remove)).|
|[set_bound](#set_bound)|Establece un límite superior en el número de vínculos que puede contener el objeto de `multi_link_registry`.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[network_link_registry](network-link-registry-class.md)

`multi_link_registry`

## <a name="requirements"></a>Requisitos

**Encabezado:** agents.h

**Espacio de nombres:** simultaneidad

## <a name="add"></a>agréguela

Agrega un vínculo al objeto `multi_link_registry`.

```cpp
virtual void add(_EType _Link);
```

### <a name="parameters"></a>Parámetros

*_Link*<br/>
Un puntero a un bloque que se va a agregar.

### <a name="remarks"></a>Observaciones

El método produce una excepción [invalid_link_target](invalid-link-target-class.md) si el vínculo ya está presente en el registro o si ya se ha establecido un enlazado con la función `set_bound` y se ha quitado un vínculo.

## <a name="begin"></a>inicia

Devuelve un iterador al primer elemento del objeto `multi_link_registry`.

```cpp
virtual iterator begin();
```

### <a name="return-value"></a>Valor devuelto

Iterador que direcciona el primer elemento del objeto `multi_link_registry`.

### <a name="remarks"></a>Observaciones

El estado final se indica mediante un vínculo `NULL`.

## <a name="contains"></a>tuviera

Busca un bloque especificado en el objeto de `multi_link_registry`.

```cpp
virtual bool contains(_EType _Link);
```

### <a name="parameters"></a>Parámetros

*_Link*<br/>
Puntero a un bloque que se va a buscar en el objeto `multi_link_registry`.

### <a name="return-value"></a>Valor devuelto

**true** si se encontró el bloque especificado; en caso contrario, **false** .

## <a name="count"></a>contabiliza

Cuenta el número de elementos del objeto `multi_link_registry`.

```cpp
virtual size_t count();
```

### <a name="return-value"></a>Valor devuelto

Número de elementos del objeto `multi_link_registry`.

## <a name="ctor"></a>multi_link_registry

Construye un objeto `multi_link_registry`.

```cpp
multi_link_registry();
```

## <a name="dtor"></a>~ multi_link_registry

Destruye el objeto `multi_link_registry`.

```cpp
virtual ~multi_link_registry();
```

### <a name="remarks"></a>Observaciones

El método produce una excepción [invalid_operation](invalid-operation-class.md) si se llama antes de que se quiten todos los vínculos.

## <a name="remove"></a>retirar

Quita un vínculo del objeto `multi_link_registry`.

```cpp
virtual bool remove(_EType _Link);
```

### <a name="parameters"></a>Parámetros

*_Link*<br/>
Un puntero a un bloque que se va a quitar, si se encuentra.

### <a name="return-value"></a>Valor devuelto

**true** si el vínculo se encontró y se quitó; de lo contrario, **false** .

## <a name="set_bound"></a>set_bound

Establece un límite superior en el número de vínculos que puede contener el objeto de `multi_link_registry`.

```cpp
void set_bound(size_t _MaxLinks);
```

### <a name="parameters"></a>Parámetros

*_MaxLinks*<br/>
Número máximo de vínculos que puede contener el objeto de `multi_link_registry`.

### <a name="remarks"></a>Observaciones

Una vez establecido un enlazado, al desvincular una entrada, el objeto `multi_link_registry` entra en un estado inmutable en el que las llamadas posteriores a `add` producirán una excepción `invalid_link_target`.

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[single_link_registry (clase)](single-link-registry-class.md)
