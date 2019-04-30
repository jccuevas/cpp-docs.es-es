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
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398802"
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

[Microsoft::WRL (espacio de nombres)](microsoft-wrl-namespace.md)