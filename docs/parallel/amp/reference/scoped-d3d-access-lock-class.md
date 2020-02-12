---
title: scoped_d3d_access_lock (Clase)
ms.date: 11/04/2016
f1_keywords:
- scoped_d3d_access_lock
- AMPRT/scoped_d3d_access_lock
- AMPRT/concurrency::direct3d::scoped_d3d_access_lock::scoped_d3d_access_lock
ms.assetid: 0ad333e6-9839-4736-a722-16d95d70c4b1
ms.openlocfilehash: b5a2d9dab9cba7b19fa0d0b1627f653f2c7fdc57
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126401"
---
# <a name="scoped_d3d_access_lock-class"></a>scoped_d3d_access_lock (Clase)

Contenedor RAII para un bloqueo de acceso de D3D en un objeto accelerator_view.

## <a name="syntax"></a>Sintaxis

```cpp
class scoped_d3d_access_lock;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[Constructor de scoped_d3d_access_lock](#ctor)|Sobrecargado. Construye un objeto `scoped_d3d_access_lock`. El bloqueo se libera cuando este objeto sale del ámbito.|
|[~ scoped_d3d_access_lock destructor](#dtor)|Libera el bloqueo de acceso de D3D en el objeto de `accelerator_view` asociado.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[operator=](#operator_eq)|Toma posesión de un bloqueo de otro `scoped_d3d_access_lock`.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`scoped_d3d_access_lock`

## <a name="requirements"></a>Requisitos

**Encabezado:** amprt. h

**Espacio de nombres:** Concurrency::d irect3d

## <a name="ctor"></a>scoped_d3d_access_lock

Construye un objeto `scoped_d3d_access_lock`. El bloqueo se libera cuando este objeto sale del ámbito.

```cpp
explicit scoped_d3d_access_lock(// [1] constructor
    accelerator_view& _Av);

explicit scoped_d3d_access_lock(// [2] constructor
    accelerator_view& _Av,
    adopt_d3d_access_lock_t _T);

scoped_d3d_access_lock(// [3] move constructor
    scoped_d3d_access_lock&& _Other);
```

### <a name="parameters"></a>Parámetros

*_Av*<br/>
`accelerator_view` del bloqueo que se va a adoptar.

*_T*<br/>
Objeto `adopt_d3d_access_lock_t`.

*_Other*<br/>
Objeto `scoped_d3d_access_lock` del que se va a desplace un bloqueo existente.

## <a name="construction"></a>Construcción

[1] el constructor adquiere un bloqueo de acceso de D3D en el objeto [accelerator_view](accelerator-view-class.md) especificado. La construcción se bloquea hasta que se adquiere el bloqueo.

[2] el constructor adopta un bloqueo de acceso D3D del objeto [accelerator_view](accelerator-view-class.md) especificado.

[3] el constructor de movimiento toma un bloqueo de acceso de D3D existente de otro objeto de `scoped_d3d_access_lock`. La construcción no se bloquea.

## <a name="dtor"></a>~ scoped_d3d_access_lock

Libera el bloqueo de acceso de D3D en el objeto de `accelerator_view` asociado.

```cpp
~scoped_d3d_access_lock();
```

## <a name="operator_eq"></a>operador =

Toma posesión de un bloqueo de acceso D3D de otro objeto `scoped_d3d_access_lock`, liberando el bloqueo anterior.

```cpp
scoped_d3d_access_lock& operator= (scoped_d3d_access_lock&& _Other);
```

### <a name="parameters"></a>Parámetros

*_Other*<br/>
Accelerator_view desde la que se va a trasladar el bloqueo de acceso de D3D.

### <a name="return-value"></a>Valor devuelto

Referencia a este `scoped_accelerator_view_lock`.

## <a name="see-also"></a>Consulte también

[Concurrency::direct3d (espacio de nombres)](concurrency-direct3d-namespace.md)
