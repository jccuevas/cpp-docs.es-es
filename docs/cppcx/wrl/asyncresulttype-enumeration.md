---
title: AsyncResultType (enumeración)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncResultType
helpviewer_keywords:
- AsyncResultType enumeration
ms.assetid: 4195d234-3f3f-4363-9118-6ad2a7551cf2
ms.openlocfilehash: d3f99fa85a777ae8361ed6f7cb82fe97ddd8d667
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59028059"
---
# <a name="asyncresulttype-enumeration"></a>AsyncResultType (enumeración)

Especifica el tipo de resultado devuelto por la `GetResults()` método.

## <a name="syntax"></a>Sintaxis

```cpp
enum AsyncResultType;
```

## <a name="members"></a>Miembros

### <a name="values"></a>Valores

|Name|Descripción|
|----------|-----------------|
|`MultipleResults`|Un conjunto de resultados múltiples, que se presentan progresivamente entre `Start` estado y antes de `Close()` se llama.|
|`SingleResult`|Un único resultado, que se presenta después de la `Complete` se produce el evento.|

## <a name="requirements"></a>Requisitos

**Encabezado:** async.h

**Espacio de nombres**: Microsoft::WRL

## <a name="see-also"></a>Vea también

[Microsoft::WRL (Espacio de nombres)](microsoft-wrl-namespace.md)