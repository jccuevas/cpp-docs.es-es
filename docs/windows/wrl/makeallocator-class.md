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
ms.openlocfilehash: 805f0c09b0490d8cec1a0be96dcb1fc99a051371
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54337469"
---
# <a name="makeallocator-class"></a>MakeAllocator (clase)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

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
**True** asignar memoria para un objeto que admite referencias débiles; **false** asignar memoria para un objeto que no es compatible con las referencias débiles.

## <a name="remarks"></a>Comentarios

Asigna memoria para una clase activable, con o sin compatibilidad con la referencia débil.

Invalidar el `MakeAllocator` clase para implementar un modelo de asignación de memoria definido por el usuario.

`MakeAllocator` se utiliza normalmente para evitar pérdidas de memoria si se produce un objeto durante la construcción.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

Name                                                  | Descripción
----------------------------------------------------- | ----------------------------------------------------------------
[MakeAllocator::MakeAllocator](#makeallocator)        | Inicializa una nueva instancia de la clase `MakeAllocator`.
[MakeAllocator::~MakeAllocator](#tilde-makeallocator) | Desinicializa la instancia actual de la `MakeAllocator` clase.

### <a name="public-methods"></a>Métodos públicos

Name                                 | Descripción
------------------------------------ | -----------------------------------------------------------------------------------------------------------
[MakeAllocator::Allocate](#allocate) | Asigna memoria y lo asocia con el actual `MakeAllocator` objeto.
[MakeAllocator::Detach](#detach)     | Desasocia la memoria asignada por el [Allocate](#allocate) método desde la actual `MakeAllocator` objeto.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`MakeAllocator`

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Espacio de nombres**: Microsoft::WRL::Details

## <a name="allocate"></a>MakeAllocator::Allocate

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
__forceinline void* Allocate();
```

### <a name="return-value"></a>Valor devuelto

Si es correcto, un puntero a la memoria asignada; en caso contrario, `nullptr`.

### <a name="remarks"></a>Comentarios

Asigna memoria y lo asocia con el actual `MakeAllocator` objeto.

El tamaño de la memoria asignada es el tamaño del tipo especificado por el actual `MakeAllocator` parámetro de plantilla.

Un desarrollador necesita sobrescribir sólo el `Allocate()` método para implementar un modelo de asignación de memoria diferente.

## <a name="detach"></a>MakeAllocator::Detach

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
__forceinline void Detach();
```

### <a name="remarks"></a>Comentarios

Desasocia la memoria asignada por el [Allocate](#allocate) método desde la actual `MakeAllocator` objeto.

Si se llama a `Detach()`, usted es responsable de eliminar la memoria proporcionada por el `Allocate` método.

## <a name="makeallocator"></a>MakeAllocator::MakeAllocator

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
MakeAllocator();
```

### <a name="remarks"></a>Comentarios

Inicializa una nueva instancia de la clase `MakeAllocator`.

## <a name="tilde-makeallocator"></a>MakeAllocator::~MakeAllocator

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
~MakeAllocator();
```

### <a name="remarks"></a>Comentarios

Desinicializa la instancia actual de la `MakeAllocator` clase.

Este destructor también elimina la memoria asignada subyacente si es necesario.
