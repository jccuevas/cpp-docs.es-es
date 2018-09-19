---
title: AsyncResultType (enumeración) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncResultType
dev_langs:
- C++
helpviewer_keywords:
- AsyncResultType enumeration
ms.assetid: 4195d234-3f3f-4363-9118-6ad2a7551cf2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2a79ef02302208aa14bc1620e486fcfbc6e12253
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42591268"
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