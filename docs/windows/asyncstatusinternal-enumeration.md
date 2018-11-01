---
title: AsyncStatusInternal (enumeración)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::Details::AsyncStatusInternal
helpviewer_keywords:
- AsyncStatusInternal enumeration
ms.assetid: b783923f-3f1c-4487-9384-be572cbc62d7
ms.openlocfilehash: fe70ee1ac5d26ed15d2b497356fe941c72ec0c83
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50564949"
---
# <a name="asyncstatusinternal-enumeration"></a>AsyncStatusInternal (enumeración)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
enum AsyncStatusInternal;
```

## <a name="remarks"></a>Comentarios

Especifica una asignación entre enumeraciones internas para el estado de las operaciones asincrónicas y la `Windows::Foundation::AsyncStatus` enumeración.

## <a name="members"></a>Miembros

`_Created`<br/>
Equivalente a `::Windows::Foundation::AsyncStatus::Created`.

`_Started`<br/>
Equivalente a `::Windows::Foundation::AsyncStatus::Started`.

`_Completed`<br/>
Equivalente a `::Windows::Foundation::AsyncStatus::Completed`.

`_Cancelled`<br/>
Equivalente a `::Windows::Foundation::AsyncStatus::Cancelled`.

`_Error`<br/>
Equivalente a `::Windows::Foundation::AsyncStatus::Error`.

## <a name="requirements"></a>Requisitos

**Encabezado:** async.h

**Namespace:** wrl

## <a name="see-also"></a>Vea también

[Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)