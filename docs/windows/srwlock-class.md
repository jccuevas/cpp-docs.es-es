---
title: SRWLock (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::SRWLock
dev_langs:
- C++
helpviewer_keywords:
- SRWLock class
ms.assetid: 4fa250e3-5f29-4b06-ac24-61b6c04ade93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fb97a29796c287cfaadddc305f25807de5dcba2e
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42604241"
---
# <a name="srwlock-class"></a>SRWLock (clase)

Representa un bloqueo fino de lector/escritor.

## <a name="syntax"></a>Sintaxis

```cpp
class SRWLock;
```

## <a name="remarks"></a>Comentarios

Un bloqueo fino de lector/escritor se utiliza para sincronizar el acceso a través de subprocesos a un objeto o un recurso. Para obtener más información, consulte [funciones de sincronización](/windows/desktop/Sync/synchronization-functions).

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|||
|-|-|
|`SyncLockExclusive`|Sinónimo de un **SRWLock** objeto que se adquiere en modo exclusivo.|
|`SyncLockShared`|Sinónimo de un **SRWLock** objeto que se adquiere en modo compartido.|

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[SRWLock::SRWLock (constructor)](../windows/srwlock-srwlock-constructor.md)|Inicializa una nueva instancia de la **SRWLock** clase.|
|[SRWLock::~SRWLock (destructor)](../windows/srwlock-tilde-srwlock-destructor.md)|Desinicializa una instancia de la **SRWLock** clase.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[SRWLock::LockExclusive (método)](../windows/srwlock-lockexclusive-method.md)|Adquiere un **SRWLock** objeto en modo exclusivo.|
|[SRWLock::LockShared (método)](../windows/srwlock-lockshared-method.md)|Adquiere un **SRWLock** objeto en modo compartido.|
|[SRWLock::TryLockExclusive (método)](../windows/srwlock-trylockexclusive-method.md)|Intenta adquirir un **SRWLock** objeto en modo exclusivo para el actual o especificada **SRWLock** objeto.|
|[SRWLock::TryLockShared (método)](../windows/srwlock-trylockshared-method.md)|Intenta adquirir un **SRWLock** objeto en modo compartido para el actual o especificada **SRWLock** objeto.|

### <a name="protected-data-member"></a>Miembro de datos protegidos

|nombre|Descripción|
|----------|-----------------|
|[SRWLock::SRWLock_ (miembro de datos)](../windows/srwlock-srwlock-data-member.md)|Contiene la variable subyacente de bloqueo actual **SRWLock** objeto.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`SRWLock`

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Namespace:** Wrappers

## <a name="see-also"></a>Vea también

[Microsoft::WRL::Wrappers (espacio de nombres)](../windows/microsoft-wrl-wrappers-namespace.md)