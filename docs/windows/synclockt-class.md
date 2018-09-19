---
title: SyncLockT (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT
dev_langs:
- C++
helpviewer_keywords:
- SyncLockT class
ms.assetid: a967f6f7-3555-43d1-b210-2bb65d63d15e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e8589c43d49709842a745464d2727860ccd2c1e2
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42609682"
---
# <a name="synclockt-class"></a>SyncLockT (clase)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
template <
   typename SyncTraits
>
class SyncLockT;
```

### <a name="parameters"></a>Parámetros

*SyncTraits*  
El tipo que puede tomar posesión de un recurso.

## <a name="remarks"></a>Comentarios

Representa un tipo que puede tardar exclusivo o propiedad compartida de un recurso.

El **SyncLockT** clase se utiliza, por ejemplo, para ayudar a implementar el [SRWLock](../windows/srwlock-class.md) clase.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[SyncLockT::SyncLockT (constructor)](../windows/synclockt-synclockt-constructor.md)|Inicializa una nueva instancia de la **SyncLockT** clase.|
|[SyncLockT::~SyncLockT (destructor)](../windows/synclockt-tilde-synclockt-destructor.md)|Desinicializa una instancia de la **SyncLockT** clase.|

### <a name="protected-constructors"></a>Constructores protegidos

|Name|Descripción|
|----------|-----------------|
|[SyncLockT::SyncLockT (constructor)](../windows/synclockt-synclockt-constructor.md)|Inicializa una nueva instancia de la **SyncLockT** clase.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[SyncLockT::IsLocked (método)](../windows/synclockt-islocked-method.md)|Indica si el actual **SyncLockT** objeto posee un recurso; es decir, el **SyncLockT** objeto es *bloqueado*.|
|[SyncLockT::Unlock (método)](../windows/synclockt-unlock-method.md)|Devuelve el control de los recursos mantenidos por el actual **SyncLockT** objeto, si existe.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|nombre|Descripción|
|----------|-----------------|
|[SyncLockT::sync_ (miembro de datos)](../windows/synclockt-sync-data-member.md)|Contiene el recurso subyacente representado por la **SyncLockT** clase.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`SyncLockT`

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Namespace:** Wrappers

## <a name="see-also"></a>Vea también

[Microsoft::WRL::Wrappers::Details (espacio de nombres)](../windows/microsoft-wrl-wrappers-details-namespace.md)  
[SRWLock (clase)](../windows/srwlock-class.md)