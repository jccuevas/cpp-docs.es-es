---
title: AsyncResultType (enumeración)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncResultType
helpviewer_keywords:
- AsyncResultType enumeration
ms.assetid: 4195d234-3f3f-4363-9118-6ad2a7551cf2
ms.openlocfilehash: b8a2a9ec803fba1be0012fcb58bf3b42e78f9071
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214167"
---
# <a name="asyncresulttype-enumeration"></a>AsyncResultType (enumeración)

Especifica el tipo de resultado devuelto por el método `GetResults()`.

## <a name="syntax"></a>Sintaxis

```cpp
enum AsyncResultType;
```

## <a name="members"></a>Members

### <a name="values"></a>Valores

|Nombre|Descripción|
|----------|-----------------|
|`MultipleResults`|Conjunto de varios resultados, que se presentan progresivamente entre `Start` estado y antes de que se llame a `Close()`.|
|`SingleResult`|Un único resultado, que se presenta después de que se produzca el evento `Complete`.|

## <a name="requirements"></a>Requisitos

**Encabezado:** Async. h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Consulte también

[Microsoft::WRL (espacio de nombres)](microsoft-wrl-namespace.md)
