---
title: SyncLockWithStatusT (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT
dev_langs:
- C++
helpviewer_keywords:
- SyncLockWithStatusT class
ms.assetid: 4832fd93-0ac8-4168-9404-b43fefea7476
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 69676651c77175b55f4363b525a3ca3acb9be46d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46437461"
---
# <a name="synclockwithstatust-class"></a>SyncLockWithStatusT (Clase)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
template <
   typename SyncTraits
>
class SyncLockWithStatusT : public SyncLockT<SyncTraits>;
```

### <a name="parameters"></a>Parámetros

*SyncTraits*<br/>
Un tipo que puede tomar exclusivo o propiedad compartida de un recurso.

## <a name="remarks"></a>Comentarios

Representa un tipo que puede tardar exclusivo o propiedad compartida de un recurso.

El **SyncLockWithStatusT** clase se utiliza para implementar el [Mutex](../windows/mutex-class1.md) y [semáforo](../windows/semaphore-class.md) clases.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[SyncLockWithStatusT::SyncLockWithStatusT (constructor)](../windows/synclockwithstatust-synclockwithstatust-constructor.md)|Inicializa una nueva instancia de la **SyncLockWithStatusT** clase.|

### <a name="protected-constructors"></a>Constructores protegidos

|Name|Descripción|
|----------|-----------------|
|[SyncLockWithStatusT::SyncLockWithStatusT (constructor)](../windows/synclockwithstatust-synclockwithstatust-constructor.md)|Inicializa una nueva instancia de la **SyncLockWithStatusT** clase.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[SyncLockWithStatusT::GetStatus (método)](../windows/synclockwithstatust-getstatus-method.md)|Recupera el estado de espera de la actual **SyncLockWithStatusT** objeto.|
|[SyncLockWithStatusT::IsLocked (método)](../windows/synclockwithstatust-islocked-method.md)|Indica si el actual **SyncLockWithStatusT** objeto posee un recurso; es decir, el **SyncLockWithStatusT** objeto es *bloqueado*.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|nombre|Descripción|
|----------|-----------------|
|[SyncLockWithStatusT::status_ (miembro de datos)](../windows/synclockwithstatust-status-data-member.md)|Contiene el resultado de la operación de espera subyacente después de una operación de bloqueo en un objeto basado en la actual **SyncLockWithStatusT** objeto.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`SyncLockT`

`SyncLockWithStatusT`

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Namespace:** Wrappers

## <a name="see-also"></a>Vea también

[Microsoft::WRL::Wrappers::Details (espacio de nombres)](../windows/microsoft-wrl-wrappers-details-namespace.md)