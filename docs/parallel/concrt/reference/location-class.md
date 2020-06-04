---
title: location (clase)
ms.date: 11/04/2016
f1_keywords:
- location
- CONCRT/concurrency::location
- CONCRT/concurrency::location::location
- CONCRT/concurrency::location::current
- CONCRT/concurrency::location::from_numa_node
helpviewer_keywords:
- location class
ms.assetid: c3289f51-5bf1-4dff-a18d-d0dab8e5d9c7
ms.openlocfilehash: 7f45ff6d3092bd7c27e81adddca72c9411f752d1
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139825"
---
# <a name="location-class"></a>location (clase)

Una abstracción de una ubicación física en el hardware.

## <a name="syntax"></a>Sintaxis

```cpp
class location;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[ubicación](#ctor)|Sobrecargado. Construye un objeto `location`.|
|[~ Location (destructor)](#dtor)|Destruye un objeto `location`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[corrientes](#current)|Devuelve un objeto `location` que representa la posición más específica en la que se está ejecutando el subproceso que realiza la llamada.|
|[from_numa_node](#from_numa_node)|Devuelve un objeto `location` que representa un nodo NUMA determinado.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[operator!=](#operator_neq)|Determina si dos objetos `location` representan una ubicación diferente.|
|[operator=](#operator_eq)|Asigna el contenido de un objeto de `location` diferente a este.|
|[operator==](#operator_eq_eq)|Determina si dos objetos `location` representan la misma ubicación.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`location`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrt. h

**Espacio de nombres:** simultaneidad

## <a name="dtor"></a>~ Ubicación

Destruye un objeto `location`.

```cpp
~location();
```

## <a name="current"></a>corrientes

Devuelve un objeto `location` que representa la posición más específica en la que se está ejecutando el subproceso que realiza la llamada.

```cpp
static location __cdecl current();
```

### <a name="return-value"></a>Valor devuelto

Ubicación que representa la posición más específica en la que se está ejecutando el subproceso que realiza la llamada.

## <a name="from_numa_node"></a>from_numa_node

Devuelve un objeto `location` que representa un nodo NUMA determinado.

```cpp
static location __cdecl from_numa_node(unsigned short _NumaNodeNumber);
```

### <a name="parameters"></a>Parámetros

*_NumaNodeNumber*<br/>
Número de nodo NUMA para el que se va a construir una ubicación.

### <a name="return-value"></a>Valor devuelto

Ubicación que representa el nodo NUMA especificado por el parámetro `_NumaNodeNumber`.

## <a name="ctor"></a>Cód

Construye un objeto `location`.

```cpp
location();

location(
    const location& _Src);

location(
    T _LocationType,
    unsigned int _Id,
    unsigned int _BindingId = 0,
    _Inout_opt_ void* _PBinding = NULL);
```

### <a name="parameters"></a>Parámetros

*_Src*<br/>

*_LocationType*<br/>

*_Id*<br/>

*_BindingId*<br/>

*_PBinding*<br/>
Opta Puntero de enlace.

### <a name="remarks"></a>Observaciones

Una ubicación construida de forma predeterminada representa el sistema en su conjunto.

## <a name="operator_neq"></a>operador! =

Determina si dos objetos `location` representan una ubicación diferente.

```cpp
bool operator!= (const location& _Rhs) const;
```

### <a name="parameters"></a>Parámetros

*_Rhs*<br/>
`location`de operando.

### <a name="return-value"></a>Valor devuelto

**true** si las dos ubicaciones son diferentes; de lo contrario, **false** .

## <a name="operator_eq"></a>operador =

Asigna el contenido de un objeto de `location` diferente a este.

```cpp
location& operator= (const location& _Rhs);
```

### <a name="parameters"></a>Parámetros

*_Rhs*<br/>
Objeto `location` de origen.

### <a name="return-value"></a>Valor devuelto

## <a name="operator_eq_eq"></a>operador = =

Determina si dos objetos `location` representan la misma ubicación.

```cpp
bool operator== (const location& _Rhs) const;
```

### <a name="parameters"></a>Parámetros

*_Rhs*<br/>
`location`de operando.

### <a name="return-value"></a>Valor devuelto

**true** si las dos ubicaciones son idénticas y **false** en caso contrario.

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)
