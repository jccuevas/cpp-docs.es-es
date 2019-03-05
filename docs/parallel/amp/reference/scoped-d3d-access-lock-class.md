---
title: scoped_d3d_access_lock (Clase)
ms.date: 11/04/2016
f1_keywords:
- scoped_d3d_access_lock
- AMPRT/scoped_d3d_access_lock
- AMPRT/concurrency::direct3d::scoped_d3d_access_lock::scoped_d3d_access_lock
ms.assetid: 0ad333e6-9839-4736-a722-16d95d70c4b1
ms.openlocfilehash: e36c3c2cfa9d1b617e377a7e340f98875457bdf1
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57272469"
---
# <a name="scopedd3daccesslock-class"></a>scoped_d3d_access_lock (Clase)

Contenedor RAII para un bloqueo de acceso de D3D en un objeto accelerator_view.

### <a name="syntax"></a>Sintaxis

```
class scoped_d3d_access_lock;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[Constructor scoped_d3d_access_lock](#ctor)|Sobrecargado. Construye un objeto `scoped_d3d_access_lock`. El bloqueo se libera cuando este objeto queda fuera del ámbito.|
|[~ scoped_d3d_access_lock (destructor)](#dtor)|Libera el bloqueo de acceso de D3D en el asociado `accelerator_view` objeto.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[operator=](#operator_eq)|Toma posesión de un bloqueo de otro `scoped_d3d_access_lock`.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`scoped_d3d_access_lock`

## <a name="requirements"></a>Requisitos

**Encabezado:** amprt.h

**Namespace:** Concurrency:: Direct3D

##  <a name="ctor"></a> scoped_d3d_access_lock

Construye un objeto `scoped_d3d_access_lock`. El bloqueo se libera cuando este objeto queda fuera del ámbito.

```
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
El `accelerator_view` para que adopte el bloqueo.

*_T*<br/>
Objeto `adopt_d3d_access_lock_t`.

*_Other*<br/>
La `scoped_d3d_access_lock` objeto desde el que se va a mover un bloqueo existente.

## <a name="construction"></a>Construcción

[1] constructor adquiere un bloqueo de acceso de D3D en el determinado [accelerator_view](accelerator-view-class.md) objeto. Construcción se bloquea hasta que se adquiere el bloqueo.

[2] constructor adopte un bloqueo de acceso de D3D desde el determinado [accelerator_view](accelerator-view-class.md) objeto.

[3] Constructor de movimiento de tiene un bloqueo de acceso de D3D existente desde otro `scoped_d3d_access_lock` objeto. No impide la construcción.

##  <a name="dtor"></a> ~scoped_d3d_access_lock

Libera el bloqueo de acceso de D3D en el asociado `accelerator_view` objeto.

```
~scoped_d3d_access_lock();
```

## <a name="operator_eq"></a> operator=

Toma posesión de un bloqueo de acceso de D3D de otro `scoped_d3d_access_lock` objeto, lo que libera el bloqueo anterior.

```
scoped_d3d_access_lock& operator= (scoped_d3d_access_lock&& _Other);
```

### <a name="parameters"></a>Parámetros

*_Other*<br/>
El objeto accelerator_view desde el que se va a mover el bloqueo de acceso de D3D.

### <a name="return-value"></a>Valor devuelto

Una referencia a este `scoped_accelerator_view_lock`.

## <a name="see-also"></a>Vea también

[Concurrency::direct3d (espacio de nombres)](concurrency-direct3d-namespace.md)
