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
ms.openlocfilehash: df4e2aa1ce650fd5b1f04baf2f7c4cd2fb4cff93
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79423649"
---
# <a name="comptrrefbase-class"></a>ComPtrRefBase (clase)

Es compatible con la infraestructura de WRL y no está diseñada para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
template <typename T>
class ComPtrRefBase;
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Un tipo de [> ComPtr\<t](comptr-class.md) o un tipo derivado de él, no solo la interfaz representada por el `ComPtr`.

## <a name="remarks"></a>Observaciones

Representa la clase base para la clase [ComPtrRef](comptrref-class.md) .

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Typedefs públicos

Nombre            | Descripción
--------------- | -------------------------------------------------
`InterfaceType` | Sinónimo del tipo de parámetro de plantilla *T*.

### <a name="public-operators"></a>Operadores públicos

Nombre                                                                       | Descripción
-------------------------------------------------------------------------- | -----------------------------------------------------------------------------------------------------
[ComPtrRefBase:: Operator IInspectable * *](#operator-iinspectable-star-star) | Convierte el miembro de datos [ptr_](#ptr) actual en un puntero a puntero a la interfaz `IInspectable`.
[ComPtrRefBase:: Operator IUnknown * *](#operator-iunknown-star-star)         | Convierte el miembro de datos [ptr_](#ptr) actual en un puntero a puntero a la interfaz `IUnknown`.

### <a name="protected-data-members"></a>Miembros de datos protegidos

Nombre                        | Descripción
--------------------------- | ----------------------------------------------------------------
[ComPtrRefBase::p tr_](#ptr) | Puntero al tipo especificado por el parámetro de plantilla actual.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`ComPtrRefBase`

## <a name="requirements"></a>Requisitos

**Encabezado:** client.h

**Espacio de nombres:** Microsoft:: WRL::D etalles

## <a name="operator-iinspectable-star-star"></a>ComPtrRefBase:: Operator IInspectable\*operador de \*

Es compatible con la infraestructura de WRL y no está diseñada para utilizarse directamente desde el código.

```cpp
operator IInspectable**() const;
```

### <a name="remarks"></a>Observaciones

Convierte el miembro de datos [ptr_](#ptr) actual en un puntero a puntero a la interfaz `IInspectable`.

Se emite un error si el `ComPtrRefBase` actual no se deriva de `IInspectable`.

Esta conversión solo está disponible si se define `__WRL_CLASSIC_COM__`.

## <a name="operator-iunknown-star-star"></a>ComPtrRefBase:: Operator IUnknown * * (operador)

Es compatible con la infraestructura de WRL y no está diseñada para utilizarse directamente desde el código.

```cpp
operator IUnknown**() const;
```

### <a name="remarks"></a>Observaciones

Convierte el miembro de datos [ptr_](#ptr) actual en un puntero a puntero a la interfaz `IUnknown`.

Se emite un error si el `ComPtrRefBase` actual no se deriva de `IUnknown`.

## <a name="ptr"></a>ComPtrRefBase::p tr_

Es compatible con la infraestructura de WRL y no está diseñada para utilizarse directamente desde el código.

```cpp
T* ptr_;
```

### <a name="remarks"></a>Observaciones

Puntero al tipo especificado por el parámetro de plantilla actual. `ptr_` es el miembro de datos protegido.
