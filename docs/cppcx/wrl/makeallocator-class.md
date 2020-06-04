---
title: MakeAllocator (clase)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAllocator
- implements/Microsoft::WRL::Details::MakeAllocator::Allocate
- implements/Microsoft::WRL::Details::MakeAllocator::Detach
- implements/Microsoft::WRL::Details::MakeAllocator::MakeAllocator
- implements/Microsoft::WRL::Details::MakeAllocator::~MakeAllocator
helpviewer_keywords:
- Microsoft::WRL::Details::MakeAllocator class
- Microsoft::WRL::Details::MakeAllocator::Allocate method
- Microsoft::WRL::Details::MakeAllocator::Detach method
- Microsoft::WRL::Details::MakeAllocator::MakeAllocator, constructor
- Microsoft::WRL::Details::MakeAllocator::~MakeAllocator, destructor
ms.assetid: a1114615-abd7-4a56-9bc3-750c118f0fa1
ms.openlocfilehash: dc0d83f2550646572a4eff2bec7850037c6dbf6a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371334"
---
# <a name="makeallocator-class"></a>MakeAllocator (clase)

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
template<
    typename T,
    bool hasWeakReferenceSupport =
          !__is_base_of(RuntimeClassFlags<InhibitWeakReference>,
                        T)
>
class MakeAllocator;

template<typename T>
class MakeAllocator<T, false>;

template<typename T>
class MakeAllocator<T, true>;
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Nombre de tipo.

*hasWeakReferenceSupport*<br/>
**true** para asignar memoria para un objeto que admite referencias débiles; **false** para asignar memoria para un objeto que no admite referencias débiles.

## <a name="remarks"></a>Observaciones

Asigna memoria para una clase activable, con o sin compatibilidad de referencia débil.

Invalide `MakeAllocator` la clase para implementar un modelo de asignación de memoria definido por el usuario.

`MakeAllocator`normalmente se utiliza para evitar pérdidas de memoria si un objeto se produce durante la construcción.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

Nombre                                                  | Descripción
----------------------------------------------------- | ----------------------------------------------------------------
[MakeAllocator::MakeAllocator](#makeallocator)        | Inicializa una nueva instancia de la clase `MakeAllocator`.
[MakeAllocator::-MakeAllocator](#tilde-makeallocator) | Desinicializa la instancia `MakeAllocator` actual de la clase.

### <a name="public-methods"></a>Métodos públicos

Nombre                                 | Descripción
------------------------------------ | -----------------------------------------------------------------------------------------------------------
[MakeAllocator::Asignar](#allocate) | Asigna memoria y la asocia `MakeAllocator` con el objeto actual.
[MakeAllocator::Dsetach](#detach)     | Desasocia la memoria [Allocate](#allocate) asignada por `MakeAllocator` el método Allocate del objeto actual.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`MakeAllocator`

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Espacio de nombres:** Microsoft::WRL::Details

## <a name="makeallocatorallocate"></a><a name="allocate"></a>MakeAllocator::Asignar

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
__forceinline void* Allocate();
```

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, un puntero a la memoria asignada; de `nullptr`lo contrario, .

### <a name="remarks"></a>Observaciones

Asigna memoria y la asocia `MakeAllocator` con el objeto actual.

El tamaño de la memoria asignada es el tamaño `MakeAllocator` del tipo especificado por el parámetro de plantilla actual.

Un desarrollador debe invalidar `Allocate()` solo el método para implementar un modelo de asignación de memoria diferente.

## <a name="makeallocatordetach"></a><a name="detach"></a>MakeAllocator::Dsetach

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
__forceinline void Detach();
```

### <a name="remarks"></a>Observaciones

Desasocia la memoria [Allocate](#allocate) asignada por `MakeAllocator` el método Allocate del objeto actual.

Si llama `Detach()`a , usted es responsable de `Allocate` eliminar la memoria proporcionada por el método.

## <a name="makeallocatormakeallocator"></a><a name="makeallocator"></a>MakeAllocator::MakeAllocator

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
MakeAllocator();
```

### <a name="remarks"></a>Observaciones

Inicializa una nueva instancia de la clase `MakeAllocator`.

## <a name="makeallocatormakeallocator"></a><a name="tilde-makeallocator"></a>MakeAllocator::-MakeAllocator

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
~MakeAllocator();
```

### <a name="remarks"></a>Observaciones

Desinicializa la instancia `MakeAllocator` actual de la clase.

Este destructor también elimina la memoria asignada subyacente si es necesario.
