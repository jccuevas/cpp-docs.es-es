---
title: ComPtrRefBase (clase)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRefBase
- client/Microsoft::WRL::Details::ComPtrRefBase::operator IInspectable**
- client/Microsoft::WRL::Details::ComPtrRefBase::operator IUnknown**
- client/Microsoft::WRL::Details::ComPtrRefBase::ptr_
helpviewer_keywords:
- Microsoft::WRL::Details::ComPtrRefBase class
- Microsoft::WRL::Details::ComPtrRefBase::operator IInspectable** operator
- Microsoft::WRL::Details::ComPtrRefBase::operator IUnknown** operator
- Microsoft::WRL::Details::ComPtrRefBase::ptr_ data member
ms.assetid: 6d344c1a-cc13-4a3f-8a0d-f167ccb9348f
ms.openlocfilehash: 4f6dd6449cf8135ad14486d64cea95d8329e0014
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372615"
---
# <a name="comptrrefbase-class"></a>ComPtrRefBase (clase)

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
template <typename T>
class ComPtrRefBase;
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Un [ComPtr\<T>](comptr-class.md) tipo o un tipo derivado de él, no simplemente la interfaz representada por el `ComPtr`archivo .

## <a name="remarks"></a>Observaciones

Representa la clase base para la [clase ComPtrRef.](comptrref-class.md)

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

Nombre            | Descripción
--------------- | -------------------------------------------------
`InterfaceType` | Sinónimo del tipo de parámetro de plantilla *T*.

### <a name="public-operators"></a>Operadores públicos

Nombre                                                                       | Descripción
-------------------------------------------------------------------------- | -----------------------------------------------------------------------------------------------------
[ComPtrRefBase::operator IInspectable**](#operator-iinspectable-star-star) | Convierte el miembro de datos [ptr_](#ptr) actual en un puntero `IInspectable` a un puntero a la interfaz.
[ComPtrRefBase::operator IUnknown**](#operator-iunknown-star-star)         | Convierte el miembro de datos [ptr_](#ptr) actual en un puntero `IUnknown` a un puntero a la interfaz.

### <a name="protected-data-members"></a>Miembros de datos protegidos

Nombre                        | Descripción
--------------------------- | ----------------------------------------------------------------
[ComPtrRefBase::ptr_](#ptr) | Puntero al tipo especificado por el parámetro de plantilla actual.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`ComPtrRefBase`

## <a name="requirements"></a>Requisitos

**Encabezado:** client.h

**Espacio de nombres:** Microsoft::WRL::Details

## <a name="comptrrefbaseoperator-iinspectable-operator"></a><a name="operator-iinspectable-star-star"></a>Operador IInspectable\* \* ComPtrRefBase::operator

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
operator IInspectable**() const;
```

### <a name="remarks"></a>Observaciones

Convierte el miembro de datos [ptr_](#ptr) actual en un puntero `IInspectable` a un puntero a la interfaz.

Se emite un error `ComPtrRefBase` si la corriente `IInspectable`no deriva de .

Esta conversión solo `__WRL_CLASSIC_COM__` está disponible si está definida.

## <a name="comptrrefbaseoperator-iunknown-operator"></a><a name="operator-iunknown-star-star"></a>Operador ComPtrRefBase::operator IUnknown**

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
operator IUnknown**() const;
```

### <a name="remarks"></a>Observaciones

Convierte el miembro de datos [ptr_](#ptr) actual en un puntero `IUnknown` a un puntero a la interfaz.

Se emite un error `ComPtrRefBase` si la corriente `IUnknown`no deriva de .

## <a name="comptrrefbaseptr_"></a><a name="ptr"></a>ComPtrRefBase::ptr_

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
T* ptr_;
```

### <a name="remarks"></a>Observaciones

Puntero al tipo especificado por el parámetro de plantilla actual. `ptr_`es el miembro de datos protegido.
