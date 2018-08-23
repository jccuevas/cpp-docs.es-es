---
title: MakeAllocator (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAllocator
dev_langs:
- C++
helpviewer_keywords:
- MakeAllocator class
ms.assetid: a1114615-abd7-4a56-9bc3-750c118f0fa1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e27be8eaddfc22474f15d7f9358050273252bf8a
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42610329"
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

*T*  
Nombre de tipo.

*hasWeakReferenceSupport*  
**True** asignar memoria para un objeto que admite referencias débiles; **false** asignar memoria para un objeto que no es compatible con las referencias débiles.

## <a name="remarks"></a>Comentarios

Asigna memoria para una clase activable, con o sin compatibilidad con la referencia débil.

Invalidar el **MakeAllocator** clase para implementar un modelo de asignación de memoria definido por el usuario.

**MakeAllocator** se utiliza normalmente para evitar pérdidas de memoria si se produce un objeto durante la construcción.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[MakeAllocator::MakeAllocator (constructor)](../windows/makeallocator-makeallocator-constructor.md)|Inicializa una nueva instancia de la **MakeAllocator** clase.|
|[MakeAllocator::~MakeAllocator (destructor)](../windows/makeallocator-tilde-makeallocator-destructor.md)|Desinicializa la instancia actual de la **MakeAllocator** clase.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[MakeAllocator::Allocate (método)](../windows/makeallocator-allocate-method.md)|Asigna memoria y lo asocia con el actual **MakeAllocator** objeto.|
|[MakeAllocator::Detach (método)](../windows/makeallocator-detach-method.md)|Desasocia la memoria asignada por el [Allocate](../windows/makeallocator-allocate-method.md) método desde la actual **MakeAllocator** objeto.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`MakeAllocator`

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Namespace:** wrl

## <a name="see-also"></a>Vea también

[Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)