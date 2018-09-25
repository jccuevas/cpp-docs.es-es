---
title: MakeAllocator (clase) | Microsoft Docs
ms.custom: ''
ms.date: 09/21/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAllocator
- implements/Microsoft::WRL::Details::MakeAllocator::Allocate
- implements/Microsoft::WRL::Details::MakeAllocator::Detach
- implements/Microsoft::WRL::Details::MakeAllocator::MakeAllocator
- implements/Microsoft::WRL::Details::MakeAllocator::~MakeAllocator
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Details::MakeAllocator class
- Microsoft::WRL::Details::MakeAllocator::Allocate method
- Microsoft::WRL::Details::MakeAllocator::Detach method
- Microsoft::WRL::Details::MakeAllocator::MakeAllocator, constructor
- Microsoft::WRL::Details::MakeAllocator::~MakeAllocator, destructor
ms.assetid: a1114615-abd7-4a56-9bc3-750c118f0fa1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6cb6574172747712fa2670b4444b17bec047a8cf
ms.sourcegitcommit: edb46b0239a0e616af4ec58906e12338c3e8d2c6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/25/2018
ms.locfileid: "47169741"
---
# <a name="makeallocator-class"></a>MakeAllocator (clase)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
template<
   typename T,
   bool hasWeakReferenceSupport =
         !__is_base_of(RuntimeClassFlags<InhibitWeakReference>, T)>
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
`true` Para asignar memoria para un objeto que admite referencias débiles; `false` asignar memoria para un objeto que no es compatible con las referencias débiles.

## <a name="remarks"></a>Comentarios

Asigna memoria para una clase activable, con o sin compatibilidad con la referencia débil.

Invalidar el `MakeAllocator` clase para implementar un modelo de asignación de memoria definido por el usuario.

`MakeAllocator` se utiliza normalmente para evitar pérdidas de memoria si se produce un objeto durante la construcción.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

Name                                                  | Descripción
----------------------------------------------------- | ----------------------------------------------------------------
[Makeallocator](#makeallocator)        | Inicializa una nueva instancia de la clase `MakeAllocator`.
[MakeAllocator:: ~ MakeAllocator](#tilde-makeallocator) | Desinicializa la instancia actual de la `MakeAllocator` clase.

### <a name="public-methods"></a>Métodos públicos

Name                                 | Descripción
------------------------------------ | -----------------------------------------------------------------------------------------------------------
[Makeallocator](#allocate) | Asigna memoria y lo asocia con el actual `MakeAllocator` objeto.
[Makeallocator](#detach)     | Desasocia la memoria asignada por el [Allocate](#allocate) método desde la actual `MakeAllocator` objeto.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`MakeAllocator`

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Namespace:** wrl

## <a name="allocate"></a>Makeallocator

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

## <a name="detach"></a>Makeallocator

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
__forceinline void Detach();
```

### <a name="remarks"></a>Comentarios

Desasocia la memoria asignada por el [Allocate](#allocate) método desde la actual `MakeAllocator` objeto.

Si se llama a `Detach()`, usted es responsable de eliminar la memoria proporcionada por el `Allocate` método.

## <a name="makeallocator"></a>Makeallocator

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
MakeAllocator();
```

### <a name="remarks"></a>Comentarios

Inicializa una nueva instancia de la clase `MakeAllocator`.

## <a name="tilde-makeallocator"></a>MakeAllocator:: ~ MakeAllocator

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
~MakeAllocator();
```

### <a name="remarks"></a>Comentarios

Desinicializa la instancia actual de la `MakeAllocator` clase.

Este destructor también elimina la memoria asignada subyacente si es necesario.
