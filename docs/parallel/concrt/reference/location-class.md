---
title: location (Clase)
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
ms.openlocfilehash: 5e90dd3b23b33f6699f2df4ce0df9178f95816b8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62375462"
---
# <a name="location-class"></a>location (Clase)

Una abstracción de una ubicación física en el hardware.

## <a name="syntax"></a>Sintaxis

```
class location;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[location](#ctor)|Sobrecargado. Construye un objeto `location`.|
|[~ location (destructor)](#dtor)|Destruye un objeto `location`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[current](#current)|Devuelve un `location` objeto que representa el lugar más específico que se está ejecutando el subproceso que realiza la llamada.|
|[from_numa_node](#from_numa_node)|Devuelve un `location` el objeto que representa un nodo NUMA determinado.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[operator!=](#operator_neq)|Determina si dos `location` objetos representan otra ubicación.|
|[operator=](#operator_eq)|Asigna el contenido de otro `location` objeto a ésta.|
|[operator==](#operator_eq_eq)|Determina si dos `location` objetos representan la misma ubicación.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`location`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrt.h

**Espacio de nombres:** simultaneidad

##  <a name="dtor"></a> ~location

Destruye un objeto `location`.

```
~location();
```

##  <a name="current"></a> Actual

Devuelve un `location` objeto que representa el lugar más específico que se está ejecutando el subproceso que realiza la llamada.

```
static location __cdecl current();
```

### <a name="return-value"></a>Valor devuelto

Una ubicación que representa la ubicación más específica en la que está ejecutando el subproceso que realiza la llamada.

##  <a name="from_numa_node"></a> from_numa_node

Devuelve un `location` el objeto que representa un nodo NUMA determinado.

```
static location __cdecl from_numa_node(unsigned short _NumaNodeNumber);
```

### <a name="parameters"></a>Parámetros

*_NumaNodeNumber*<br/>
El número de nodos NUMA para construir una ubicación para.

### <a name="return-value"></a>Valor devuelto

Una ubicación que representa el nodo NUMA especificado por el `_NumaNodeNumber` parámetro.

##  <a name="ctor"></a> Ubicación

Construye un objeto `location`.

```
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
(Opcional) Puntero de enlace.

### <a name="remarks"></a>Comentarios

Una ubicación construido de forma predeterminada, representa el sistema como un todo.

##  <a name="operator_neq"></a> operator!=

Determina si dos `location` objetos representan otra ubicación.

```
bool operator!= (const location& _Rhs) const;
```

### <a name="parameters"></a>Parámetros

*_Rhs*<br/>
Operando `location`.

### <a name="return-value"></a>Valor devuelto

**True** si las dos ubicaciones son diferentes, **false** en caso contrario.

##  <a name="operator_eq"></a> operator=

Asigna el contenido de otro `location` objeto a ésta.

```
location& operator= (const location& _Rhs);
```

### <a name="parameters"></a>Parámetros

*_Rhs*<br/>
Objeto `location` de origen.

### <a name="return-value"></a>Valor devuelto

##  <a name="operator_eq_eq"></a> operador ==

Determina si dos `location` objetos representan la misma ubicación.

```
bool operator== (const location& _Rhs) const;
```

### <a name="parameters"></a>Parámetros

*_Rhs*<br/>
Operando `location`.

### <a name="return-value"></a>Valor devuelto

**True** si las dos ubicaciones son idénticas, y **false** en caso contrario.

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)
