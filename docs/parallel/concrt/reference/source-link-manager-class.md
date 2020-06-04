---
title: source_link_manager (clase)
ms.date: 11/04/2016
f1_keywords:
- source_link_manager
- AGENTS/concurrency::source_link_manager
- AGENTS/concurrency::source_link_manager::source_link_manager
- AGENTS/concurrency::source_link_manager::add
- AGENTS/concurrency::source_link_manager::begin
- AGENTS/concurrency::source_link_manager::contains
- AGENTS/concurrency::source_link_manager::count
- AGENTS/concurrency::source_link_manager::reference
- AGENTS/concurrency::source_link_manager::register_target_block
- AGENTS/concurrency::source_link_manager::release
- AGENTS/concurrency::source_link_manager::remove
- AGENTS/concurrency::source_link_manager::set_bound
helpviewer_keywords:
- source_link_manager class
ms.assetid: 287487cf-e0fe-4c35-aa3c-24f081d1ddae
ms.openlocfilehash: 35c7cc72520cdb0675abf9c15574a49e33741d0b
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142696"
---
# <a name="source_link_manager-class"></a>source_link_manager (clase)

El objeto `source_link_manager` administra los vínculos de red del bloque de mensajería para los bloques `ISource`.

## <a name="syntax"></a>Sintaxis

```cpp
template<class _LinkRegistry>
class source_link_manager;
```

### <a name="parameters"></a>Parámetros

*_LinkRegistry*<br/>
El registro de vínculos de red.

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Typedefs públicos

|Nombre|Descripción|
|----------|-----------------|
|`const_pointer`|Un tipo que proporciona un puntero a un `const` elemento de un objeto `source_link_manager`.|
|`const_reference`|Un tipo que proporciona una referencia a un elemento `const` almacenado en un objeto `source_link_manager` para leer y realizar operaciones const.|
|`iterator`|Un tipo que proporciona un iterador que puede leer o modificar cualquier elemento del objeto `source_link_manager`.|
|`type`|El tipo de registro de vínculo administrado por el objeto `source_link_manager`.|

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[source_link_manager](#ctor)|Construye un objeto `source_link_manager`.|
|[~ source_link_manager destructor](#dtor)|Destruye el objeto `source_link_manager`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[add](#add)|Agrega un vínculo de origen al objeto de `source_link_manager`.|
|[begin](#begin)|Devuelve un iterador al primer elemento del objeto `source_link_manager`.|
|[contains](#contains)|Busca un bloque especificado en el `network_link_registry` dentro de este objeto `source_link_manager`.|
|[count](#count)|Cuenta el número de bloques vinculados en el objeto de `source_link_manager`.|
|[reference](#reference)|Adquiere una referencia en el objeto `source_link_manager`.|
|[register_target_block](#register_target_block)|Registra el bloque de destino que contiene este objeto `source_link_manager`.|
|[release](#release)|Libera la referencia en el objeto `source_link_manager`.|
|[remove](#remove)|Quita un vínculo del objeto `source_link_manager`.|
|[set_bound](#set_bound)|Establece el número máximo de vínculos de origen que se pueden agregar a este objeto `source_link_manager`.|

## <a name="remarks"></a>Observaciones

Actualmente, se cuentan las referencias de los bloques de origen. Se trata de un contenedor de un objeto `network_link_registry` que permite el acceso simultáneo a los vínculos y proporciona la capacidad de hacer referencia a los vínculos a través de las devoluciones de llamada. Los bloques de mensajes (`target_block`s o `propagator_block`s) deben utilizar esta clase para sus vínculos de origen.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`source_link_manager`

## <a name="requirements"></a>Requisitos

**Encabezado:** agents.h

**Espacio de nombres:** simultaneidad

## <a name="add"></a>agréguela

Agrega un vínculo de origen al objeto de `source_link_manager`.

```cpp
void add(_EType _Link);
```

### <a name="parameters"></a>Parámetros

*_Link*<br/>
Un puntero a un bloque que se va a agregar.

## <a name="begin"></a>inicia

Devuelve un iterador al primer elemento del objeto `source_link_manager`.

```cpp
iterator begin();
```

### <a name="return-value"></a>Valor devuelto

Iterador que direcciona el primer elemento del objeto `source_link_manager`.

### <a name="remarks"></a>Observaciones

El estado final del iterador se indica mediante un vínculo de `NULL`.

## <a name="contains"></a>tuviera

Busca un bloque especificado en el `network_link_registry` dentro de este objeto `source_link_manager`.

```cpp
bool contains(_EType _Link);
```

### <a name="parameters"></a>Parámetros

*_Link*<br/>
Puntero a un bloque que se va a buscar en el objeto `source_link_manager`.

### <a name="return-value"></a>Valor devuelto

**true** si se encontró el bloque especificado; en caso contrario, **false** .

## <a name="count"></a>contabiliza

Cuenta el número de bloques vinculados en el objeto de `source_link_manager`.

```cpp
size_t count();
```

### <a name="return-value"></a>Valor devuelto

El número de bloques vinculados en el objeto de `source_link_manager`.

## <a name="reference"></a>referencia

Adquiere una referencia en el objeto `source_link_manager`.

```cpp
void reference();
```

## <a name="register_target_block"></a>register_target_block

Registra el bloque de destino que contiene este objeto `source_link_manager`.

```cpp
void register_target_block(_Inout_ ITarget<typename _Block::source_type>* _PTarget);
```

### <a name="parameters"></a>Parámetros

*_PTarget*<br/>
El bloque de destino que contiene este objeto `source_link_manager`.

## <a name="release"></a>emisión

Libera la referencia en el objeto `source_link_manager`.

```cpp
void release();
```

## <a name="remove"></a>retirar

Quita un vínculo del objeto `source_link_manager`.

```cpp
bool remove(_EType _Link);
```

### <a name="parameters"></a>Parámetros

*_Link*<br/>
Un puntero a un bloque que se va a quitar, si se encuentra.

### <a name="return-value"></a>Valor devuelto

**true** si el vínculo se encontró y se quitó; de lo contrario, **false** .

## <a name="set_bound"></a>set_bound

Establece el número máximo de vínculos de origen que se pueden agregar a este objeto `source_link_manager`.

```cpp
void set_bound(size_t _MaxLinks);
```

### <a name="parameters"></a>Parámetros

*_MaxLinks*<br/>
Número máximo de vínculos.

## <a name="ctor"></a>source_link_manager

Construye un objeto `source_link_manager`.

```cpp
source_link_manager();
```

## <a name="dtor"></a>~ source_link_manager

Destruye el objeto `source_link_manager`.

```cpp
~source_link_manager();
```

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[single_link_registry (clase)](single-link-registry-class.md)<br/>
[multi_link_registry (clase)](multi-link-registry-class.md)
