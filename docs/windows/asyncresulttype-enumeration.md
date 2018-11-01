---
title: AsyncResultType (enumeración)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncResultType
helpviewer_keywords:
- AsyncResultType enumeration
ms.assetid: 4195d234-3f3f-4363-9118-6ad2a7551cf2
ms.openlocfilehash: df91b80fe21ecddabc7062b040387b8c2b2c1bb7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50551377"
---
# <a name="asyncresulttype-enumeration"></a>AsyncResultType (enumeración)

Especifica el tipo de resultado devuelto por la `GetResults()` método.

## <a name="syntax"></a>Sintaxis

```cpp
enum AsyncResultType;
```

## <a name="members"></a>Miembros

### <a name="values"></a>Valores

|Nombre|Descripción|
|----------|-----------------|
|`MultipleResults`|Un conjunto de resultados múltiples, que se presentan progresivamente entre `Start` estado y antes de `Close()` se llama.|
|`SingleResult`|Un único resultado, que se presenta después de la `Complete` se produce el evento.|

## <a name="requirements"></a>Requisitos

**Encabezado:** async.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[Microsoft::WRL (espacio de nombres)](../windows/microsoft-wrl-namespace.md)