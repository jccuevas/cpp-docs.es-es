---
title: AsyncStatusInternal (enumeración)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::Details::AsyncStatusInternal
helpviewer_keywords:
- AsyncStatusInternal enumeration
ms.assetid: b783923f-3f1c-4487-9384-be572cbc62d7
ms.openlocfilehash: b38d58603eafeaa76c79873bbf375b4a3b405cdb
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58785897"
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

**Espacio de nombres**: Microsoft::WRL::Details

## <a name="see-also"></a>Vea también

[Microsoft::WRL::Details (espacio de nombres)](microsoft-wrl-details-namespace.md)